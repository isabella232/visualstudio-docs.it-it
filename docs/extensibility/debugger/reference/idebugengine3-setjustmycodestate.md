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
ms.openlocfilehash: fb528d3f8c12e21f327b168a88d4df070e2863188fcc8e1580135db9685c1ca4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121307778"
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
