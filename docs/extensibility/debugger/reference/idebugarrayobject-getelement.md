---
title: 'IDebugArrayObject:: GetElement | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 61085ee3e8323b2aa297473cffeebb998fc5c11b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870181"
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
in Indice dell'elemento.

`ppElement`\
out Restituisce un'interfaccia [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta l'elemento.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo considera tutti gli elementi di un oggetto matrice come matrice unidimensionale, anche se l'oggetto matrice è multidimensionale. Ad esempio, data la matrice `myarray[3][2][6]` e un `dwIndex` parametro di 20, questo metodo restituisce l'elemento da `myarray[1][1][2]` e un `dwIndex` parametro di 21 restituisce l'elemento da `myarray[1][1][3]` . Usare il metodo [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) per determinare il numero totale di elementi nella matrice.

## <a name="see-also"></a>Vedi anche
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
