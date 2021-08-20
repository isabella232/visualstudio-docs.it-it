---
description: Ottiene il nome di un thread.
title: IDebugThread2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7028a22b391fc1ba79c4d47a9a348086db9dfea7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126089"
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
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Il nome recuperato è sempre un nome che può essere visualizzato e questo nome descrive il thread. Il nome del thread può essere derivato da un'architettura di runtime che supporta thread denominati oppure può essere un nome derivato dal motore di debug. In alternativa, il nome del thread può essere impostato da una chiamata al [metodo SetThreadName.](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)

## <a name="see-also"></a>Vedi anche
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)
