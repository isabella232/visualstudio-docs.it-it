---
title: Interfaccia IActiveScriptSiteDebug32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 03f42217-303d-46e7-9792-61a5ab95252c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 2a55161f76fcd98b52ddb769c640aca0e903239b
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835264"
---
# <a name="iactivescriptsitedebug32-interface"></a>Interfaccia IActiveScriptSiteDebug32
Gli SmartHost implementano l' `IActiveScriptSiteDebug32` interfaccia per eseguire la gestione dei documenti e partecipare al debug. L' `IActiveScriptSite` oggetto in genere fornisce un'implementazione dell' `IActiveScriptSiteDebug32` interfaccia. Se questa operazione viene eseguita, chiamare il `IActiveScriptSite::QueryInterface` metodo per ottenere l' `IActiveScriptSiteDebug32` interfaccia.  
  
 Oltre ai metodi ereditati da `IUnknown` , l' `IActiveScriptSiteDebug32` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|Restituisce l'oggetto applicazione di debug associato a questo sito di script.|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|Utilizzato dal motore di linguaggio per delegare `IDebugCodeContext::GetSourceContext` .|