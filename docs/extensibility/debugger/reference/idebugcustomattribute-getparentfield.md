---
title: Proprietà IDebugCustomAttribute::GetParentField . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fae84a4d02438335aea00c50dd9b89520d08bae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732694"
---
# <a name="idebugcustomattributegetparentfield"></a>IDebugCustomAttribute::GetParentField
Ottiene il campo a cui è associato l'attributo personalizzato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetParentField( 
   IDebugField** ppField
);
```

```csharp
int GetParentField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Parametri
`ppField`\
[fuori] Restituisce l'oggetto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che rappresenta il campo a cui è associato l'attributo personalizzato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 Chiamare il [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) metodo sull'oggetto restituito [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetto per determinare il tipo di campo padre è.

## <a name="see-also"></a>Vedere anche
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
