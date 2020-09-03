---
title: 'IDebugProgram2:: alleghi | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Attach
helpviewer_keywords:
- IDebugProgram2::Attach
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7d0b182ba7a873816e3a7aa32d39beb2c63cc5ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723144"
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
Si connette al programma.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback
);
```

## <a name="parameters"></a>Parametri
`pCallback`\
in Oggetto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) da utilizzare per la notifica degli eventi di debug.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Nella tabella seguente vengono illustrati alcuni possibili codici di errore.

|Valore|Descrizione|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Il programma specificato è già collegato al debugger.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Si è verificata una violazione della sicurezza durante la procedura di associazione.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Non è possibile collegare un programma desktop al debugger.|

## <a name="remarks"></a>Osservazioni
 Un motore di debug (DE) non chiama mai questo metodo per la connessione a un programma. Se il DE viene eseguito nello spazio degli indirizzi del programma, viene chiamato il metodo [Onattribute](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) . Se il DE viene eseguito nello spazio degli indirizzi SDM (Session Debug Manager), viene chiamato il metodo di [associazione](../../../extensibility/debugger/reference/idebugengine2-attach.md) .

## <a name="see-also"></a>Vedere anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
