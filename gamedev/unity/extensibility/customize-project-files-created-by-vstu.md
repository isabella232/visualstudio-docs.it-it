---
title: Personalizzare i file di progetto creati con VSTU | Microsoft Docs
description: Informazioni su come personalizzare i file di progetto creati Visual Studio Tools per Unity (VSTU). Esaminare un esempio di codice C#.
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
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123961583"
---
# <a name="customize-project-files-created-by-vstu"></a>Personalizzare i file di progetto creati con VSTU
Unity fornisce callback durante la generazione del file di progetto. Implementare i metodi e usando un oggetto per modificare il file di progetto o di soluzione ogni volta che `OnGeneratedSlnSolution` `OnGeneratedCSProject` viene [`AssetPostprocessor`](https://docs.unity3d.com/ScriptReference/AssetPostprocessor.html) rigenerato.

## <a name="demonstrates"></a>Dimostra
Viene illustrato come personalizzare i file di progetto di Visual Studio generati da Visual Studio Tools per Unity.

## <a name="example"></a>Esempio

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
