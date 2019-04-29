---
title: IDebugEngine2::CauseBreak | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fa0d559887019a697b820a5a6c91f80b78c6b713
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920956"
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