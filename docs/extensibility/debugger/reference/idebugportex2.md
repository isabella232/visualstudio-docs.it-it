---
description: Questa interfaccia consente alla gestione del debug di sessione (SDM) di controllare i programmi e i processi in esecuzione su una porta.
title: Interfaccia IDebugPortEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 41c5eff48a164107c9c87582bc2de1d532f7236e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122057707"
---
# <a name="idebugportex2"></a>IDebugPortEx2
Questa interfaccia consente alla gestione del debug di sessione (SDM) di controllare i programmi e i processi in esecuzione su una porta.

## <a name="syntax"></a>Sintassi

```
IDebugPortEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un fornitore di porte personalizzato implementa questa interfaccia sullo stesso oggetto che implementa [IDebugPort2.](../../../extensibility/debugger/reference/idebugport2.md)

## <a name="notes-for-callers"></a>Note per i chiamanti
 SDM chiama [QueryInterface](/cpp/atl/queryinterface) `IDebugPort2` sull'interfaccia per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugPortEx2` .

|Metodo|Descrizione|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Avvia un file eseguibile.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Riprende l'esecuzione di un processo.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Determina se un processo può essere terminato.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Termina un processo.|
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Ottiene l'ID processo della porta stessa.|
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Ottiene un programma associato a un nodo di programma.|

## <a name="remarks"></a>Commenti
 Questa interfaccia è in genere privata tra SDM e il fornitore di porte personalizzato.

 Se lo si desidera, un motore di debug può cercare questa interfaccia nell'interfaccia [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) passata a [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) e usare [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) per avviare il programma. Questo non è tuttavia un requisito e un deret può eseguire qualsiasi operazione per avviare il programma di richiesta.

## <a name="requirements"></a>Requisiti
 Intestazione: portpriv.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
