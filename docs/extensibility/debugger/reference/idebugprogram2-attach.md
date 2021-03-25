---
description: Si connette al programma.
title: 'IDebugProgram2:: alleghi | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Attach
helpviewer_keywords:
- IDebugProgram2::Attach
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4f9565ea0975e38ced80f0747560cf1a24b4150c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076225"
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

## <a name="remarks"></a>Commenti
 Un motore di debug (DE) non chiama mai questo metodo per la connessione a un programma. Se il DE viene eseguito nello spazio degli indirizzi del programma, viene chiamato il metodo [Onattribute](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) . Se il DE viene eseguito nello spazio degli indirizzi SDM (Session Debug Manager), viene chiamato il metodo di [associazione](../../../extensibility/debugger/reference/idebugengine2-attach.md) .

## <a name="see-also"></a>Vedi anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
