---
description: Questo metodo restituisce una copia dell'enumerazione dei campi corrente come oggetto separato.
title: IEnumDebugFields::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Clone
helpviewer_keywords:
- IEnumDebugFields::Clone method
ms.assetid: 7ec265a8-696f-45ce-a2a2-0a83e96fee1b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b31ce817852f1ada7ae25326cd3b63a283b5d04b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122095608"
---
# <a name="ienumdebugfieldsclone"></a>IEnumDebugFields::Clone
Questo metodo restituisce una copia dell'enumerazione corrente come oggetto separato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Clone(
   IEnumDebugFields** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametri
`ppEnum`\
[out] Restituisce una copia di questa enumerazione come oggetto separato.

## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 La copia dell'enumerazione ha lo stesso stato dell'originale al momento della chiamata a questo metodo. Tuttavia, gli stati della copia e dell'originale sono separati e possono essere modificati singolarmente.

## <a name="see-also"></a>Vedi anche
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
