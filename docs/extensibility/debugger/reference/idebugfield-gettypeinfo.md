---
title: IDebugField::GetTypeInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetTypeInfo
helpviewer_keywords:
- IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fc48442e27315e289c812c14e0ae70d8b8fd437a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333109"
---
# <a name="idebugfieldgettypeinfo"></a>IDebugField::GetTypeInfo
Questo metodo ottiene indipendenti dal tipo di informazioni sul simbolo o tipo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetTypeInfo( 
   TYPE_INFO* pTypeInfo
);
```

```csharp
int GetTypeInfo(
   TYPE_INFO[] pTypeInfo
);
```

## <a name="parameters"></a>Parametri
`pTypeInfo`\
[out] Restituisce informazioni sul tipo nella classe fornita [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) struttura.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Informazioni indipendenti dal tipo includerà, ad esempio, l'AppDomain, il modulo e la classe che contiene il simbolo.

## <a name="see-also"></a>Vedere anche
- [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)