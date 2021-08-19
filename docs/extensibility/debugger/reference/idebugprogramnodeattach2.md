---
description: Consente a un nodo di programma di ricevere una notifica di un tentativo di connessione al programma associato.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: e28ca64629d0bdb000a39d5cd4ab040b732730fb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122096102"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Consente a un nodo di programma di ricevere una notifica di un tentativo di connessione al programma associato.

## <a name="syntax"></a>Sintassi

```
IDebugProgramNodeAttach2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata nella stessa classe che implementa l'interfaccia [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) per ricevere la notifica di un'operazione di collegamento e per offrire la possibilità di annullare l'operazione di collegamento.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Ottenere questa interfaccia chiamando il `QueryInterface` metodo in un oggetto [IDebugProgramNode2.](../../../extensibility/debugger/reference/idebugprogramnode2.md) Il [metodo OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) deve essere chiamato prima del metodo [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) per offrire al nodo del programma la possibilità di arrestare il processo di connessione.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Si connette al programma associato o rinvia il processo di connessione al [metodo](../../../extensibility/debugger/reference/idebugengine2-attach.md) Attach.|

## <a name="remarks"></a>Commenti
 Questa interfaccia è l'alternativa preferita al metodo [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) deprecato. Tutti i motori di debug vengono sempre caricati con la funzione , in altri modo ne viene creata un'istanza all'esterno dello spazio degli indirizzi del programma di cui è in `CoCreateInstance` corso il debug.

 Se un'implementazione precedente del metodo impostava semplicemente l'oggetto del programma di cui è in corso il debug, deve essere implementato `IDebugProgramNode2::Attach_V7` `GUID` solo il metodo [OnAttach.](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)

 Se un'implementazione precedente del metodo usava l'interfaccia di callback fornita, tale funzionalità deve essere spostata in un'implementazione del metodo Attach e non è necessario che l'interfaccia `IDebugProgramNode2::Attach_V7` sia [](../../../extensibility/debugger/reference/idebugengine2-attach.md) `IDebugProgramNodeAttach2` implementata.

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
