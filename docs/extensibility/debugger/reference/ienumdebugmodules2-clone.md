---
description: Restituisce una copia dell'enumerazione dei moduli corrente come oggetto separato.
title: 'IEnumDebugModules2:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2::Clone
helpviewer_keywords:
- IEnumDebugModules2::Clone
ms.assetid: fd6d3abc-20d9-4f6f-9c8e-5bd29f68d47d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 699afcaabdf88ca8b2b6ea60b6ad06dfcb12e3bd
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224889"
---
# <a name="ienumdebugmodules2clone"></a>IEnumDebugModules2::Clone
Restituisce una copia dell'enumerazione corrente come oggetto separato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Clone(
   IEnumDebugModules2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugModules2 ppEnum
);
```

## <a name="parameters"></a>Parametri
`ppEnum`\
[out] Restituisce una copia di questa enumerazione come oggetto separato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 La copia dell'enumerazione ha lo stesso stato dell'originale al momento della chiamata di questo metodo. Tuttavia, gli Stati della copia e dell'originale sono separati e possono essere modificati singolarmente.

## <a name="see-also"></a>Vedi anche
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
