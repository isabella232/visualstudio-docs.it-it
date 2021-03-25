---
description: Crea un oggetto usando un costruttore.
title: 'IDebugFunctionObject:: CreateObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27608634859ae96a8fb9461076397bb6df53570d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073560"
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
Crea un oggetto usando un costruttore.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CreateObject( 
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject(
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   out IDebugObject     ppObject
);
```

## <a name="parameters"></a>Parametri
`pConstructor`\
in Oggetto [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) che rappresenta il costruttore dell'oggetto da creare.

`dwArgs`\
in Numero di parametri nella `pArg` matrice. Rappresenta il numero di parametri passati al costruttore.

`pArg`\
in Matrice di oggetti [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta i parametri passati al costruttore.

`ppObject`\
out Restituisce un `IDebugObject` oggetto che rappresenta l'oggetto appena creato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Chiamare questo metodo per creare un oggetto che rappresenta un'istanza di una classe (o un altro tipo complesso che richiede un costruttore) che rappresenta un parametro per la funzione rappresentata dall'interfaccia [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

 Se il parametro dell'oggetto non richiede un costruttore, chiamare il metodo [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) .

## <a name="see-also"></a>Vedi anche
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)
