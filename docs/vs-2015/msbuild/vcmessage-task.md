---
title: Attività VCMessage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 508d1fe33046f6051c9c5c1b8e54036e78ae7d2f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193345"
---
# <a name="vcmessage-task"></a>Attività VCMessage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Registra gli avvisi e i messaggi di errore durante una compilazione.  
  
## <a name="remarks"></a>Osservazioni  
 Questa attività consente di implementare MSBuild per Visual C++ e non deve essere chiamata dall'utente. Per altre informazioni, vedere <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività **VCMessage**.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|**Argomenti**|Parametro **stringa** facoltativo.<br /><br /> Elenco delimitato da punto e virgola dei messaggi da visualizzare.|  
|**Codice**|Parametro **String** obbligatorio.<br /><br /> Un numero di errore che qualifica il messaggio.|  
|**Tipo**|Parametro **stringa** facoltativo.<br /><br /> Specifica il tipo di messaggio da generare. Specifica `"Warning"` per generare un messaggio di avviso o `"Error"` per generare un messaggio di errore.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento attività](../msbuild/msbuild-task-reference.md)
