---
title: Interfaccia IActiveScriptSiteDebug | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebug interface
ms.assetid: 2557ee09-688b-4c03-a821-180c24dfa0e6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3cd8043648586ed3c614cbb137e51d992d7ae29b
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58145778"
---
# <a name="iactivescriptsitedebug-interface"></a>Interfaccia IActiveScriptSiteDebug Interface
Implementare smart host il `IActiveScriptSiteDebug` interfaccia per eseguire la gestione dei documenti e per partecipare il debug. Il `IActiveScriptSite` oggetto in genere fornisce un'implementazione del `IActiveScriptSiteDebug` interfaccia. Se questa operazione, chiamare il `IActiveScriptSite::QueryInterface` metodo per ottenere il `IActiveScriptSiteDebug` interfaccia.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IActiveScriptSiteDebug` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)|Utilizzato dal motore del linguaggio per delegare `IDebugCodeContext::GetSourceContext`.|  
|[IActiveScriptSiteDebug::GetApplication](../../winscript/reference/iactivescriptsitedebug-getapplication.md)|Restituisce l'oggetto di debug dell'applicazione associata a questo sito dello script.|  
|[IActiveScriptSiteDebug::GetRootApplicationNode](../../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)|Ottiene il nodo dell'applicazione nella quale script devono essere aggiunti i documenti.|  
|[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)|Consente a uno smart host determinare come gestire errori di run-time.|