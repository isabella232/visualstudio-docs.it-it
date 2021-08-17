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
ms.openlocfilehash: a579d985cea401f855934b1966e387c7a5a1832a12f2f347b734f6a7e035f7f4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121449183"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Consente a un nodo di programma di ricevere una notifica di un tentativo di connessione al programma associato.

## <a name="syntax"></a>Sintassi

```
IDebugProgramNodeAttach2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata nella stessa classe che implementa [l'interfaccia IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) per ricevere la notifica di un'operazione di collegamento e offrire la possibilità di annullare l'operazione di collegamento.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Ottenere questa interfaccia chiamando il `QueryInterface` metodo in un oggetto [IDebugProgramNode2.](../../../extensibility/debugger/reference/idebugprogramnode2.md) Il [metodo OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) deve essere chiamato prima del metodo [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) per offrire al nodo del programma la possibilità di arrestare il processo di connessione.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Si collega al programma associato o rinvia il processo di connessione al [metodo](../../../extensibility/debugger/reference/idebugengine2-attach.md) Attach.|

## <a name="remarks"></a>Commenti
 Questa interfaccia è l'alternativa [](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) preferita al metodo Attach_V7 deprecato. Tutti i motori di debug vengono sempre caricati con la funzione, cio' ne viene creata un'istanza all'esterno dello spazio di indirizzi del programma di cui è in `CoCreateInstance` corso il debug.

 Se un'implementazione precedente del metodo impostava semplicemente l'oggetto del programma in fase di debug, deve essere implementato solo `IDebugProgramNode2::Attach_V7` `GUID` il metodo [OnAttach.](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)

 Se un'implementazione precedente del metodo ha usato l'interfaccia di callback fornita, tale funzionalità deve essere spostata in un'implementazione del metodo Attach e l'interfaccia non deve `IDebugProgramNode2::Attach_V7` essere [](../../../extensibility/debugger/reference/idebugengine2-attach.md) `IDebugProgramNodeAttach2` implementata.

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
