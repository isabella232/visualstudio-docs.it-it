---
title: Proprietà IDebugDocumentContext2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d31a78412a1a6b20518b6f38ba76b7964cbdbe3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731740"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
Questa interfaccia rappresenta una posizione in un documento di file di origine.

## <a name="syntax"></a>Sintassi

```
IDebugDocumentContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia come parte del relativo supporto per il debug a livello di codice sorgente. Oltre a una posizione nel codice sorgente, questa interfaccia fornisce metodi per confrontare i contesti e spostarsi all'interno di un documento di codice sorgente.

## <a name="notes-for-callers"></a>Note per i chiamanti
 I metodi su diverse interfacce, in genere le interfacce [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) e [GetDocumentContext,](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) restituiscono questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugDocumentContext2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|Ottiene il documento che contiene questo contesto del documento.|
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|Ottiene il nome visualizzabile del documento che contiene questo contesto del documento.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|Recupera un elenco di tutti i contesti di codice associati a questo contesto del documento.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|Ottiene la lingua associata al contesto del documento.|
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Ottiene l'intervallo di istruzioni del file di questo contesto del documento.|
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|Ottiene l'intervallo di origine del file di questo contesto del documento.|
|[Confronta](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|Confronta questo contesto del documento con una matrice specificata di contesti del documento.|
|[Seek](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|Sposta il contesto del documento di un determinato numero di istruzioni o righe.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)
