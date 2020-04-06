---
title: Proprietà IDebugArrayObject::GetElement . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e29fe09905119057224b45b455e4f56e5ce904af
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736177"
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
[fuori] Restituisce un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaccia che rappresenta l'elemento.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 Questo metodo vede tutti gli elementi di un oggetto matrice come matrice unidimensionale, anche se l'oggetto matrice è multidimensionale. Ad esempio, dati `myarray[3][2][6]` la `dwIndex` matrice e un parametro pari `myarray[1][1][2]`a 20, questo metodo restituirebbe l'elemento da , e un `dwIndex` parametro 21 restituirebbe l'elemento da `myarray[1][1][3]`. Utilizzare il [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) metodo per determinare il numero totale di elementi nella matrice.

## <a name="see-also"></a>Vedere anche
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
