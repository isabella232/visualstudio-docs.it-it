---
description: Questa interfaccia rappresenta un documento di testo.
title: IDebugDocumentText2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eb1c5928362616466985a6f88102ffcbf4377444
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154210"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Questa interfaccia rappresenta un documento di testo.

## <a name="syntax"></a>Sintassi

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un motore di debug (DE) implementa questa interfaccia quando il codice sorgente che deve fornire è in formato testo. Poiché questo è il caso più comune, se un DE implementa l'interfaccia [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) , deve implementare anche l' `IDebugDocumentText2` interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Usare il `QueryInterface` metodo per ottenere questa interfaccia da un' `IDebugDocument2` interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi sull' `IDebugDocument2` interfaccia, questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Recupera la dimensione del testo in questa posizione nel documento.|
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Recupera il testo dalla posizione specificata nel documento.|

## <a name="remarks"></a>Commenti
 Un oggetto che implementa questa interfaccia deve implementare anche l' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaccia, che fornisce l' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaccia per un oggetto [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) .

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
