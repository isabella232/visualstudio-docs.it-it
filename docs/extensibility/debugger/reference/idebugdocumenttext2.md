---
title: Proprietà IDebugDocumentText2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b5def7f6cc4ac5ced91ca0a273ce750003dca20
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731556"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Questa interfaccia rappresenta un documento di testo.

## <a name="syntax"></a>Sintassi

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un motore di debug (DE) implementa questa interfaccia quando il codice sorgente che deve fornire è in formato testo. Poiché questo è il caso più tipico, se un DE implementa `IDebugDocumentText2` il [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaccia, è necessario implementare anche l'interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Utilizzare `QueryInterface` il metodo per ottenere `IDebugDocument2` questa interfaccia da un'interfaccia .

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi `IDebugDocument2` sull'interfaccia, questa interfaccia implementa i metodi seguenti:In addition to the methods on the interface, this interface implements the following methods:

|Metodo|Descrizione|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Recupera le dimensioni del testo in questa posizione nel documento.|
|[Gettext](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Recupera il testo dalla posizione specificata nel documento.|

## <a name="remarks"></a>Osservazioni
 Un oggetto che implementa questa <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaccia deve implementare <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> anche l'interfaccia, che fornisce l'interfaccia per un [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) oggetto.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
