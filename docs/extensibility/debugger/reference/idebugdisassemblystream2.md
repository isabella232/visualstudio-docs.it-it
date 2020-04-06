---
title: Proprietà IDebugDisassemblyStream2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98ba08e4ec32aceaf6c265714848939cc6ad9c66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732041"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
Questa interfaccia rappresenta un flusso di istruzioni.

## <a name="syntax"></a>Sintassi

```
IDebugDisassemblyStream2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un motore di debug implementa questa interfaccia per supportare il disassembly del codice di un programma.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Una chiamata al [metodo GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) restituisce questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugDisassemblyStream2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[Leggere](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Legge le istruzioni a partire dalla posizione corrente nel flusso di smontaggio.|
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Sposta il puntatore di lettura nel flusso di disassembly di un determinato numero di istruzioni relative a una posizione specificata.|
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Restituisce un identificatore di posizione del codice per un contesto di codice specifico.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Restituisce un oggetto contesto di codice corrispondente a un identificatore di posizione del codice specificato.|
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Restituisce un identificatore di posizione del codice che rappresenta la posizione del codice corrente.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Ottiene il documento di origine associato a questo flusso di disassembly.|
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Ottiene l'ambito di questo flusso di disassembly.|
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Ottiene le dimensioni di questo flusso di disassembly.|

## <a name="remarks"></a>Osservazioni
 Il flusso di disassembly può essere creato per rappresentare l'intero spazio di indirizzi o solo una funzione o un modulo all'interno dello spazio. Ogni istruzione è rappresentata da un [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struttura restituita da una chiamata al [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) metodo.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
