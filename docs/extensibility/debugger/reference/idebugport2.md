---
title: Proprietà IDebugPort2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62912be9fdfecc98a264a58c9713cc12ccaf28f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725226"
---
# <a name="idebugport2"></a>IDebugPort2
Questa interfaccia rappresenta una porta di debug in un computer.

## <a name="syntax"></a>Sintassi

```
IDebugPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un fornitore di porta personalizzato implementa questa interfaccia per rappresentare una porta di debug in un computer.

 Se la porta supporta l'invio di <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> eventi di <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> porta, è necessario implementare anche l'interfaccia per supportare un'interfaccia che a sua volta fornisce il [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Le chiamate a [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) o [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) restituiscono questa interfaccia, che rappresenta la porta richiesta.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugPort2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Restituisce il nome della porta.|
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Restituisce l'identificatore di porta.|
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Restituisce la richiesta utilizzata per creare una porta (se disponibile).|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Restituisce il fornitore della porta per questa porta.|
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Restituisce un'interfaccia al processo dato l'identificatore del processo.|
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Enumera tutti i processi in esecuzione su una porta.|

## <a name="remarks"></a>Osservazioni
 La porta locale fornisce l'accesso a tutti i processi e i programmi in esecuzione nel computer locale. Altre porte potrebbero rappresentare una connessione via cavo seriale a un dispositivo basato su Windows CE o una connessione di rete a un computer non DCOM. L'interfaccia `IDebugPort2` viene utilizzata per trovare il nome e l'identificatore di una porta ed enumerare tutti i processi in esecuzione sulla porta. Le strutture per l'avvio e la terminazione dei processi sulla porta vengono implementate nell'interfaccia. `IDebugPortEx2`

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
