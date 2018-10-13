---
title: Attività XslTransformation | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dad55677c5b75ec2c2721bd489a031cbf29597da
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49292318"
---
# <a name="xsltransformation-task"></a>Attività XslTransformation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Consente di trasformare un input XML tramite un XSLT o un XSLT compilato e di creare un file o dispositivo di output.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `XslTransformation` .  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`OutputPaths`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica i file di output per la trasformazione XML.|  
|`Parameters`|Parametro `String` facoltativo.<br /><br /> Specifica i parametri per il documento di input XSLT.|  
|`XmlContent`|Parametro `String` facoltativo.<br /><br /> Specifica l'input XML sotto forma di stringa.|  
|`XmlInputPaths`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica i file di input XML.|  
|`XslCompiledDllPath`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il file XSLT compilato.|  
|`XslContent`|Parametro `String` facoltativo.<br /><br /> Specifica l'input XSLT sotto forma di stringa.|  
|`XslInputPath`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il file di input XSLT.|  
  
## <a name="remarks"></a>Note  
 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)



