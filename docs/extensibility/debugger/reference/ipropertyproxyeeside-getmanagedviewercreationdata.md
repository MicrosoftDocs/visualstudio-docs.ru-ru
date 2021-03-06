---
description: Получает сведения о средстве просмотра для этого типа свойства, чтобы создать экземпляр этого средства просмотра.
title: 'Ипропертипроксеесиде:: Жетманажедвиеверкреатиондата | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f2d7d4ef3f35cb0ad00f91033213449af8cb7306
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224139"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
Получает сведения о средстве просмотра для этого типа свойства, чтобы создать экземпляр этого средства просмотра.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetManagedViewerCreationData(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  className,
   ASSEMBLYLOCRESOLUTION* alr,
   BOOL*                  replacementOk
);
```

```csharp
int GetManagedViewerCreationData(
   out string                     assemName,
   out IEEDataStorage             assemBytes,
   out IEEDataStorage             assemPdb,
   out string                     className,
   out enum_ASSEMBLYLOCRESOLUTION alr,
   out int                        replacementOk
);
```

## <a name="parameters"></a>Параметры
`assemName`\
заполняет Возвращает имя сборки, содержащей этот объект.

`assemBytes`\
заполняет Возвращает объект [иидатастораже](../../../extensibility/debugger/reference/ieedatastorage.md) , содержащий байты сборки данного объекта (это значение null, если нет доступных байтов).

`assemPdb`\
заполняет Возвращает `IEEDataStorage` объект, содержащий сведения о хранилище символов для этого объекта (значение null, если хранилище символов недоступно).

`className`\
заполняет Возвращает имя класса, содержащего этот объект.

`alr`\
заполняет Возвращает значение из перечисления [ассемблилокресолутион](../../../extensibility/debugger/reference/assemblylocresolution.md) , указывающее расположение сборки.

`replacementOk`\
заполняет Возвращает ненулевой ( `TRUE` ), если значение этого объекта может быть изменено; ноль ( `FALSE` ), если объект доступен только для чтения.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Комментарии
 Этот метод используется визуализаторами типов для создания экземпляра управляемого средства просмотра.

## <a name="see-also"></a>См. также раздел
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
