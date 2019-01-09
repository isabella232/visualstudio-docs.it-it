---
title: Attività GetReferenceAssemblyPaths | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 485b8f9c19a8a91d686b603ee1be9da70b6c78e1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53987875"
---
# <a name="getreferenceassemblypaths-task"></a>Attività GetReferenceAssemblyPaths
Restituisce i percorsi degli assembly di riferimento dei vari framework.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `GetReferenceAssemblyPaths` .  
  
|Parametro|Description|  
|---------------|-----------------|  
|`ReferenceAssemblyPaths`|Parametro di ouput facoltativo `String[]`.<br /><br /> Restituisce il percorso, in base al parametro `TargetFrameworkMoniker`. Se `TargetFrameworkMoniker` è null o vuoto, il percorso sarà `String.Empty`.|  
|`FullFrameworkReferenceAssemblyPaths`|Parametro di ouput facoltativo `String[]`.<br /><br /> Restituisce il percorso, in base al parametro `TargetFrameworkMoniker`, senza considerare la parte del profilo del moniker. Se `TargetFrameworkMoniker` è null o vuoto, il percorso sarà `String.Empty`.|  
|`TargetFrameworkMoniker`|Parametro `String` facoltativo.<br /><br /> Specifica il moniker del framework di destinazione associato ai percorsi degli assembly di riferimento.|  
|`RootPath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso radice da usare per generare il percorso dell'assembly di riferimento.|  
|`BypassFrameworkInstallChecks`|Parametro <xref:System.Boolean> facoltativo.<br /><br /> Se `true`, consente di ignorare i controlli di base eseguiti da `GetReferenceAssemblyPaths` per impostazione predefinita per garantire che determinati framework di runtime vengano installati, a seconda del framework di destinazione.|  
|`TargetFrameworkMonikerDisplayName`|Parametro di ouput facoltativo `String`.<br /><br /> Specifica il nome visualizzato per il moniker del framework di destinazione.|  
  
## <a name="remarks"></a>Note  
 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)