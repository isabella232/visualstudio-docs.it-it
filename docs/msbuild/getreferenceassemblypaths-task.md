---
title: Attività GetReferenceAssemblyPaths | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
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
ms.openlocfilehash: 1041a298b7b195180e312e54aeadd666b478cb29
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2018
ms.locfileid: "37946820"
---
# <a name="getreferenceassemblypaths-task"></a>Attività GetReferenceAssemblyPaths
Restituisce i percorsi degli assembly di riferimento dei vari framework.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `GetReferenceAssemblyPaths` .  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`ReferenceAssemblyPaths`|Parametro di ouput facoltativo `String[]`.<br /><br /> Restituisce il percorso, in base al parametro `TargetFrameworkMoniker`. Se `TargetFrameworkMoniker` è null o vuoto, il percorso sarà `String.Empty`.|  
|`FullFrameworkReferenceAssemblyPaths`|Parametro di ouput facoltativo `String[]`.<br /><br /> Restituisce il percorso, in base al parametro `TargetFrameworkMoniker`, senza considerare la parte del profilo del moniker. Se `TargetFrameworkMoniker` è null o vuoto, il percorso sarà `String.Empty`.|  
|`TargetFrameworkMoniker`|Parametro `String` facoltativo.<br /><br /> Specifica il moniker del framework di destinazione associato ai percorsi degli assembly di riferimento.|  
|`RootPath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso radice da usare per generare il percorso dell'assembly di riferimento.|  
|`BypassFrameworkInstallChecks`|Parametro <xref:System.Boolean> facoltativo.<br /><br /> Se `true`, consente di ignorare i controlli di base eseguiti da `GetReferenceAssemblyPaths` per impostazione predefinita per garantire che determinati framework di runtime vengano installati, a seconda del framework di destinazione.|  
|`TargetFrameworkMonikerDisplayName`|Parametro di ouput facoltativo `String`.<br /><br /> Specifica il nome visualizzato per il moniker del framework di destinazione.|  
  
## <a name="remarks"></a>Note  
 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)