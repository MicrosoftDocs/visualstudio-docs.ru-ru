---
title: Предоставление автоматизации для кода | Документация Майкрософт
description: Сведения о реализации модели кода, которая требует реализации интерфейсов, определяемых внутренней структурой данных.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 57d5337ae088560bb94a6af39902e90b6af02686
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060969"
---
# <a name="providing-automation-for-code"></a>Предоставление автоматизации для кода
Создание модели автоматизации для кода не является обязательным. Пакет SDK для среды не предоставляет пример для этого. Подробные сведения о моделях кода см. в разделе <xref:EnvDTE.CodeModel> объект.

 Для реализации модели кода необходимо реализовать все интерфейсы, определяемые внутренней структурой данных. Объекты должны быть производными от `IDispatch` класса.

 Объекты, которые вы расширяете, <xref:EnvDTE.CodeModel> и <xref:EnvDTE.FileCodeModel> , доступны из <xref:EnvDTE.Project> объекта и выглядят следующим образом:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 Можно выбрать реализацию только `CodeModel` `FileCodeModel` интерфейса или в объекте, возвращаемом из `Project` <xref:EnvDTE.ProjectItem> объектов и. Предоставьте все функциональные возможности этого интерфейса, которые подходят для вашей системы проектов.

 Если вы хотите добавить такие компоненты, как методы или свойства, которые недоступны из стандартных `CodeModel` `FileCodeModel` интерфейсов и, создайте собственный интерфейс, наследующий от стандартного. Не забудьте задокументировать его в системе проекта, чтобы конечные пользователи могли найти его. Вы возвращаете стандартный интерфейс, но пользователь может вызвать `QueryInterface` метод или выполнить приведение к интерфейсу, если известно, что он существует.

## <a name="see-also"></a>См. также
- [Общие сведения о модели автоматизации](../../extensibility/internals/automation-model-overview.md)
