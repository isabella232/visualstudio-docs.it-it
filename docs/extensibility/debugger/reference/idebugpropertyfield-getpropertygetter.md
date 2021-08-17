---
description: Ottiene il metodo che ottiene la proprietà.
title: IDebugPropertyField::GetPropertyGetter | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField::GetPropertyGetter
helpviewer_keywords:
- IDebugPropertyField::GetPropertyGetter method
ms.assetid: ab9f861a-42ad-4a82-9ae6-2606176f755a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 55c7594863860923014eea4c213ad8dd59a8073156cacc0a8f4565d3700371c9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121338631"
---
# <a name="idebugpropertyfieldgetpropertygetter"></a>IDebugPropertyField::GetPropertyGetter
Ottiene il metodo che ottiene la proprietà.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetPropertyGetter( 
   IDebugMethodField** ppField
);
```

```cpp
int GetPropertyGetter(
   out IDebugMethodField ppField
);
```

## <a name="parameters"></a>Parametri
`ppField`\
[out] Restituisce un [oggetto IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) che rappresenta il metodo che ottiene la proprietà.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Per ottenere il metodo che imposta la proprietà, [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md) chiama il metodo .

## <a name="see-also"></a>Vedi anche
- [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)
- [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
