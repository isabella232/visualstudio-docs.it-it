---
description: Ottiene il conteggio degli elementi nella matrice.
title: IDebugArrayObject::GetCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 402a73f6e9f0b866c661b5508d6c785e29d6236f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627582"
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
[out] Restituisce il conteggio.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo vede tutti gli elementi di un oggetto matrice come matrice unidimensionale, anche se l'oggetto matrice è multidimensionale. Ad esempio, dato la matrice `myarray[3][2][6]` , questo metodo restituisce 36 nel parametro `pdwElements` . Usare il [metodo GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) per recuperare i singoli elementi uno alla volta.

## <a name="see-also"></a>Vedi anche
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
