---
description: Ottiene il campo a cui è associato l'attributo personalizzato.
title: 'IDebugCustomAttribute:: GetParentField | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a4af4569b64a41fc84a09c7e8f2ce0a8f6b42e86
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154509"
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
out Restituisce l'oggetto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che rappresenta il campo a cui è associato l'attributo personalizzato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Chiamare il metodo [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) sull'oggetto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) restituito per determinare il tipo di campo padre.

## <a name="see-also"></a>Vedi anche
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
