---
description: Ottiene un elemento della matrice.
title: IDebugArrayObject::GetElement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8bc91b0576e98b5c27659ca9ae90ef37001e790c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122145444"
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
Ottiene un elemento della matrice.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetElement( 
   DWORD          dwIndex,
   IDebugObject** ppElement
);
```

```csharp
int GetElement(
   [In] uint dwIndex,
   out IDebugObject ppElement
);
```

## <a name="parameters"></a>Parametri
`dwIndex`\
[in] Indice dell'elemento.

`ppElement`\
[out] Restituisce [un'interfaccia IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta l'elemento.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo vede tutti gli elementi di un oggetto matrice come matrice unidimensionale, anche se l'oggetto matrice è multidimensionale. Ad esempio, dati la matrice e un parametro `myarray[3][2][6]` di 20, questo metodo restituirebbe l'elemento da e un parametro `dwIndex` `myarray[1][1][2]` di 21 restituirebbe `dwIndex` l'elemento da `myarray[1][1][3]` . Usare il [metodo GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) per determinare il numero totale di elementi nella matrice.

## <a name="see-also"></a>Vedi anche
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
