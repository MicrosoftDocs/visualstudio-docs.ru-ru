---
title: IManagedAddin - интерфейс
description: Реализуйте интерфейс IManagedAddin для создания компонента, который загружает управляемые надстройки VSTO.
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IManagedAddin interface
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 614cf7e8d0e682d894328fb764c6d64b855d2834
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469792"
---
# <a name="imanagedaddin-interface"></a>IManagedAddin - интерфейс
  Реализуйте интерфейс IManagedAddin для создания компонента, который загружает управляемые надстройки VSTO. Этот интерфейс был добавлен в систему Microsoft Office 2007.

## <a name="syntax"></a>Синтаксис

```csharp
[
    object,
    uuid(B9CEAB65-331C-4713-8410-DDDAF8EC191A),
    pointer_default(unique),
    oleautomation
]
interface IManagedAddin : IUnknown
{
    HRESULT Load(
        [in] BSTR bstrManifestURL,
        [in] IDispatch *pdispApplication);
    HRESULT Unload();
};
```

## <a name="methods"></a>Методы
 В следующей таблице перечислены методы, определяемые интерфейсом IManagedAddin.

|Имя|Описание|
|----------|-----------------|
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Вызывается, когда приложение Microsoft Office загружает управляемую надстройку VSTO.|
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Вызывается непосредственно перед тем, как приложение Microsoft Office выгружает управляемую надстройку VSTO.|

## <a name="remarks"></a>Комментарии
 Microsoft Office приложений, начиная с системы Microsoft Office 2007, используйте интерфейс IManagedAddin, чтобы помочь в загрузке надстроек Office VSTO. Вы можете реализовать интерфейс IManagedAddin, чтобы создать собственный загрузчик надстройки VSTO и среду выполнения для управляемых надстроек VSTO вместо использования загрузчика надстроек VSTO (*VSTOLoader.dll*) и [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Для получения дополнительной информации см. [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

## <a name="how-managed-add-ins-are-loaded"></a>Загрузка управляемых надстроек
 При запуске приложения происходит следующее.

1. Приложение обнаруживает надстройки VSTO путем поиска записей в следующем разделе реестра:

    **HKEY_CURRENT_USER\Software\Microsoft\Office\\ *\<application name>* \аддинс\\**

    Каждая запись в этом разделе реестра представляет собой уникальный идентификатор надстройки VSTO. Как правило, это имя сборки надстройки VSTO.

2. Приложение ищет запись `Manifest` под записью для каждой надстройки VSTO.

    Управляемые надстройки VSTO могут хранить полный путь манифеста в `Manifest` записи в разделе **HKEY_CURRENT_USER\Software\Microsoft\Office\\ _\<application name>_ \аддинс \\ _\<add-in ID>_**. Манифест представляет собой файл (как правило, XML-файл), предоставляющий сведения, используемые для загрузки надстройки VSTO.

3. Если приложение находит запись `Manifest` , приложение пытается загрузить компонент загрузчика управляемой надстройки VSTO. Приложение делает это, пытаясь создать COM-объект, реализующий интерфейс IManagedAddin.

    [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Содержит компонент загрузчика надстройки VSTO (*VSTOLoader.dll*) или можно создать собственный, реализовав интерфейс IManagedAddin.

4. Приложение вызывает метод [IManagedAddin::Load](../vsto/imanagedaddin-load.md) и передает в него значение записи `Manifest` .

5. Метод [IManagedAddin::Load](../vsto/imanagedaddin-load.md) выполняет задачи, необходимые для загрузки надстройки VSTO, такие как настройка политики безопасности и домена приложения для загружаемой надстройки VSTO.

   Дополнительные сведения о разделах реестра, которые Microsoft Office приложения используют для обнаружения и загрузки управляемых надстроек VSTO, см. в разделе [записи реестра для надстроек VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

## <a name="guidance-to-implement-imanagedaddin"></a>Руководство по внедрению IManagedAddin
 При реализации IManagedAddin необходимо зарегистрировать библиотеку DLL, содержащую реализацию, с помощью следующего идентификатора CLSID:

 99D651D7-5F7C-470E-8A3B-774D5D9536AC

 Microsoft Office приложения используют этот идентификатор CLSID для создания COM-объекта, реализующего IManagedAddin.

> [!CAUTION]
> Этот идентификатор CLSID также используется *VSTOLoader.dll* в [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Поэтому, если вы используете IManagedAddin для создания собственного загрузчика надстройки VSTO и компонента среды выполнения, вы не сможете развернуть компонент на компьютерах, где выполняются надстройки VSTO, зависящие от [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

## <a name="see-also"></a>См. также раздел
- [Справочник по неуправляемым API &#40;разработке решений Office в Visual Studio&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)
