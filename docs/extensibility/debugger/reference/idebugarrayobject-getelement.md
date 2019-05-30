---
title: IDebugArrayObject::GetElement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 527302a2e6d6fc2884107e3773402adc56b881c7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322213"
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
[in] L'indice di elemento.

`ppElement`\
[out] Restituisce un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaccia che rappresenta l'elemento.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Questo metodo considera tutti gli elementi di un oggetto matrice come una matrice unidimensionale, anche se l'oggetto di matrice è multidimensionale. Si consideri ad esempio la matrice `myarray[3][2][6]` e una `dwIndex` parametro pari a 20, questo metodo restituisce l'elemento dal `myarray[1][1][2]`e un `dwIndex` restituisce l'elemento dal parametro di 21 `myarray[1][1][3]`. Usare la [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) metodo per determinare il numero totale di elementi nella matrice.

## <a name="see-also"></a>Vedere anche
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)