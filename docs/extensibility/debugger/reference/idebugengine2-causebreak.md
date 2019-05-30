---
title: IDebugEngine2::CauseBreak | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93f9937609a09439b265946e76f0af0381d488f1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330139"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
Le richieste che tutti i programmi in fase di debug da questo motore di debug (DE) per arrestare l'esecuzione la volta successiva che uno dei relativi thread tenta di eseguire.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CauseBreak( 
   void 
);
```

```csharp
int CauseBreak();
```

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Questo metodo è asincrono: un' [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) evento viene inviato quando il programma quindi tenta di eseguire dopo che questo metodo viene chiamato.

## <a name="see-also"></a>Vedere anche
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)