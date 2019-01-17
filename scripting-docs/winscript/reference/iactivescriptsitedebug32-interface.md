---
title: Interfaccia IActiveScriptSiteDebug32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03f42217-303d-46e7-9792-61a5ab95252c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: e7937311e01274570e34bd639a0dc5f68206a3aa
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345565"
---
# <a name="iactivescriptsitedebug32-interface"></a>IActiveScriptSiteDebug32 Interface
Implementare smart host il `IActiveScriptSiteDebug32` interfaccia per eseguire la gestione dei documenti e per partecipare il debug. Il `IActiveScriptSite` oggetto in genere fornisce un'implementazione del `IActiveScriptSiteDebug32` interfaccia. Se questa operazione, chiamare il `IActiveScriptSite::QueryInterface` metodo per ottenere il `IActiveScriptSiteDebug32` interfaccia.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IActiveScriptSiteDebug32` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|Restituisce l'oggetto di debug dell'applicazione associata a questo sito dello script.|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|Utilizzato dal motore del linguaggio per delegare `IDebugCodeContext::GetSourceContext`.|