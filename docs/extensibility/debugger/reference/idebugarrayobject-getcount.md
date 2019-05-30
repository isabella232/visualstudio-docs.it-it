---
title: IDebugArrayObject::GetCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ac21ac30e1f4511efa1ec8a7fe27129bf2ddb3a1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321656"
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
Ottiene il numero di elementi nella matrice.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetCount( 
   DWORD* pdwElements
);
```

```csharp
int GetCount(
   out uint pdwElements
);
```

## <a name="parameters"></a>Parametri
`pdwElements`\
[out] Restituisce il conteggio.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Questo metodo considera tutti gli elementi di un oggetto matrice come una matrice unidimensionale, anche se l'oggetto di matrice è multidimensionale. Si consideri ad esempio la matrice `myarray[3][2][6]`, questo metodo restituirà 36 nel `pdwElements` parametro. Usare la [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) metodo per recuperare i singoli elementi uno alla volta.

## <a name="see-also"></a>Vedere anche
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)