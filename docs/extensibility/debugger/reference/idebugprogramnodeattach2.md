---
title: Proprietà IDebugProgramNodeAttach2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d527dfcfcd09e4d70adca86436aa56e1852bee70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721829"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Consente a un nodo di programma di ricevere una notifica di un tentativo di connessione al programma associato.

## <a name="syntax"></a>Sintassi

```
IDebugProgramNodeAttach2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata nella stessa classe che implementa il [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interfaccia per ricevere la notifica di un'operazione di collegamento e per fornire la possibilità di annullare l'operazione di collegamento.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Ottenere questa interfaccia `QueryInterface` chiamando il metodo in un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) oggetto. Il [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metodo deve essere chiamato prima di [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) metodo per dare al nodo del programma la possibilità di arrestare il processo di collegamento.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Questa interfaccia implementa il metodo seguente:This interface implements the following method:

|Metodo|Descrizione|
|------------|-----------------|
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Si connette al programma associato o rinvia il processo di collegamento al metodo [Attach.](../../../extensibility/debugger/reference/idebugengine2-attach.md)|

## <a name="remarks"></a>Osservazioni
 Questa interfaccia è l'alternativa preferita al metodo [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) deprecato. Tutti i motori di debug `CoCreateInstance` vengono sempre caricati con la funzione, ovvero viene creata un'istanza all'esterno dello spazio di indirizzi del programma in fase di debug.

 Se un'implementazione `IDebugProgramNode2::Attach_V7` precedente del `GUID` metodo stava semplicemente impostando il programma in fase di debug, è necessario implementare solo il metodo [OnAttach.](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)

 Se un'implementazione `IDebugProgramNode2::Attach_V7` precedente del metodo utilizzava l'interfaccia di callback fornita, tale funzionalità `IDebugProgramNodeAttach2` deve essere spostata in un'implementazione del metodo [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) e l'interfaccia non deve essere implementata.

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
