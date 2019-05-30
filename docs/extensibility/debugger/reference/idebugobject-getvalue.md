---
title: IDebugObject::GetValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59d58e136045bb4177755c981f91974f9ac2fa77
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323654"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Ottiene il valore dell'oggetto come una serie consecutiva di byte.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int GetValue(
   ref byte[] pValue,
   uint nSize
);
```

## <a name="parameters"></a>Parametri
`pValue`\
[in, out] Matrice che viene compilata con una serie consecutiva di byte che rappresenta il valore dell'oggetto.

`nSize`\
[in] Il numero massimo di byte da recuperare.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Ottenere il numero totale di byte di valore che può essere recuperato chiamando il [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md) (metodo).

## <a name="see-also"></a>Vedere anche
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)