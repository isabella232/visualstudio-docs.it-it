---
description: Restituisce il numero di argomenti del parametro di tipo per questa istanza.
title: 'IDebugGenericFieldInstance:: TypeArgumentCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TypeArgumentCount
- IDebugGenericFieldInstance::TypeArgumentCount
ms.assetid: e662c5ea-a5c1-478e-a268-5980dadffcd1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 034c180e41a2754347dd0eea7a81cb4ae64a0c2a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165358"
---
# <a name="idebuggenericfieldinstancetypeargumentcount"></a>IDebugGenericFieldInstance::TypeArgumentCount
Restituisce il numero di argomenti del parametro di tipo per questa istanza.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT TypeArgumentCount(
   ULONG32* pcArgs
);
```

```csharp
int TypeArgumentCount(
   ref uint pcArgs
);
```

## <a name="parameters"></a>Parametri
`pcArgs`\
[in, out] Numero di argomenti di parametro di tipo per questa istanza.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Se, ad esempio, List \<int> , questo metodo restituisce 1 e, se List \<int,float2> questo metodo restituisce 2. Questo metodo restituisce 0 se non sono presenti argomenti di tipo.

## <a name="see-also"></a>Vedi anche
- [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)
