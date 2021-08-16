---
description: Crea un oggetto che utilizza un costruttore in base alle impostazioni del flag di valutazione e a un valore di timeout.
title: Interfaccia IDebugFunctionObject2::CreateObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: abe71179784d69ed78d372fd5e3b3bb1e8728c0b52d20b532556f145e052f7e3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121389787"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
Crea un oggetto che utilizza un costruttore in base alle impostazioni del flag di valutazione e a un valore di timeout.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CreateObject (
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject (
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   out IDebugObject**   ppObject
);
```

## <a name="parameters"></a>Parametri
`pConstructor`\
[in] Oggetto [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) che rappresenta il costruttore dell'oggetto da creare.

`dwArgs`\
[in] Numero di parametri nella `pArg` matrice. Rappresenta il numero di parametri passati al costruttore.

`pArgs`\
[in] Matrice di [oggetti IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta i parametri passati al costruttore.

`dwEvalFlags`\
[in] Combinazione di flag [dell'enumerazione EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) che specificano la modalità di esecuzione della valutazione.

`dwTimeout`\
[in] Tempo massimo di attesa, in millisecondi, prima della restituzione da questo metodo. Usare **INFINITE** per un'attesa illimitata.

`ppObject`\
[out] Restituisce un **oggetto IDebugObject** che rappresenta l'oggetto appena creato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Chiamare questo metodo per creare un oggetto che rappresenta un'istanza di una classe o un altro tipo complesso che richiede un costruttore, che è un parametro.

## <a name="see-also"></a>Vedi anche
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
