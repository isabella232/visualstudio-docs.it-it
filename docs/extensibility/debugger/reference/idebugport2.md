---
description: Questa interfaccia rappresenta una porta di debug in un computer.
title: Interfaccia IDebugPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ca97bd3a89358f374e66a1c35693ca4f2801641c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133016"
---
# <a name="idebugport2"></a>IDebugPort2
Questa interfaccia rappresenta una porta di debug in un computer.

## <a name="syntax"></a>Sintassi

```
IDebugPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un fornitore di porte personalizzato implementa questa interfaccia per rappresentare una porta di debug in un computer.

 Se la porta supporta l'invio di eventi di porta, deve implementare anche l'interfaccia per supportare un'interfaccia che a sua volta fornisce <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> l'interfaccia [IDebugPortEvents2.](../../../extensibility/debugger/reference/idebugportevents2.md)

## <a name="notes-for-callers"></a>Note per i chiamanti
 Le chiamate [a GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) [o AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) restituiscono questa interfaccia, che rappresenta la porta richiesta.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugPort2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Restituisce il nome della porta.|
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Restituisce l'identificatore di porta.|
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Restituisce la richiesta utilizzata per creare una porta (se disponibile).|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Restituisce il fornitore della porta per questa porta.|
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Restituisce un'interfaccia al processo in base all'identificatore del processo.|
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Enumera tutti i processi in esecuzione su una porta.|

## <a name="remarks"></a>Commenti
 La porta locale fornisce l'accesso a tutti i processi e i programmi in esecuzione nel computer locale. Altre porte possono rappresentare una connessione via cavo seriale a un dispositivo Windows CE o una connessione di rete a un computer non DCOM. `IDebugPort2`L'interfaccia viene usata per trovare il nome e l'identificatore di una porta ed enumerare tutti i processi in esecuzione sulla porta. Le funzionalità per l'avvio e la terminazione dei processi sulla porta vengono implementate `IDebugPortEx2` nell'interfaccia .

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
