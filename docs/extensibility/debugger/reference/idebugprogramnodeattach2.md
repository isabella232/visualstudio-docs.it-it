---
description: Consente a un nodo del programma di ricevere una notifica di un tentativo di connessione al programma associato.
title: IDebugProgramNodeAttach2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1a1de6c7480e1ce4dcc0723614741a05dcc961a6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071467"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Consente a un nodo del programma di ricevere una notifica di un tentativo di connessione al programma associato.

## <a name="syntax"></a>Sintassi

```
IDebugProgramNodeAttach2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata nella stessa classe che implementa l'interfaccia [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) per ricevere una notifica di un'operazione di connessione e per offrire l'opportunità di annullare l'operazione di associazione.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Ottenere questa interfaccia chiamando il `QueryInterface` metodo in un oggetto [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) . Il metodo [Onconnettit](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) deve essere chiamato prima del metodo di [connessione](../../../extensibility/debugger/reference/idebugengine2-attach.md) per fornire al nodo del programma la possibilità di arrestare il processo di connessione.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Si connette al programma associato o rinvia il processo di associazione al metodo di [connessione](../../../extensibility/debugger/reference/idebugengine2-attach.md) .|

## <a name="remarks"></a>Commenti
 Questa interfaccia è l'alternativa preferita al metodo [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) deprecato. Tutti i motori di debug vengono sempre caricati con la `CoCreateInstance` funzione, ovvero ne viene creata un'istanza fuori dallo spazio degli indirizzi del programma di cui è in corso il debug.

 Se un'implementazione precedente del `IDebugProgramNode2::Attach_V7` Metodo stava semplicemente impostando il `GUID` del programma di cui è in corso il debug, è necessario implementare solo il metodo [onconnettit](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) .

 Se un'implementazione precedente del `IDebugProgramNode2::Attach_V7` Metodo usava l'interfaccia di callback fornita, la funzionalità deve essere spostata in un'implementazione del metodo di [connessione](../../../extensibility/debugger/reference/idebugengine2-attach.md) e `IDebugProgramNodeAttach2` non è necessario implementare l'interfaccia.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
