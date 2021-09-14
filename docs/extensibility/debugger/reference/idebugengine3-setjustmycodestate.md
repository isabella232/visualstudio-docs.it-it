---
description: Questo metodo indica al motore di debug le informazioni sullo stato di JustMyCode.
title: IDebugEngine3::SetJustMyCodeState | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b3f87d8a33c4b6ea43aebc487d09dafc87169eca
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710306"
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
[in] Diverso da zero ( ) per aggiornare le informazioni correnti, zero ( ) per reimpostare tutte le informazioni `TRUE` `FALSE` (ignorando tutto ciò che è stato impostato in precedenza).

`dwModules`\
[in] Numero di strutture di informazioni in `rgJMCSpec.`

`rgJMCSpec`\
[in] Matrice di [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) da usare.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice di errore.

## <a name="remarks"></a>Commenti
 JustMyCode è il concetto di debug solo del codice appartenente a un utente e di ignorare tutto il codice intermedio, ad esempio il codice di sistema, anche se il codice sorgente è disponibile per tale codice di sistema.

## <a name="see-also"></a>Vedi anche
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)
