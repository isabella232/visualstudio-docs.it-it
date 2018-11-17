---
title: IDebugDocumentText2 | Microsoft Docs
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
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 85b5d9e78af9e4e49b3a985ca00ffad102e6b53d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728842"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia rappresenta un documento di testo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugDocumentText2 : IDebugDocument2  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un motore di debug (DE) implementa questa interfaccia quando il codice sorgente che è necessario fornire è in formato testo. Poiché questo è il caso più tipico, se un CRI implementa il [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaccia, deve anche implementare il `IDebugDocumentText2` interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Usare la `QueryInterface` per ottenere questa interfaccia dal metodo un `IDebugDocument2` interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi nel `IDebugDocument2` interfaccia, questa interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Recupera la dimensione del testo nella posizione specificata nel documento.|  
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Recupera il testo dalla posizione specificata nel documento.|  
  
## <a name="remarks"></a>Note  
 Un oggetto che implementa questa interfaccia deve implementare anche il <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> dell'interfaccia, che fornisce il <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaccia di amministrazione di un' [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) oggetto.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)

