---
description: Questa interfaccia rappresenta la posizione iniziale di un'istruzione di codice.
title: Interfaccia IDebugCodeContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: da3fdc1c8f3c9c836519ba45d39df0aeca326d05
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122104131"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Questa interfaccia rappresenta la posizione iniziale di un'istruzione di codice. Per la maggior parte delle architetture di run-time attualmente, un contesto di codice può essere pensato come un indirizzo nel flusso di esecuzione di un programma.

## <a name="syntax"></a>Sintassi

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug implementa questa interfaccia per correlare la posizione di un'istruzione di codice a una posizione del documento.

## <a name="notes-for-callers"></a>Note per i chiamanti
 I metodi su molte interfacce restituiscono questa interfaccia, in genere [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). Viene inoltre ampiamente usato con [l'interfaccia IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) e nelle informazioni sulla risoluzione dei punti di interruzione.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi [nell'interfaccia IDebugMemoryContext2,](../../../extensibility/debugger/reference/idebugmemorycontext2.md) questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Ottiene il contesto del documento che corrisponde al contesto del codice attivo.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Ottiene le informazioni sulla lingua per questo contesto di codice.|

## <a name="remarks"></a>Commenti
 La differenza principale tra `IDebugCodeContext2` un'interfaccia e [un'interfaccia IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) è che un `IDebugCodeContext2` oggetto è sempre allineato alle istruzioni. Ciò significa che un oggetto punta sempre all'inizio di un'istruzione , mentre un oggetto può puntare a qualsiasi byte di `IDebugCodeContext2` `IDebugMemoryContext2` memoria nell'architettura di run-time. `IDebugCodeContext2` viene incrementato dalle istruzioni anziché dalle dimensioni di archiviazione di base (in genere byte).

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [Avanti](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
