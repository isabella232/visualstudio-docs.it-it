---
title: IDebugThread2::GetName . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d4828b573585969154f2ad1d484c9fcdf767417
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718767"
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
Ottiene il nome di un thread.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetName ( 
   BSTR* pbstrName
);
```

```csharp
int GetName ( 
   out string pbstrName
);
```

## <a name="parameters"></a>Parametri
`pbstrName`\
[fuori] Restituisce il nome del thread.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Il nome recuperato è sempre un nome che può essere visualizzato e questo nome descrive il thread. Il nome del thread potrebbe essere derivato da un'architettura di runtime che supporta i thread denominati o potrebbe essere un nome derivato dal motore di debug. In alternativa, il nome del thread può essere impostato da una chiamata al [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) metodo.

## <a name="see-also"></a>Vedere anche
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)
