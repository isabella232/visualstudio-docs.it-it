---
title: IDebugDocumentContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe54a6d3e97fc40f915c42c4aa5397165416b073
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326650"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
Questa interfaccia rappresenta una posizione in un documento di file di origine.

## <a name="syntax"></a>Sintassi

```
IDebugDocumentContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia come parte del supporto per livello debug del codice sorgente. Oltre a una posizione nel codice sorgente, questa interfaccia fornisce metodi per il confronto contesti e spostamento all'interno di un documento di codice sorgente.

## <a name="notes-for-callers"></a>Note per i chiamanti
 I metodi in diverse interfacce, generalmente il [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) e [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) interfacce, tornare a questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente sono illustrati i metodi di `IDebugDocumentContext2`.

|Metodo|Descrizione|
|------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|Ottiene il documento che contiene il contesto di questo documento.|
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|Ottiene il nome visualizzabile del documento che contiene il contesto di questo documento.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|Recupera un elenco di tutti i contesti di codice associato a questo contesto di documento.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|Ottiene la lingua associata a questo contesto di documento.|
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Ottiene l'intervallo di istruzioni di file di questo contesto di documento.|
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|Ottiene l'intervallo di origine di file di questo contesto di documento.|
|[Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|Confronta questo contesto di documento in una matrice specificata di contesti di documento.|
|[Seek](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|Sposta il contesto del documento da un determinato numero di istruzioni o le righe.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)