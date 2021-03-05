---
description: Ottiene il numero di elementi nella matrice.
title: 'IDebugArrayObject:: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4dafff955eb0801ffe13f76f61d8f7451398e41e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158696"
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
out Restituisce il conteggio.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo considera tutti gli elementi di un oggetto matrice come matrice unidimensionale, anche se l'oggetto matrice è multidimensionale. Ad esempio, in base alla matrice `myarray[3][2][6]` , questo metodo restituisce 36 nel `pdwElements` parametro. Usare il metodo [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) per recuperare i singoli elementi uno alla volta.

## <a name="see-also"></a>Vedi anche
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
