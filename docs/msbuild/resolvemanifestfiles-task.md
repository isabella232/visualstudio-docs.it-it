---
title: Attività ResolveManifestFiles | Microsoft Docs
description: Informazioni su MSBuild'attività ResolveManifestFiles per risolvere gli elementi del processo di compilazione in file per la generazione del manifesto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveManifestFiles task [MSBuild]
- MSBuild, ResolveManifestFiles task
ms.assetid: e1e14f67-9b69-433f-94d4-a783a68676b2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: f0306ef70bf7aa2c74875001bbd6f4e1a3bec2c14be65565cda0c56ac13892f8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121270367"
---
# <a name="resolvemanifestfiles-task"></a>ResolveManifestFiles (attività)

Risolve gli elementi seguenti del processo di compilazione nei file per la generazione del manifesto: elementi compilati, dipendenze, satelliti, contenuto, simboli di debug e documentazione.

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività `ResolveManifestFiles` .

|Parametro|Descrizione|
|---------------|-----------------|
|`DeploymentManifestEntryPoint`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il nome del manifesto della distribuzione.|
|`EntryPoint`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica l'assembly gestito o un riferimento al manifesto ClickOnce che rappresenta il punto di ingresso al manifesto.|
|`ExtraFiles`|Parametro facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Specifica i file aggiuntivi.|
|`ManagedAssemblies`|Parametro facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Specifica gli assembly gestiti.|
|`NativeAssemblies`|Parametro facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Specifica gli assembly nativi.|
|`OutputAssemblies`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica gli assembly generati.|
|`OutputDeploymentManifestEntryPoint`|Parametro di ouput facoltativo <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Specifica il punto di ingresso del manifesto della distribuzione dell'output.|
|`OutputEntryPoint`|Parametro di ouput facoltativo <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Specifica il punto di ingresso dell'output.|
|`OutputFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica i file di output.|
|`PublishFiles`|Parametro facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Specifica i file di pubblicazione.|
|`SatelliteAssemblies`|Parametro facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Specifica gli assembly satellite.|
|`SigningManifests`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, i manifesti sono firmati.|
|`TargetCulture`|Parametro `String` facoltativo.<br /><br /> Specifica le impostazioni cultura di destinazione per gli assembly satellite.|
|`TargetFrameworkVersion`|Parametro `String` facoltativo.<br /><br /> Specifica la versione di .NET Framework di destinazione.|

## <a name="remarks"></a>Commenti

 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e delle relative descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
