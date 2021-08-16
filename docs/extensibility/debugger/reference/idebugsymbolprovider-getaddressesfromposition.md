---
description: Questo metodo esegue il mapping di una posizione del documento in una matrice di indirizzi di debug.
title: IDebugSymbolProvider::GetAddressesFromPosition | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fde2dd02ffb0e8a314fb8c0c71c43fdc529fca587f64a7d05ca7641f42e40480
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121306894"
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
Questo metodo esegue il mapping di una posizione del documento in una matrice di indirizzi di debug.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetAddressesFromPosition( 
   IDebugDocumentPosition2* pDocPos,
   BOOL                     fStatmentOnly,
   IEnumDebugAddresses**    ppEnumBegAddresses,
   IEnumDebugAddresses**    ppEnumEndAddresses
);
```

```csharp
int GetAddressesFromPosition( 
   IDebugDocumentPosition2  pDocPos,
   bool                     fStatmentOnly,
   out IEnumDebugAddresses  ppEnumBegAddresses,
   out IEnumDebugAddresses  ppEnumEndAddresses
);
```

## <a name="parameters"></a>Parametri
`pDocPos`\
[in] Posizione del documento.

`fStatmentOnly`\
[in] Se TRUE, limita gli indirizzi di debug a una singola istruzione.

`ppEnumBegAddresses`\
[out] Restituisce un enumeratore per gli indirizzi di debug iniziali associati a questa istruzione o riga.

`ppEnumEndAddresses`\
[out] Restituisce un [enumeratore IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) per gli indirizzi di debug finali associati a questa istruzione o riga.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Una posizione del documento indica in genere un intervallo di righe di origine. Questo metodo fornisce gli indirizzi di debug iniziale e finale associati a queste righe. Alcuni linguaggi consentono istruzioni che si estendono su più righe o righe che contengono più di un'istruzione. Questo metodo fornisce un flag per limitare gli indirizzi di debug a una singola istruzione.

 È possibile che una singola istruzione abbia più indirizzi di debug, come nel caso dei modelli.

## <a name="see-also"></a>Vedi anche
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
