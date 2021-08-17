---
description: Questa interfaccia enumera le strutture FRAMEINFO.
title: IEnumDebugFrameInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: f658b5fdaa5d65185f845790f5342e5c8b7a2422
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122103351"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
Questa interfaccia enumera le [strutture FRAMEINFO.](../../../extensibility/debugger/reference/frameinfo.md)

## <a name="syntax"></a>Sintassi

```
IEnumDebugFrameInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug implementa questa interfaccia per fornire un elenco di strutture che descrivono lo stack di chiamate corrente.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Visual Studio chiama [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) per ottenere questa interfaccia ogni volta che si verifica un punto di interruzione, un'eccezione o un'interruzione in un programma in fase di debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IEnumDebugFrameInfo2` .

|Metodo|Descrizione|
|------------|-----------------|
|[Avanti](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Recupera un numero specificato di [strutture FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) in una sequenza di enumerazione.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Ignora un numero specificato di [strutture FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) in una sequenza di enumerazione.|
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Riporta all'inizio la sequenza di enumerazione.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Ottiene il numero di [strutture FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) in un enumeratore.|

## <a name="remarks"></a>Commenti
 Visual Studio ottiene questa interfaccia come primo passaggio per la gestione di un punto di interruzione, un'eccezione o una sospensione generata dall'utente nel programma in fase di debug. L'elenco [di strutture FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) rappresenta lo stack di chiamate corrente, con la chiamata di funzione corrente all'inizio dell'elenco e la chiamata di funzione meno recente alla fine dell'elenco. Ogni rappresenta un stack frame, un contesto in cui le `FRAMEINFO` espressioni possono essere valutate e le variabili locali osservate.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
