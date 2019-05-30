---
title: IDebugArrayField::GetElementType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetElementType
helpviewer_keywords:
- IDebugArrayField::GetElementType method
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13dabbf61999e8558fe08ecb65169dd43302d98f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320962"
---
# <a name="idebugarrayfieldgetelementtype"></a>IDebugArrayField::GetElementType
Ottiene il tipo di elemento nella matrice.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetElementType( 
   IDebugField** ppType
);
```

```csharp
int GetElementType(
   out IDebugField ppType
);
```

## <a name="parameters"></a>Parametri
`ppType`\
[out] Restituisce un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che descrive il tipo di elemento.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Il [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md) oggetto presuppone che tutti gli elementi della matrice sono dello stesso tipo.

## <a name="see-also"></a>Vedere anche
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)