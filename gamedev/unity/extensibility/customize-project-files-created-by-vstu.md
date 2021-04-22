---
title: Настройка файлов проекта, созданных в VSTU | Документация Майкрософт
description: Сведения о том, как настраивать файлы проекта, создаваемые набором средств Visual Studio для Unity (VSTU). Знакомство с примером кода C#.
ms.custom: ''
ms.date: 04/19/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: a4a5973863877db2d071f9be8d4689928b21a689
ms.sourcegitcommit: 3e1ff87fba290f9e60fb4049d011bb8661255d58
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2021
ms.locfileid: "107879321"
---
# <a name="customize-project-files-created-by-vstu"></a>Настройка файлов проекта, созданных в VSTU
Unity предоставляет обратные вызовы во время создания файла проекта. Реализуйте `OnGeneratedSlnSolution` методы и, `OnGeneratedCSProject` используя [`AssetPostprocessor`](https://docs.unity3d.com/ScriptReference/AssetPostprocessor.html) для изменения файла проекта или решения при каждом его повторном формировании.

## <a name="demonstrates"></a>Что демонстрирует
Как настраивать файлы проекта Visual Studio, создаваемые набором средств Visual Studio для Unity.

## <a name="example"></a>Пример

```csharp
using System;
using UnityEditor;
using UnityEngine;

public class ProjectFilePostprocessor : AssetPostprocessor
{
  public static string OnGeneratedSlnSolution(string path, string content)
  {
    // TODO: process solution content
    return content;
  }

  public static string OnGeneratedCSProject(string path, string content)
  {
    // TODO: process project content
    return content;
  }
}
```
