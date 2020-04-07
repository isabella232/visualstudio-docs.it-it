---
title: Proprietà IDebugEngineLaunch2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee77cbd680df2c851d53aac298605023227fa6f8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730502"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
Utilizzato da un motore di debug (DE) per avviare e terminare i programmi.

## <a name="syntax"></a>Sintassi

```
IDebugEngineLaunch2 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata da un DE personalizzato se ha requisiti speciali per l'avvio di un processo che non può essere gestito interamente da una porta personalizzata. Questo è in genere il caso quando il DE fa parte di un interprete e il processo in fase di debug è uno script: l'interprete deve essere lanciato prima e quindi lo script viene caricato e avviato. Una porta può avviare l'interprete, ma lo script può richiedere una gestione speciale (che è dove il DE ha un ruolo). Questa interfaccia viene implementata solo se esistono requisiti univoci per l'avvio di un programma che una porta personalizzata non è in grado di gestire.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene chiamata dal gestore di sessione di debug (SDM) se il modello SDM può ottenere questa interfaccia dal [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interfaccia (utilizzando QueryInterface). Se questa interfaccia può essere ottenuta, il SDM sa che il DE ha requisiti speciali e chiama questa interfaccia per avviare il programma invece di avere la porta avviarlo.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugEngineLaunch2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Avvia un processo tramite il DE.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Riprende l'esecuzione del processo.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Determina se un processo può essere terminato.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Termina un processo.|

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
