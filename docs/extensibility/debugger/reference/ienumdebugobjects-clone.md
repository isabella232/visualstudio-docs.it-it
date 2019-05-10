---
title: IEnumDebugObjects::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Clone
helpviewer_keywords:
- IEnumDebugObjects::Clone method
ms.assetid: cb7df109-d29a-4218-b900-6809091459dd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 76ae819deecaa76d37054235b6bed295278ca37d
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2019
ms.locfileid: "65223451"
---
# <a name="ienumdebugobjectsclone"></a>IEnumDebugObjects::Clone
Questo metodo restituisce una copia dell'enumerazione corrente come oggetto separato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Clone(
   IEnumDebugObjects** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugObjects ppEnum
);
```

## <a name="parameters"></a>Parametri
 `ppEnum`\

 [out] Restituisce una copia di questa enumerazione come oggetto separato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 La copia dell'enumerazione ha lo stesso stato originale al momento che questo metodo viene chiamato. Tuttavia, gli Stati dell'originale e la copia sono separati e possono essere modificati singolarmente.

## <a name="see-also"></a>Vedere anche
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)