---
title: Диагностические данные и журналы, созданные системой
description: Сведения о создаваемых системой Visual Studio журналах, типах собираемых данных и о том, как использовать их для решения проблем и повышения качества продукта.
ms.custom: SEO-VS-2020
ms.date: 05/24/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d357b5e21ca86d7ccf11f576a15bbd0e7a90e466
ms.sourcegitcommit: a339547aa2f4e0f64b7afbcc3e1ade0a4f9287d2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/01/2021
ms.locfileid: "106171840"
---
# <a name="system-generated-logs-collected-by-visual-studio"></a>Созданные системой журналы, собираемые Visual Studio

Visual Studio собирает журналы, созданные системой, для устранения проблем и повышения качества продукта в рамках [программы улучшения Visual Studio](visual-studio-experience-improvement-program.md). В этой статье приведены некоторые сведения о типах собираемых данных и их использовании. Кроме того, она содержит советы, помогающие создателям расширений избежать случайного раскрытия личных или конфиденциальных сведений.

## <a name="types-of-collected-data"></a>Типы собираемых данных

Visual Studio собирает создаваемые системой журналы, относящиеся к сбоям, зависаниям пользовательского интерфейса и высокой загрузке ЦП или памяти. Корпорация Майкрософт также собирает сведения об ошибках, возникших во время установки или использования продукта. Собираемые данные зависят от ошибки и могут содержать трассировки стека, дампы памяти и сведения об исключениях:

- В отношении высокой загрузки ЦП и зависания собираются данные трассировки стека соответствующих потоков Visual Studio.

- Если трассировки стека некоторых потоков недостаточно для выявления первопричины проблемы, например сбоев, отсутствия отклика или большой загрузки памяти, мы собираем *дамп* памяти. Дамп представляет состояние процесса на момент возникновения ошибки.

- В случае возникновения непредвиденной ошибки, например исключения при попытке записи в файл на диске, мы собираем сведения об исключении. Сведения включают имя исключения, трассировку стека потока, в котором возникло исключение, сообщение, связанное с исключением, и другие сведения, относящиеся к конкретному исключению.

   В следующем примере собранных данных показано имя исключения, трассировка стека и сообщение об исключении:

   ```text
   "Reserved.DataModel.Fault.Exception.TypeString": "System.IO.IOException",
   "Reserved.DataModel.Fault.Exception.StackTrace": "System.IO.__Error.WinIOError(Int32,String)\r\n
   System.IO.FileStream.Init(String,FileMode,FileAccess,Int32,Boolean,FileShare,Int32,FileOptions,SECURITY_ATTRIBUTES,String,Boolean,Boolean,Boolean)\r\n
   System.IO.FileStream..ctor(String,FileMode,FileAccess,FileShare,Int32,FileOptions,String,Boolean,Boolean,Boolean)\r\nSystem.IO.StreamWriter.CreateFile(String,Boolean,Boolean)\r\n
   System.IO.StreamWriter..ctor(String,Boolean,Encoding,Int32,Boolean)\r\n
   System.IO.StreamWriter..ctor(String,Boolean)\r\n
   System.IO.File.CreateText(String)\r\n
   Microsoft.VisualStudio.Setup.Services.FileSystem.CreateText(String,Boolean)\r\n
   Microsoft.VisualStudio.Setup.Cache.ChannelManifestRepository.WriteChannelManifest(IChannelManifest,String,String)\r\n
   Microsoft.VisualStudio.Setup.Cache.ChannelManifestRepository.AddChannel(ChannelManifestPair,Boolean)\r\n
   Microsoft.VisualStudio.Setup.Cache.CacheManager.AddChannel(ChannelManifestPair,Boolean)\r\n
   Microsoft.VisualStudio.Setup.ChannelManager.\<UpdateAsync>d__37.MoveNext()\r\n”,
   "Reserved.DataModel.Fault.Exception.Message": " The process cannot access the file 'C:\\Users\\[UserName]\\AppData\\Local\\Microsoft\\VisualStudio\\Packages\\_Channels\\4CB340F5\\channelManifest.json' because it is being used by another process."
   ```

## <a name="how-we-use-system-generated-logs"></a>Как используются журналы, созданные системой

Процедура определения основной причины ошибки зависит от типа ошибки и ее серьезности.

### <a name="error-classification"></a>Классификация ошибок

На основании журналов выполняется классификация и подсчет ошибок для определения их приоритета. Например, может быть обнаружено, что ошибка System.IO.\__Error.WinIOError в System.IO.FileStream.Init возникла 500 раз в версии \<x> продукта и имеет наибольшее количество случаев в этой версии.

### <a name="work-items-for-tracking"></a>Рабочие элементы для отслеживания

Рабочие элементы для отдельных упорядоченных ошибок создаются и назначаются инженерам для дальнейшего изучения. Эти рабочие элементы обычно содержат сведения о классификации, приоритете и диагностические сведения, относящиеся к типу ошибки. Эти сведения мы получаем из собранных журналов, созданных системой, для конкретной ошибки. Например, рабочий элемент для сбоя может содержать трассировку стека, в котором возник сбой.

### <a name="error-investigation"></a>Исследование ошибки

Инженеры используют сведения, доступные в рабочем элементе, для определения основной причины ошибки. В некоторых случаях им может потребоваться больше сведений, чем имеется в рабочем элементе, тогда они могут обратиться к исходному журналу, созданному системой. Например, инженер может проверить дамп памяти, чтобы понять причину сбоя продукта.

## <a name="tips-for-extension-authors"></a>Советы для авторов расширений

Авторам расширений следует ограничивать раскрытие личных данных, отказавшись от использования личных и других конфиденциальных сведений в именах модулей, типов и методов. В случае возникновения сбоя или аналогичной ошибки с этим кодом в стеке такие сведения собираются как часть журналов, созданных системой.

## <a name="opt-out-of-data-collection"></a>Отказ от сбора данных

Учитывая цели сбора данных и ограничения, налагаемые на доступ к данным и их хранение, мы рекомендуем использовать параметры конфиденциальности по умолчанию для Windows и Visual Studio. Тем не менее вы можете [отказаться от участия](../ide/visual-studio-experience-improvement-program.md#opt-in-or-out) в программе улучшения Visual Studio в любой момент. Явный отказ предполагает отказ от **необязательного** сбора диагностических данных. Чтобы обеспечить безопасность, актуальность и производительность Visual Studio, **требуется** сбор некоторых диагностических данных. На этот процесс сбора ваш явный отказ от VSCEIP не повлияет. Сведения о том, как отключить сбор данных журналов, созданных системой, для всех программ, см. в статье [Диагностика, отзывы и конфиденциальность в Windows 10](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy). Конкретные параметры зависят от используемой версии Windows.

## <a name="see-also"></a>См. также

- [Программа улучшения качества программного обеспечения Visual Studio](visual-studio-experience-improvement-program.md)
- [Диагностика, отзывы и конфиденциальность в Windows 10](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy)
