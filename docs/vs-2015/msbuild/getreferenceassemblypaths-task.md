---
title: Attività GetReferenceAssemblyPaths | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4563e1c28c17a173c211f979d2ca46503a6d19a7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54805130"
---
# <a name="getreferenceassemblypaths-task"></a>Attività GetReferenceAssemblyPaths
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Restituisce i percorsi degli assembly di riferimento dei vari framework.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `GetReferenceAssemblyPaths` .  
  
|Parametro|Description|  
|---------------|-----------------|  
|`ReferenceAssemblyPaths`|Parametro di ouput facoltativo `String[]`.<br /><br /> Restituisce il percorso, in base al parametro `TargetFrameworkMoniker`. Se `TargetFrameworkMoniker` è null o vuoto, il percorso sarà `String.Empty`.|  
|`FullFrameworkReferenceAssemblyPaths`|Parametro di ouput facoltativo `String[]`.<br /><br /> Restituisce il percorso, in base al parametro `TargetFrameworkMoniker`, senza considerare la parte del profilo del moniker. Se `TargetFrameworkMoniker` è null o vuoto, il percorso sarà `String.Empty`.|  
|`TargetFrameworkMoniker`|Parametro `String` facoltativo.<br /><br /> Specifica il moniker del framework di destinazione associato ai percorsi degli assembly di riferimento.|  
|`RootPath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso radice da usare per generare il percorso dell'assembly di riferimento.|  
|`BypassFrameworkInstallChecks`|Parametro [Boolean](<!-- TODO: review code entity reference <xref:assetId:///Boolean?qualifyHint=False&amp;autoUpgrade=True>  -->) facoltativo.<br /><br /> Se `true`, consente di ignorare i controlli di base eseguiti da `GetReferenceAssemblyPaths` per impostazione predefinita per garantire che determinati framework di runtime vengano installati, a seconda del framework di destinazione.|  
|`TargetFrameworkMonikerDisplayName`|Parametro di ouput facoltativo `String`.<br /><br /> Specifica il nome visualizzato per il moniker del framework di destinazione.|  
  
## <a name="remarks"></a>Note  
 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
