---
title: Attività AssignProjectConfiguration | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 09633a0b-8f6f-4aba-8058-7cb4d13ce2c0
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e2091fad7e527990e8ed89ea8622cf41c1ae1ac4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187028"
---
# <a name="assignprojectconfiguration-task"></a>Attività AssignProjectConfiguration
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa attività accetta stringhe di configurazione elenco e le assegna ai progetti specificati.  
  
## <a name="task-parameters"></a>Parametri dell'attività  
 Nella tabella che segue vengono descritti i parametri dell'attività `AssignProjectConfiguration`.  
  
|Parametro|DESCRIZIONE|  
|---------------|-----------------|  
|`SolutionConfigurationContents`|Parametro di ouput facoltativo `string`.<br /><br /> Include una stringa XML contenente una configurazione di progetto per ogni progetto. Le configurazioni vengono assegnate ai progetti con nome.|  
|`DefaultToVcxPlatformMapping`|Parametro di ouput facoltativo `string`.<br /><br /> Contiene un elenco delimitato da punto e virgola dei mapping dai nomi di piattaforma usati<br /><br /> dalla maggior parte dei tipi a quelli usati da file con estensione vcxproj.<br /><br /> Ad esempio:<br /><br /> `"AnyCPU=Win32;X86=Win32;X64=X64"`|  
|`VcxToDefaultPlatformMapping`|Facoltativo<br /><br /> Parametro di output `string`.<br /><br /> Contiene un elenco delimitato da punto e virgola dei mapping dai nomi di piattaforma con estensione vcxproj ai nomi di piattaforma usati dalla maggior parte dei tipi.<br /><br /> Ad esempio:<br /><br /> `"Win32=AnyCPU;X64=X64"`|  
|`CurrentProjectConfiguration`|Parametro di ouput facoltativo `string`.<br /><br /> Contiene la configurazione per il progetto corrente.|  
|`CurrentProjectPlatform`|Parametro di ouput facoltativo `string`.<br /><br /> Contiene la piattaforma per il progetto corrente.|  
|`OnlyReferenceAndBuildProjectsEnabledInSolutionConfiguration`|Parametro di ouput facoltativo `bool`.<br /><br /> Contiene un flag che indica che i riferimenti devono essere compilati anche se sono stati disabilitati nella configurazione del progetto.|  
|`ShouldUnsetParentConfigurationAndPlatform`|Parametro di ouput facoltativo `bool`.<br /><br /> Contiene un flag che indica se la configurazione padre e la piattaforma devono essere annullate.|  
|`OutputType`|Parametro di ouput facoltativo `string`.<br /><br /> Contiene il tipo di output per il progetto.|  
|`ResolveConfigurationPlatformUsingMappings`|Parametro di ouput facoltativo `bool`.<br /><br /> Contiene un flag che indica se la compilazione deve usare i mapping predefiniti per risolvere la configurazione e la piattaforma dei riferimenti del progetto passati.|  
|`AssignedProjects`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene l'elenco dei percorsi dei riferimenti risolti.|  
|`UnassignedProjects`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene l'elenco degli elementi di riferimento del progetto che non sono stati risolti usando l'elenco di output prerisolto.|  
  
## <a name="remarks"></a>Osservazioni  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
