---
title: Metodo IDebugArrayField::GetElementType . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetElementType
helpviewer_keywords:
- IDebugArrayField::GetElementType method
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3870f28ffb62239d0a092093d28c83d25e92bd31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736327"
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
[fuori] Restituisce un [Oggetto IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che descrive il tipo di elemento.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 Il [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md) oggetto presuppone che tutti gli elementi della matrice sono dello stesso tipo.

## <a name="see-also"></a>Vedere anche
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
