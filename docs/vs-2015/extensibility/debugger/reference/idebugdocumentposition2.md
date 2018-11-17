---
title: IDebugDocumentPosition2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocumentPosition2
helpviewer_keywords:
- IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6ada282748bbc3eece247ae8a271e9af1b6756f8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743840"
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia rappresenta una posizione astratta in un file di origine.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugDocumentPosition2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Visual Studio implementa in genere questa interfaccia. Un motore di debug (DE) implementerà questa interfaccia anche se deve fornire il proprio codice sorgente (come quando il DE implementa il [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interface).  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia viene passata come argomento di [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md). Vengono inoltre forniti come parte di un [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) union (in particolare, un [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) struttura) che a sua volta fa parte del [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) struttura, usato nella creazione di un punto di interruzione in sospeso.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugDocumentPosition2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Ottiene il nome del file del file di origine che contiene la posizione del documento.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|Ottiene il documento contenitore.|  
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Determina se questa posizione è contenuta nel documento specificato.|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Ottiene l'intervallo per questa posizione del documento.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)

