---
title: IDebugGenericFieldInstance::TypeArgumentCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TypeArgumentCount
- IDebugGenericFieldInstance::TypeArgumentCount
ms.assetid: e662c5ea-a5c1-478e-a268-5980dadffcd1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5a6b55d51cd2db25da1b51af84172d64c682245
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689941"
---
# <a name="idebuggenericfieldinstancetypeargumentcount"></a>IDebugGenericFieldInstance::TypeArgumentCount
Restituisce il numero del tipo di argomenti di parametro per questa istanza.

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

#### <a name="parameters"></a>Parametri
 `pcArgs`

 [in, out] Numero di argomenti di parametro di tipo per questa istanza.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Ad esempio, se elenco\<int >, questo metodo restituisce 1 e, se elenco\<int, float2 > questo metodo restituisce 2. Questo metodo restituisce 0 se non sono presenti argomenti tipo.

## <a name="see-also"></a>Vedere anche
- [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)