---
description: Questa interfaccia rappresenta un flusso di istruzioni.
title: IDebugDisassemblyStream2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: e42d8019c854ca800dd35028fe82a158bc3a428e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122119516"
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
 Nella tabella seguente vengono illustrati i metodi di `IDebugDisassemblyStream2` .

|Metodo|Descrizione|
|------------|-----------------|
|[Lettura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Legge le istruzioni a partire dalla posizione corrente nel flusso disassembly.|
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Sposta il puntatore di lettura nel flusso disassembly di un determinato numero di istruzioni rispetto a una posizione specificata.|
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Restituisce un identificatore della posizione del codice per un particolare contesto del codice.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Restituisce un oggetto contesto del codice corrispondente a un identificatore di posizione del codice specificato.|
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Restituisce un identificatore della posizione del codice che rappresenta la posizione del codice corrente.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Ottiene il documento di origine associato a questo flusso disassembly.|
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Ottiene l'ambito di questo flusso disassembly.|
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Ottiene le dimensioni di questo flusso disassembly.|

## <a name="remarks"></a>Commenti
 Il flusso disassembly può essere creato per rappresentare l'intero spazio indirizzi o solo una funzione o un modulo all'interno dello spazio. Ogni istruzione è rappresentata da una [struttura DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) restituita da una chiamata al [metodo Read.](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
