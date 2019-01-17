---
title: Interfaccia IActiveScriptSiteDebug | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 339325686d2a98e34c6e9f96056612769a9e110e
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348308"
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