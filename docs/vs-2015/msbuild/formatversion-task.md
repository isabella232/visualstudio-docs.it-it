---
title: Attività FormatVersion | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7fbd03676d69dde5f9a6d169739a25e7b5e1b82e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54755125"
---
# <a name="formatversion-task"></a>Attività FormatVersion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Aggiunge il numero di revisione al numero di versione.  
  
-   Caso n. 1: Input: Version=\<indefinita>;  Revision=\<indifferente>;   Output: OutputVersion="1.0.0.0"  
  
-   Caso n. 2: Input: Version="1.0.0.*"  Revision="5"  Output: OutputVersion="1.0.0.5"  
  
-   Caso n. 3: Input: Version="1.0.0.0"  Revision=\<indifferente>;  Output: OutputVersion="1.0.0.0"  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `FormatVersion` .  
  
|Parametro|Description|  
|---------------|-----------------|  
|`FormatType`|Parametro `String` facoltativo.<br /><br /> Specifica il tipo di formato.<br /><br /> -   "Version" = versione.<br />-   "Path" = sostituire "." con "_";|  
|`OutputVersion`|Parametro di ouput facoltativo `String`.<br /><br /> Specifica la versione di output che include il numero di revisione.|  
|`Revision`|Parametro `Int32` facoltativo.<br /><br /> Specifica la revisione da accodare alla versione.|  
|`Version`|Parametro `String` facoltativo.<br /><br /> Specifica la stringa del numero di versione da formattare.|  
  
## <a name="remarks"></a>Note  
 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
