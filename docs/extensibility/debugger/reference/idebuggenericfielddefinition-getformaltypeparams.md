---
title: IDebugGenericFieldDefinition::GetFormalTypeParams | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetFormalTypeParams
- IDebugGenericFieldDefinition::GetFormalTypeParams
ms.assetid: cadbd6a1-bc7c-4aff-8777-5396b7a23c3e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22b02361b13a1fb639afc74fa7e0d8421a3ae19c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715778"
---
# <a name="idebuggenericfielddefinitiongetformaltypeparams"></a>IDebugGenericFieldDefinition::GetFormalTypeParams
Recupera i parametri di tipo dato il numero di parametri.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetFormalTypeParams(
   ULONG32                   cParams,
   IDebugGenericParamField** ppParams,
   ULONG32*                  pcParams
);
```

```csharp
int GetFormalTypeParams(
   uint                          cParams,
   out IDebugGenericParamField[] ppParams,
   ref uint                      pcParams
);
```

#### <a name="parameters"></a>Parametri
 `cParams`

 [in] Numero di parametri.

 `ppParams`

 [out] Matrice di parametri di tipo.

 `pcParams`

 [in, out] Numero di parametri in di `ppParams` matrice.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Restituisce i parametri di tipo nell'ordine da sinistra a destra. Ad esempio dizionario\<K, V > restituisce IDebugFormalGenericParameters {K, V}.

## <a name="see-also"></a>Vedere anche
- [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)