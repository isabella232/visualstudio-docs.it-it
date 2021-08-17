---
description: Il motore di debug invia questa interfaccia a Gestione debug sessione quando il programma sta per eseguire la prima istruzione del codice utente.
title: IDebugEntryPointEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEntryPointEvent2
helpviewer_keywords:
- IDebugEntryPointEvent2 interface
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: b41a6b95f0a7f0a842656e798f21aae1273cfc5a16869399de57d94604f180f0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121389956"
---
# <a name="idebugentrypointevent2"></a>IDebugEntryPointEvent2
Il motore di debug invia questa interfaccia a Gestione debug sessione quando il programma sta per eseguire la prima istruzione del codice utente.

## <a name="syntax"></a>Sintassi

```
IDebugEntryPointEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 De implementa questa interfaccia come parte delle normali operazioni. [L'interfaccia IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia. SDM usa [QueryInterface per](/cpp/atl/queryinterface) accedere all'interfaccia. `IDebugEvent2`

## <a name="notes-for-callers"></a>Note per i chiamanti
 De crea e invia questo oggetto evento quando il programma in fase di debug è stato caricato ed è pronto per eseguire la prima istruzione del codice utente. L'evento viene inviato usando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegato al programma di cui è in corso il debug.

## <a name="remarks"></a>Commenti
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) viene inviato quando il programma sta per eseguire la prima istruzione. Ad esempio, `IDebugEntryPoint2` viene inviato quando il programma sta per eseguire la funzione dell'utente. `main`

 Quando de invia `IDebugEntryPointEvent2` , la posizione del codice corrente deve essere alla prima istruzione del codice utente, ad esempio `main` .

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
