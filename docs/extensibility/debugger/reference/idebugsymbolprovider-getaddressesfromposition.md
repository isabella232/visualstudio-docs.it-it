---
title: IDebugSymbolProvider::GetAddressesFromPosition | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b354c7c31f4633fd307f54954c5d5115436097d0
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66207354"
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
Questo metodo esegue il mapping di una posizione di documento in una matrice di indirizzi di debug.

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
[in] Se TRUE, limita gli indirizzi di debug per una singola istruzione.

`ppEnumBegAddresses`\
[out] Restituisce un enumeratore per gli indirizzi iniziali di debug associato con questa istruzione o la riga.

`ppEnumEndAddresses`\
[out] Restituisce un [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) enumeratore per gli indirizzi di debug finale associati a questa istruzione o la riga.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Una posizione del documento indica in genere un intervallo di righe di origine. Questo metodo fornisce il valore iniziale e finale debug indirizzi associati con queste righe. Alcuni linguaggi viene consentita istruzioni che si estendono su più righe o le righe che contiene più di un'istruzione. Questo metodo fornisce un flag per limitare gli indirizzi di debug per una singola istruzione.

 È possibile che una singola istruzione per disporre di più indirizzi di debug, come nel caso di modelli.

## <a name="see-also"></a>Vedere anche
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)