---
description: Crea un oggetto che usa un costruttore, date le impostazioni dei flag di valutazione e un valore di timeout.
title: 'IDebugFunctionObject2:: CreateObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4cd5eb81972af35b84c688e34b8cbc285c4723c2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143142"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
Crea un oggetto che usa un costruttore, date le impostazioni dei flag di valutazione e un valore di timeout.

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
in Oggetto [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) che rappresenta il costruttore dell'oggetto da creare.

`dwArgs`\
in Numero di parametri nella `pArg` matrice. Rappresenta il numero di parametri passati al costruttore.

`pArgs`\
in Matrice di oggetti [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta i parametri passati al costruttore.

`dwEvalFlags`\
in Combinazione di flag dell'enumerazione [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) che specificano la modalità di esecuzione della valutazione.

`dwTimeout`\
in Tempo massimo, in millisecondi, di attesa prima che venga restituito da questo metodo. Usare **infinito** per un'attesa indefinita.

`ppObject`\
out Restituisce un **IDebugObject** che rappresenta l'oggetto appena creato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Chiamare questo metodo per creare un oggetto che rappresenta un'istanza di una classe o un altro tipo complesso che richiede un costruttore, ovvero un parametro.

## <a name="see-also"></a>Vedi anche
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
