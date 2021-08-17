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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 994d7d6a23638bfdeb78ba8807e5c6e6d19c39e7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122095374"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Questa interfaccia enumera un elenco di moduli.

## <a name="syntax"></a>Sintassi

```
IEnumDebugModules2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug implementa questa interfaccia per rappresentare un elenco di moduli caricati per un programma.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Visual Studio chiama [EnumModules per](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IEnumDebugModules2` .

|Metodo|Descrizione|
|------------|-----------------|
|[Avanti](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Recupera un numero specificato di moduli in una sequenza di enumerazione.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Ignora un numero specificato di moduli in una sequenza di enumerazione.|
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Riporta all'inizio la sequenza di enumerazione.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Ottiene il numero di moduli.|

## <a name="remarks"></a>Commenti
 Visual Studio questa interfaccia viene utilizzata principalmente per aggiornare la **finestra** Moduli.

 Ai fini del debug in Visual Studio, un programma è una sequenza logica di istruzioni di codice che possono attraversare i limiti del modulo, quindi la necessità di un elenco di moduli per una singola [interfaccia IDebugProgram2.](../../../extensibility/debugger/reference/idebugprogram2.md) Il primo modulo nell'elenco contiene in genere il punto di ingresso iniziale per il programma associato.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)
