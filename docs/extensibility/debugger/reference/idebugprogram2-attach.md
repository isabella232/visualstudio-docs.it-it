---
description: Si collega al programma.
title: IDebugProgram2::Attach | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 74dd257a1380880ab1ea1958862f81e2d069694f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122030217"
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
Si collega al programma.

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
[in] Oggetto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) da usare per la notifica degli eventi di debug.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Nella tabella seguente vengono illustrati alcuni codici di errore possibili.

|Valore|Descrizione|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Il programma specificato è già collegato al debugger.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Si è verificata una violazione di sicurezza durante la procedura di collegamento.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Un programma desktop non può essere collegato al debugger.|

## <a name="remarks"></a>Commenti
 Un motore di debug non chiama mai questo metodo per connettersi a un programma. Se de viene eseguito nello spazio di indirizzi del programma, viene chiamato il metodo [OnAttach.](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) Se de viene eseguito nello spazio di indirizzi di Gestione debug sessione (SDM), viene [chiamato il](../../../extensibility/debugger/reference/idebugengine2-attach.md) metodo Attach.

## <a name="see-also"></a>Vedi anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
