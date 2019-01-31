---
title: Attività WriteCodeFragment | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, WriteCodeFragment task
- WriteCodeFragment task [MSBuild]
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ee0b819d0387ecbd0bec3a460bf3c63d3122b269
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54796941"
---
# <a name="writecodefragment-task"></a>Attività WriteCodeFragment
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Genera un file di codice temporaneo usando il frammento di codice generato specificato. Non elimina il file.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `WriteCodeFragment` .  
  
|Parametro|Description|  
|---------------|-----------------|  
|`AssemblyAttributes`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Descrizione degli attributi da scrivere. Il valore dell'elemento `Include` è il nome completo del tipo dell'attributo, ad esempio, "System.AssemblyVersionAttribute".<br /><br /> Ogni tipo di metadati è la coppia nome-valore di un parametro, che deve essere di tipo `String`. Alcuni attributi consentono solo gli argomenti posizionali del costruttore. Tuttavia, è possibile usare tali argomenti in qualsiasi attributo. Per impostare gli attributi posizionali del costruttore, usare nomi di metadati simili a "_Parameter1","_Parameter2" e così via.<br /><br /> L'indice del parametro non può essere ignorato.|  
|`Language`|Parametro `String` obbligatorio.<br /><br /> Specifica il linguaggio del codice da generare.<br /><br /> `Language` può essere qualsiasi linguaggio per cui è disponibile un CodeDOM, ad esempio "C#" o "VisualBasic". Il file generato avrà l'estensione predefinita per tale linguaggio.|  
|`OutputDirectory`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica la cartella di destinazione per il codice generato, di solito la cartella intermedia.|  
|`OutputFile`|Parametro di ouput facoltativo <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Specifica il percorso del file generato. Se questo parametro viene impostato usando un nome di file, la cartella di destinazione viene anteposta al nome del file. Se viene impostato usando una radice, la cartella di destinazione viene ignorata.<br /><br /> Se questo parametro non viene impostato, il nome del file di output è la cartella di destinazione, un nome di file arbitrario e l'estensione del file predefinita per il linguaggio specificato.|  
  
## <a name="remarks"></a>Note  
 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
