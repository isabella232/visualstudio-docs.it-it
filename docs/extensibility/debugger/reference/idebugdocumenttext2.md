---
title: IDebugDocumentText2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6069b7c77995a855bfa47d1d369203f386b0302c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686873"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
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

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)