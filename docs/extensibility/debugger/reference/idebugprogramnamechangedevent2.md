---
title: Proprietà IDebugProgramNameChangedEvent2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramNameChangedEvent2 interface
ms.assetid: be1f1cd5-0b2f-435c-a052-dca28a7c978d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae58728601c3adbe6e37a00fd0694a5d71eef0b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722154"
---
# <a name="idebugprogramnamechangedevent2"></a>IDebugProgramNameChangedEvent2
Inviato dal motore di debug (DE) al gestore di sessione di debug (SDM) quando il nome di un programma viene modificato.

## <a name="syntax"></a>Sintassi

```
IDebugProgramNameChangedEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il DE implementa questa interfaccia per segnalare che il nome del programma è stato modificato. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata sullo stesso oggetto di questa interfaccia. Il modello SDM utilizza [QueryInterface](/cpp/atl/queryinterface) per accedere il **IDebugEvent2** interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il DE crea e invia questo oggetto evento per segnalare una modifica del nome del programma. Il DE invia questo evento utilizzando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) che viene fornita dal modello SDM quando collegato al programma in fase di debug. Il fornitore della porta personalizzata invia questo evento utilizzando l'interfaccia I.

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
