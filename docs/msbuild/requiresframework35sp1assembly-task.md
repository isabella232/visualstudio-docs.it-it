---
title: Attività RequiresFramework35SP1Assembly | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- RequiresFramework35SP1Assembly task [MSBuild]
- MSBuild, RequiresFramework35SP1Assembly task
ms.assetid: 755c018a-8a8b-4c94-8aee-3f171fc419e5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: caefe0887ca23cd4cee60c3a4ba2a6133e9893df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "77632771"
---
# <a name="requiresframework35sp1assembly-task"></a>RequiresFramework35SP1Assembly (attività)

Determina se l'applicazione richiede .NET Framework 3.5 SP1.

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività `RequiresFramework35SP1Assembly` .

|Parametro|Descrizione|
|---------------|-----------------|
|`Assemblies`|Parametro facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Specifica gli assembly a cui si fa riferimento nell'applicazione.|
|`CreateDesktopShortcut`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, crea un'icona di collegamento sul desktop durante l'installazione.|
|`DeploymentManifestEntryPoint`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il nome del file manifesto per l'applicazione.|
|`EntryPoint`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica l'assembly che deve essere eseguito quando viene eseguita l'applicazione.|
|`ErrorReportUrl`|Parametro `String` facoltativo.<br /><br /> Specifica il sito Web visualizzato nelle finestre di dialogo che si aprono durante le installazioni ClickOnce.|
|`Files`|Parametro facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Specifica l'elenco dei file che verranno distribuiti quando si pubblica l'applicazione.|
|`ReferencedAssemblies`|Parametro facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Specifica gli assembly a cui si fa riferimento nel progetto.|
|`RequiresMinimumFramework35SP1`|Parametro di ouput facoltativo `Boolean`.<br /><br /> Se `true`, l'applicazione richiede .NET Framework 3.5 SP1.|
|`SigningManifests`|Parametro di ouput facoltativo `Boolean`.<br /><br /> Se `true`, i manifesti ClickOnce sono firmati.|
|`SuiteName`|Parametro `String` facoltativo.<br /><br /> Specifica il nome della cartella del menu **Start** in cui verrà installata l'applicazione.|
|`TargetFrameworkVersion`|Parametro `String` facoltativo.<br /><br /> Specifica la versione di .NET Framework a cui è destinata l'applicazione.|

## <a name="remarks"></a>Osservazioni

 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le relative descrizioni, vedere [classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vedere anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)