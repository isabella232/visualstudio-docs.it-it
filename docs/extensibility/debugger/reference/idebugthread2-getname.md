---
title: IDebugThread2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d6b57aac800027a4a591c3ea683761e19a31462c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320218"
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
[out] Restituisce il nome del thread.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Il nome recuperato è sempre un nome che può essere visualizzato e questo nome viene descritto il thread. Il nome del thread può essere derivato da un'architettura di runtime che supporta denominate thread o potrebbe essere un nome derivato dal motore di debug. In alternativa, è possibile impostare il nome del thread da una chiamata per il [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) (metodo).

## <a name="see-also"></a>Vedere anche
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)