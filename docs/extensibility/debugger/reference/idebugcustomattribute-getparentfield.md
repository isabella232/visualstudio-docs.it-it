---
title: IDebugCustomAttribute::GetParentField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6a99310520109dad6a1b8084405119e0a106ad89
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350054"
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
[out] Restituisce il [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetto che rappresenta il campo a cui è associato l'attributo personalizzato.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Chiamare il [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) metodo sull'oggetto restituito [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) è oggetto di determinare quale tipo di campo padre.

## <a name="see-also"></a>Vedere anche
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)