---
title: Attività VCMessage | Microsoft Docs
ms.custom: ''
ms.date: 06/27/2018
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.vcmessage
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- VCMessage task (MSBuild (Visual C++))
- MSBuild (Visual C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 66c245f78c27521e9db53327f8dfdc567ed0e995
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154139"
---
# <a name="vcmessage-task"></a>attività VCMessage
Registra gli avvisi e i messaggi di errore durante una compilazione.  
  
## <a name="remarks"></a>Note  
 Questa attività consente di implementare MSBuild per Visual C++ e non deve essere chiamata dall'utente. Per ulteriori informazioni, vedere <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività **VCMessage**.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|**Argomenti**|Parametro **String** facoltativo.<br /><br /> Elenco delimitato da punto e virgola dei messaggi da visualizzare.|  
|**Codice**|Parametro **String** obbligatorio.<br /><br /> Un numero di errore che qualifica il messaggio.|  
|**Type**|Parametro **String** facoltativo.<br /><br /> Specifica il tipo di messaggio da generare. Specifica "Warning" per generare un messaggio di avviso o "Error" per generare un messaggio di errore.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)