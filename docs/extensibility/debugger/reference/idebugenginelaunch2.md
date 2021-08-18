---
description: Usato da un motore di debug (DE) per avviare e terminare i programmi.
title: IDebugEngineLaunch2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 17f75a0a127b45f0fa1bc55c1399592e35cc1383
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122089173"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
Usato da un motore di debug (DE) per avviare e terminare i programmi.

## <a name="syntax"></a>Sintassi

```
IDebugEngineLaunch2 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata da un DE personalizzato se ha requisiti speciali per l'avvio di un processo che non può essere gestito interamente da una porta personalizzata. Questo è in genere il caso in cui de fa parte di un interprete e il processo di cui viene eseguito il debug è uno script: l'interprete deve essere avviato prima e quindi lo script viene caricato e avviato. Una porta può avviare l'interprete, ma lo script può richiedere una gestione speciale ,ovvero la de ha un ruolo. Questa interfaccia viene implementata solo se sono presenti requisiti univoci per l'avvio di un programma che una porta personalizzata non può gestire.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa interfaccia viene chiamata da Gestione debug sessione (SDM) se SDM può ottenere questa interfaccia [dall'interfaccia IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) (usando QueryInterface). Se questa interfaccia può essere ottenuta, SDM sa che il de ha requisiti speciali e chiama questa interfaccia per avviare il programma anziché fare in modo che la porta lo avvii.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugEngineLaunch2` .

|Metodo|Descrizione|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Avvia un processo tramite de.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Riprende l'esecuzione del processo.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Determina se un processo può essere terminato.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Termina un processo.|

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
