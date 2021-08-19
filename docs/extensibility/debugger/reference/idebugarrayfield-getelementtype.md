---
description: Ottiene il tipo di elemento nella matrice.
title: IDebugArrayField::GetElementType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetElementType
helpviewer_keywords:
- IDebugArrayField::GetElementType method
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 346ca568371d1ea0dfe04d6f6854e13bb8c23ab6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122072812"
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
[out] Restituisce un [oggetto IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che descrive il tipo di elemento.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 [L'oggetto IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md) presuppone che tutti gli elementi della matrice siano dello stesso tipo.

## <a name="see-also"></a>Vedi anche
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
