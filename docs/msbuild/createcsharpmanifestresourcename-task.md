---
title: Attività CreateCSharpManifestResourceName | Microsoft Docs
description: Usare l'attività MSBuild CreateCSharpManifestResourceName per creare un nome di manifesto di tipo C# da un nome di file con estensione resx specificato o da un'altra risorsa.
ms.custom: SEO-VS-2020
ms.date: 11/15/2020
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CreateCSharpManifestResourceName task
- CreateCSharpManifestResourceName task [MSBuild]
ms.assetid: 2ace88c1-d757-40a7-8158-c1d3f5ff0511
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3e1bd096c2a9c7763a3be0611f3716f61df22856
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055869"
---
# <a name="createcsharpmanifestresourcename-task"></a>attività CreateCSharpManifestResourceName

Crea un nome di manifesto di tipo C# da un nome di file con *estensione resx* specificato o da un'altra risorsa.

## <a name="parameters"></a>Parametri

 Nella tabella seguente vengono descritti i parametri dell' [Attività CreateCSharpManifestResourceName](../msbuild/createcsharpmanifestresourcename-task.md).

| Parametro | Descrizione |
| - | - |
| `ManifestResourceNames` | <xref:Microsoft.Build.Framework.ITaskItem>`[]`parametro di sola lettura di output.<br /><br /> Nomi di manifesto risultanti. |
| `ResourceFiles` | Parametro `String` obbligatorio.<br /><br /> Nome del file di risorse da cui creare il nome di manifesto C#. |
| `RootNamespace` | Parametro `String` facoltativo.<br /><br /> Spazio dei nomi radice del file di risorse, in genere derivato dal file di progetto. Può essere `null`. |
| `PrependCultureAsDirectory` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, il nome delle impostazioni cultura viene aggiunto come nome di directory prima del nome di risorsa di manifesto. Il valore predefinito è `true`. |
| `ResourceFilesWithManifestResourceNames` | Parametro di output di sola lettura `String` facoltativo.<br /><br /> Restituisce il nome del file di risorse che include ora il nome di risorsa di manifesto. |

## <a name="remarks"></a>Commenti

 L' [Attività CreateCSharpManifestResourceName](../msbuild/createcsharpmanifestresourcename-task.md) determina il nome della risorsa di manifesto appropriato da assegnare a un file con *estensione resx* o a un altro file di risorse specificato. L'attività fornisce un nome logico a un file di risorse e quindi lo associa a un parametro di output come metadato.

 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e le relative descrizioni, vedere [classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
