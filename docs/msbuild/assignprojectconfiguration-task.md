---
title: Attività AssignProjectConfiguration | Microsoft Docs
description: Usare l MSBuild'attività AssignProjectConfiguration per accettare un elenco di stringhe di configurazione e assegnarle ai progetti specificati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 09633a0b-8f6f-4aba-8058-7cb4d13ce2c0
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 9444217b139a6a367cb9c74cc60b1dd7848df80a8179bc10b72a1eca8354a151
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121288438"
---
# <a name="assignprojectconfiguration-task"></a>Attività AssignProjectConfiguration

Questa attività accetta stringhe di configurazione elenco e le assegna ai progetti specificati.

## <a name="task-parameters"></a>Parametri dell'attività

 Nella tabella che segue vengono descritti i parametri dell'attività `AssignProjectConfiguration` .

|Parametro|Descrizione|
|---------------|-----------------|
|`ProjectReferences`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> `[]` di input obbligatorio.<br /><br /> Progetti da configurare.|
|`SolutionConfigurationContents`|Parametro di ouput facoltativo `string`.<br /><br /> Include una stringa XML contenente una configurazione di progetto per ogni progetto. Le configurazioni vengono assegnate ai progetti con nome.|
|`DefaultToVcxPlatformMapping`|Parametro di ouput facoltativo `string`.<br /><br /> Contiene un elenco delimitato da punto e virgola dei mapping dai nomi di piattaforma usati dalla maggior parte dei tipi a quelli usati dai file *VCXPROJ*.<br /><br /> Esempio:<br /><br /> `"AnyCPU=Win32;X86=Win32;X64=X64"`|
|`VcxToDefaultPlatformMapping`|Facoltativo<br /><br /> Parametro di output `string`.<br /><br /> Contiene un elenco delimitato da punti e virgola di mapping dai nomi della piattaforma *vcxproj* ai nomi di piattaforma utilizzati dalla maggior parte dei tipi.<br /><br /> Esempio:<br /><br /> `"Win32=AnyCPU;X64=X64"`|
|`CurrentProjectConfiguration`|Parametro di ouput facoltativo `string`.<br /><br /> Contiene la configurazione per il progetto corrente.|
|`CurrentProjectPlatform`|Parametro di ouput facoltativo `string`.<br /><br /> Contiene la piattaforma per il progetto corrente.|
|`OnlyReferenceAndBuildProjectsEnabledInSolutionConfiguration`|Parametro di ouput facoltativo `bool`.<br /><br /> Contiene un flag che indica che i riferimenti devono essere compilati anche se sono stati disabilitati nella configurazione del progetto.|
|`ShouldUnsetParentConfigurationAndPlatform`|Parametro di ouput facoltativo `bool`.<br /><br /> Contiene un flag che indica se la configurazione padre e la piattaforma devono essere annullate.|
|`OutputType`|Parametro di ouput facoltativo `string`.<br /><br /> Contiene il tipo di output per il progetto.|
|`ResolveConfigurationPlatformUsingMappings`|Parametro di ouput facoltativo `bool`.<br /><br /> Contiene un flag che indica se la compilazione deve usare i mapping predefiniti per risolvere la configurazione e la piattaforma dei riferimenti del progetto passati.|
|`AssignedProjects`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene l'elenco dei percorsi dei riferimenti risolti.|
|`UnassignedProjects`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene l'elenco degli elementi di riferimento del progetto che non sono stati risolti usando l'elenco di output prerisolto.|

## <a name="remarks"></a>Commenti

 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e delle relative descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
