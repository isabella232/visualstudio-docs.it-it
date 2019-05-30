---
title: IDebugBinder3::GetTypeArguments | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetTypeArguments
helpviewer_keywords:
- IDebugBinder3::GetTypeArguments method
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9d301dbb99e88ba4552ad59d9116f64dc032371
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330748"
---
# <a name="idebugbinder3gettypearguments"></a>IDebugBinder3::GetTypeArguments
Questo metodo recupera un elenco dei tipi di argomento associato all'oggetto.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetTypeArguments(
   UINT          skip,
   UINT          count,
   IDebugField** ppFields,
   UINT*         pFetched
);
```

```csharp
int GetTypeArguments(
   uint          skip,
   uint          count,
   IDebugField[] ppFields,
   out uint      pFetched
);
```

## <a name="parameters"></a>Parametri
`skip`\
[in] Numero di campi da ignorare prima di ottenere i tipi di argomento.

`count`\
[in] Il numero di campi dell'argomento da restituire (specifica anche la dimensione del `ppFields` matrice).

`ppFields`\
[in, out] Matrice di campi che verranno compilati in fase di restituzione di questo metodo.

`pFetched`\
[out] \(facoltativo) Il numero di argomenti tipo campi effettivamente restituiti.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 È possibile ottenere in anticipo il numero di tipi di argomento con [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md).

## <a name="see-also"></a>Vedere anche
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)