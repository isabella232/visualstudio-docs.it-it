---
description: Questo metodo ottiene informazioni indipendenti dal tipo sul simbolo o sul tipo.
title: 'IDebugField:: GetTypeInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetTypeInfo
helpviewer_keywords:
- IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9ea120cb58faa28bbb8168800ef6e35f707d879f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073703"
---
# <a name="idebugfieldgettypeinfo"></a>IDebugField::GetTypeInfo
Questo metodo ottiene informazioni indipendenti dal tipo sul simbolo o sul tipo.

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
out Restituisce le informazioni sul tipo nella struttura [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) fornita.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Le informazioni indipendenti dal tipo includono, ad esempio, AppDomain, il modulo e la classe che contiene il simbolo.

## <a name="see-also"></a>Vedi anche
- [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
