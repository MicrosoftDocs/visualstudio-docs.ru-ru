---
title: Руководство. Управление несколькими потоками в управляемом коде | Документация Майкрософт
description: Узнайте, как управлять несколькими потоками в коде, если управляемое расширение VSPackage вызывает асинхронные методы или имеет операции в потоке пользовательского интерфейса Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7b301770a54baf0416aa9fcc838a9a6633252fbe
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073135"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>Руководство. Управление несколькими потоками в управляемом коде
Если у вас есть управляемое расширение VSPackage, вызывающее асинхронные методы или имеющее операции, которые выполняются в потоках, отличных от потока пользовательского интерфейса Visual Studio, следуйте инструкциям, приведенным ниже. Можно защитить поток пользовательского интерфейса, поскольку ему не нужно ждать завершения работы в другом потоке. Вы можете сделать код более эффективным, так как у вас нет дополнительных потоков, которые занимают пространство стека, и вы можете сделать его более надежным и простым в отладке, так как избежать взаимоблокировок и неотвечающего кода.

 В общем случае можно переключиться из потока пользовательского интерфейса в другой поток или наоборот. Когда метод возвращает значение, текущий поток является потоком, из которого он был первоначально вызван.

> [!IMPORTANT]
> Следующие рекомендации используют интерфейсы API в <xref:Microsoft.VisualStudio.Threading> пространстве имен, в частности <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> класс. Интерфейсы API в этом пространстве имен являются новыми в [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] . Экземпляр класса можно получить <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> из <xref:Microsoft.VisualStudio.Shell.ThreadHelper> свойства `ThreadHelper.JoinableTaskFactory` .

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>Переключение из потока пользовательского интерфейса в фоновый поток

1. Если вы работаете в потоке пользовательского интерфейса и хотите выполнять асинхронную работу в фоновом потоке, используйте `Task.Run()` :

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. Если вы работаете в потоке пользовательского интерфейса и хотите синхронно блокироваться при выполнении работы в фоновом потоке, используйте <xref:System.Threading.Tasks.TaskScheduler> свойство `TaskScheduler.Default` внутри <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> :

    ```csharp
    // using Microsoft.VisualStudio.Threading;
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        await TaskScheduler.Default;
        // You're now on a separate thread.
        DoSomethingSynchronous();
        await OrSomethingAsynchronous();
    });
    ```

## <a name="switch-from-a-background-thread-to-the-ui-thread"></a>Переключение из фонового потока в поток пользовательского интерфейса

1. Если вы находитесь в фоновом потоке и хотите сделать что-то в потоке пользовательского интерфейса, используйте <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> :

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     Для <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> переключения на поток пользовательского интерфейса можно использовать метод. Этот метод отправляет сообщение в поток пользовательского интерфейса с продолжением текущего асинхронного метода, а также взаимодействует с остальной частью платформы потоков, чтобы установить правильный приоритет и избежать взаимоблокировок.

     Если фоновый метод потока не является асинхронным и его нельзя сделать асинхронным, вы по-прежнему можете использовать `await` синтаксис для переключения в поток пользовательского интерфейса путем создания оболочки работы с <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> , как показано в следующем примере:

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```
