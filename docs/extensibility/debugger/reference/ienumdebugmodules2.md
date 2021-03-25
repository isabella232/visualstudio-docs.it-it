---
description: Questa interfaccia enumera un elenco di moduli.
title: IEnumDebugModules2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 96a35f11346b769a4329b1212a8202e5e5ded006
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058170"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Questa interfaccia enumera un elenco di moduli.

## <a name="syntax"></a>Sintassi

```
IEnumDebugModules2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un elenco di moduli caricati per un programma.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Visual Studio chiama [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IEnumDebugModules2` .

|Metodo|Descrizione|
|------------|-----------------|
|[Avanti](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Recupera un numero specificato di moduli in una sequenza di enumerazione.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Ignora un numero specificato di moduli in una sequenza di enumerazione.|
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Riporta all'inizio la sequenza di enumerazione.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Ottiene il numero di moduli.|

## <a name="remarks"></a>Commenti
 Visual Studio usa questa interfaccia principalmente per aggiornare la finestra **moduli** .

 Ai fini del debug in Visual Studio, un programma è una sequenza logica di istruzioni di codice che possono superare i limiti dei moduli, quindi la necessità di un elenco di moduli per una singola interfaccia [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) . Il primo modulo dell'elenco contiene in genere il punto di ingresso iniziale per il programma associato.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)
