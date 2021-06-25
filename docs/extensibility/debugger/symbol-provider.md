---
title: Поставщик символов | Документация Майкрософт
description: Узнайте о поставщиках символов, предоставляемых Visual Studio, чтобы позволить Вычислителю выражений оценивать переменные и выражения.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3332bbf705d8e3149d864dbb35418fd4c12c523b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902921"
---
# <a name="symbol-provider"></a>Поставщик символов
Реализация средства оценки выражений должна получить доступ к символьной отладочной информации, созданной компилятором языка, для оценки переменных и выражений. Это достигается за счет использования интерфейсов поставщика символов (SP), также называемого обработчиком символов.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предоставляет SPs для управляемого кода и машинного кода, используя формат файла символов базы данных программы (PDB). Если программа не должна использовать символы, хранящиеся в пользовательском формате, рекомендуется использовать SPs, предоставляемые [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="implementation-notes"></a>Примечания по реализации
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Модули отладки должны взаимодействовать с SPs с помощью интерфейсов CLR. В результате пакет обновления, который будет работать с механизмами отладки Visual Studio, должен поддерживать среду CLR. Полный список всех интерфейсов отладки среды CLR можно найти в debugref.doc, который является частью компонента [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] .

 Если ваш пакет обновления будет работать только с пользовательским модулем отладки, вы можете реализовать его так, как вы видите, в зависимости от потребностей модуля отладки.

## <a name="see-also"></a>См. также
- [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)
