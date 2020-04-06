---
title: Proprietà IDebugEngine3::SetJustMyCodeState . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9930f8ecf0c2f9b6fff4ce1c9e3edb935c5a7912
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730677"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Questo metodo indica al motore di debug le informazioni sullo stato JustMyCode.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetJustMyCodeState(
   BOOL           fUpdate,
   DWORD          dwModules,
   JMC_CODE_SPEC* rgJMCSpec
);
```

```csharp
int SetJustMyCodeState(
   int             fUpdate,
   uint            dwModules,
   JMC_CODE_SPEC[] rgJMCSpec
);
```

## <a name="parameters"></a>Parametri
`fUpdate`\
[in] Diverso da`TRUE`zero ( ) per`FALSE`aggiornare le informazioni correnti, zero ( ) per reimpostare tutte le informazioni (ignorando qualsiasi elemento precedentemente impostato).

`dwModules`\
[in] Numero di strutture di informazione in`rgJMCSpec.`

`rgJMCSpec`\
[in] Matrice di [strutture di JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) da utilizzare.

## <a name="return-value"></a>Valore restituito
 Se ha `S_OK`esito positivo, restituisce ; in caso contrario, restituisce il codice di errore.

## <a name="remarks"></a>Osservazioni
 JustMyCode è il concetto di debug solo il codice che appartiene a un utente e ignorando tutto il codice intermedio, ad esempio il codice di sistema, anche se il codice sorgente è disponibile per tale codice di sistema.

## <a name="see-also"></a>Vedere anche
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)
