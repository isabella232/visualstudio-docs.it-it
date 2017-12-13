---
title: "Attività UpdateManifest | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UpdateManifest task
- UpdateManifest task [MSBuild]
ms.assetid: 1291fd33-b89e-4e15-8fb1-69f9625cf2d2
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 85cb6c20f0e330b06f2e2a3999b115bc61111f9d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="updatemanifest-task"></a>Attività UpdateManifest
Aggiorna le proprietà selezionate in un manifesto e ripete la firma.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `UpdateManifest` .  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`ApplicationManifest`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio.<br /><br /> Specifica il manifesto dell'applicazione.|  
|`ApplicationPath`|Parametro `String` obbligatorio.<br /><br /> Specifica il percorso del manifesto dell'applicazione.|  
|`InputManifest`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio.<br /><br /> Specifica il manifesto da aggiornare.|  
|`OutputManifest`|Parametro di ouput facoltativo <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Specifica il manifesto che contiene le proprietà aggiornate.|  
  
## <a name="remarks"></a>Note  
 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [Classe di base Task](../msbuild/task-base-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)