---
description: Questo metodo indica al motore di debug le informazioni sullo stato di JustMyCode.
title: 'IDebugEngine3:: SetJustMyCodeState | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a81fa4bda506cf1be27f658b071910e7c8ccd8a7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153703"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Questo metodo indica al motore di debug le informazioni sullo stato di JustMyCode.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetJustMyCodeState(
   BOOL           fUpdate,
   DWORD          dwModules,
   JMC_CODE_SPEC* rgJMCSpec
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
in Diverso da zero ( `TRUE` ) per aggiornare le informazioni correnti, zero ( `FALSE` ) per reimpostare tutte le informazioni (ignorando qualsiasi elemento precedentemente impostato).

`dwModules`\
in Numero di strutture di informazioni in `rgJMCSpec.`

`rgJMCSpec`\
in Matrice di strutture di [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) da utilizzare.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice di errore.

## <a name="remarks"></a>Commenti
 JustMyCode è il concetto di debug solo del codice che appartiene a un utente e che ignora tutto il codice intermedio, ad esempio il codice di sistema, anche se il codice sorgente è disponibile per il codice di sistema.

## <a name="see-also"></a>Vedi anche
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)
