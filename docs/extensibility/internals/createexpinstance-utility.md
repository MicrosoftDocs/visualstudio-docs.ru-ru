---
title: Служебная программа CreateExpInstance | Документация Майкрософт
description: Сведения о служебной программе CreateExpInstance, которая позволяет создавать, сбрасывать и удалять экспериментальные экземпляры Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cce9bc25cb2ed820d3291ab65d94a868bb401ec9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898140"
---
# <a name="createexpinstance-utility"></a>Служебная программа CreateExpInstance
Используйте служебную программу **CreateExpInstance** для создания, сброса или удаления экспериментального экземпляра Visual Studio. Экспериментальный экземпляр можно использовать для отладки и тестирования расширений Visual Studio без изменения базового продукта.

## <a name="syntax"></a>Синтаксис

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>Параметры
 **/CREATE** Создает экспериментальный экземпляр.

 **/Reset** Удаляет экспериментальный экземпляр, а затем создает новый.

 **/Clean** Удаляет экспериментальный экземпляр.

 **/Всинстанце** Имя каталога, содержащего базовый экземпляр Visual Studio для копирования.

 **/Рутсуффикс** Суффикс, добавляемый к имени каталога экспериментального экземпляра.

## <a name="remarks"></a>Remarks
 При работе с расширением Visual Studio можно нажать клавишу F5, чтобы открыть экспериментальный экземпляр по умолчанию и установить текущее расширение. Если экспериментальный экземпляр недоступен, Visual Studio создает его с параметрами по умолчанию.

 Расположение экспериментального экземпляра по умолчанию зависит от номера версии Visual Studio. Например, для Visual Studio 2015 расположение — *%LocalAppData%\Microsoft\VisualStudio\14.0Exp \\*. Все файлы в расположении каталога считаются частью этого экземпляра. Все дополнительные экспериментальные экземпляры не будут загружаться Visual Studio, если только имя каталога не будет изменено на расположение по умолчанию.

 Visual Studio не получает доступ к системному реестру при открытии экспериментального экземпляра. Это отличается от предыдущих версий Visual Studio, в которых использовалась экспериментальная версия куста реестра.

 Служебная программа **CreateExpInstance** заменяет служебную программу **всрежекс** .

 В следующем примере выполняется сброс экспериментального экземпляра Visual Studio по умолчанию:

 **CreateExpInstance.exe/Reset/Всинстанце = ~/Рутсуффикс = exp**

## <a name="see-also"></a>См. также
- [VSPackages](../../extensibility/internals/vspackages.md)
