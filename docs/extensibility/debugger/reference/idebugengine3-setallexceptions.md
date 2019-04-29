---
title: IDebugEngine3::SetAllExceptions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetAllExceptions
helpviewer_keywords:
- IDebugEngine3::SetAllExceptions
ms.assetid: 8f03a6ac-a854-42f7-933c-a2df1b351975
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33735e047f0ac0266648afd2ffb4de0cbc908a25
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920920"
---
# <a name="idebugengine3setallexceptions"></a>IDebugEngine3::SetAllExceptions
Questo metodo imposta lo stato di tutte le eccezioni in sospeso.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetAllExceptions(
   EXCEPTION_STATE dwState
);
```

```csharp
int SetAllExceptions(
   enum_EXCEPTION_STATE dwState
);
```

#### <a name="parameters"></a>Parametri
 `dwState`

 [in] Uno dei [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) valori.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)