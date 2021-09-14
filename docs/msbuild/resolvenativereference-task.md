---
title: Attività ResolveNativeReference | Microsoft Docs
description: Informazioni su MSBuild'attività ResolveNativeReference per risolvere i riferimenti nativi implementando la classe Microsoft.Build.Tasks.ResolveNativeReference.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveNativeReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNativeReference task
- ResolveNativeReference task [MSBuild]
ms.assetid: 56acd101-de77-4eec-92c6-f5c6d2187579
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 212239348ba1f4caf80be1ac9feb029bb702cee3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625565"
---
# <a name="resolvenativereference-task"></a>ResolveNativeReference (attività)

Risolve i riferimenti nativi. Implementa la classe <xref:Microsoft.Build.Tasks.ResolveNativeReference>. Questa classe supporta l'infrastruttura .NET Framework, che non può essere usata direttamente dal codice.

## <a name="task-parameters"></a>Parametri dell'attività

 Nella tabella che segue vengono descritti i parametri dell'attività `ResolveNativeReference` .

|Parametro|Descrizione|
|---------------|-----------------|
|`AdditionalSearchPaths`|Parametro <xref:System.String?displayProperty=fullName>`[]` obbligatorio.<br /><br /> Ottiene o imposta i percorsi di ricerca per la risoluzione di identità di assembly di riferimenti nativi.|
|`ContainedComComponents`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Ottiene o imposta i componenti COM dell'assembly nativo.|
|`ContainedLooseEtcFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Ottiene o imposta i file *Etc* liberi elencati nel manifesto nativo.|
|`ContainedLooseTlbFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Ottiene o imposta i file *con estensione tlb* dell'assembly nativo.|
|`ContainedPrerequisiteAssemblies`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Ottiene o imposta gli assembly che devono essere presenti prima che il manifesto possa essere usato.|
|`ContainedTypeLibraries`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Ottiene o imposta le librerie dei tipi dell'assembly nativo.|
|`ContainingReferenceFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Ottiene o imposta i file di riferimento.|
|`NativeReferences`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Ottiene o imposta i riferimenti all'assembly nativo Win32.|

## <a name="remarks"></a>Commenti

 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e delle relative descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
