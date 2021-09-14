---
description: Rimuove l'eccezione specificata in modo che non sia più gestita dal motore di debug.
title: IDebugEngine2::RemoveSetException | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27987f582606f1978c90ff09f36c6e75714040ea
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636331"
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
Rimuove l'eccezione specificata in modo che non sia più gestita dal motore di debug.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT RemoveSetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int RemoveSetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>Parametri
`pException`\
[in] Struttura [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) che descrive l'eccezione da rimuovere.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 L'eccezione da rimuovere deve essere stata impostata in precedenza da una chiamata precedente al [metodo SetException.](../../../extensibility/debugger/reference/idebugengine2-setexception.md)

 Per rimuovere tutte le eccezioni impostate contemporaneamente, chiamare il [metodo RemoveAllSetExceptions.](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)

## <a name="see-also"></a>Vedi anche
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
