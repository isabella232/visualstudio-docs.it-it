---
description: Imposta il valore dell'oggetto da una serie di byte consecutivi.
title: 'IDebugObject:: SetValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 972281335b964679f38693182e42c4e64074dffa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167152"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
Imposta il valore dell'oggetto da una serie di byte consecutivi.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int SetValue(
   byte[] pValue,
   uint   nSize
);
```

## <a name="parameters"></a>Parametri
`pValue`\
in Matrice di byte che rappresenta il nuovo valore.

`nSize`\
in Dimensioni in byte del valore.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 I valori nella matrice vengono copiati in questo oggetto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , sostituendo qualsiasi valore esistente. La dimensione del nuovo valore può essere maggiore o minore del valore esistente. `IDebugObject`Non può essere un riferimento null.

## <a name="see-also"></a>Vedi anche
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
