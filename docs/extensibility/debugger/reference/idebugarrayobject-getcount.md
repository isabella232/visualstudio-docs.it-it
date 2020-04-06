---
title: Proprietà IDebugArrayObject::GetCount . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d9d5e322b7bcd5238335c74caa21989f1f1962ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736202"
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
Ottiene il conteggio degli elementi nella matrice.

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
[fuori] Restituisce il conteggio.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 Questo metodo vede tutti gli elementi di un oggetto matrice come matrice unidimensionale, anche se l'oggetto matrice è multidimensionale. Ad esempio, data `myarray[3][2][6]`la matrice , questo `pdwElements` metodo restituirà 36 nel parametro. Utilizzare il [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) metodo per recuperare i singoli elementi uno alla volta.

## <a name="see-also"></a>Vedere anche
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
