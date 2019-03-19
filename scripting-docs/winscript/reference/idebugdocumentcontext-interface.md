---
title: Interfaccia IDebugDocumentContext | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentContext interface
ms.assetid: 665ee08a-5c6a-4ab1-ab93-de376acc9a74
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df4c8b8639a6d4b232f82cf87fff7b069829cc46
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159454"
---
# <a name="idebugdocumentcontext-interface"></a>Interfaccia IDebugDocumentContext
Offre una rappresentazione astratta di una parte del documento sottoposto a debug. Per i documenti di testo, questa rappresentazione è costituito da un intervallo di posizione del carattere.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IDebugDocumentContext` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugDocumentContext::GetDocument](../../winscript/reference/idebugdocumentcontext-getdocument.md)|Restituisce il documento che contiene questo contesto.|  
|[IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)|Enumera i contesti di codice associati a questo contesto di documento.|