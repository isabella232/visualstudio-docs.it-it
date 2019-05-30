---
title: IEnumDebugModules2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd6d7dc2cba76443d409feef4f2fe9dd0cd04e33
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339647"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Questa interfaccia enumera un elenco dei moduli.

## <a name="syntax"></a>Sintassi

```
IEnumDebugModules2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un elenco di moduli caricati per un programma.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Le chiamate di Visual Studio [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente sono illustrati i metodi di `IEnumDebugModules2`.

|Metodo|Descrizione|
|------------|-----------------|
|[avanti](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Recupera un determinato numero di moduli in una sequenza di enumerazione.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Ignora un numero specificato di moduli in una sequenza di enumerazione.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Ottiene il numero dei moduli.|

## <a name="remarks"></a>Note
 Visual Studio Usa questa interfaccia principalmente per aggiornare il **moduli** finestra.

 Ai fini di debug in Visual Studio, un programma è una sequenza logica di istruzioni di codice che possono oltrepassare i limiti di modulo, quindi la necessità di un elenco di moduli per una singola [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaccia. Il primo modulo nell'elenco contiene in genere il punto di ingresso iniziale per il programma associato.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)