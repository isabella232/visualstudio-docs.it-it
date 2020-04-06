---
title: IDebugSymbolProvider::GetAddressesFromContext . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7cf7599cf0fc37c16467c29c2b432f1f58b172fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719427"
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
Questo metodo esegue il mapping di un contesto di documento in una matrice di indirizzi di debug.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetAddressesFromContext( 
   IDebugDocumentContext2* pDocContext,
   BOOL                    fStatmentOnly,
   IEnumDebugAddresses**   ppEnumBegAddresses,
   IEnumDebugAddresses**   ppEnumEndAddresses
);
```

```csharp
int GetAddressesFromContext(
   IDebugDocumentContext2  pDocContext,
   bool                    fStatmentOnly,
   out IEnumDebugAddresses ppEnumBegAddresses,
   out IEnumDebugAddresses ppEnumEndAddresses
);
```

## <a name="parameters"></a>Parametri
`pDocContext`\
[in] Contesto del documento.

`fStatmentOnly`\
[in] Se TRUE, limita gli indirizzi di debug a una singola istruzione.

`ppEnumBegAddresses`\
[fuori] Restituisce un enumeratore per gli indirizzi di debug iniziali associati a questa istruzione o riga.

`ppEnumEndAddresses`\
[fuori] Restituisce un [enumeratore IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) per gli indirizzi di debug finali associati a questa istruzione o riga.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Un contesto di documento indica in genere un intervallo di righe di origine. Questo metodo fornisce gli indirizzi di debug iniziale e finale associati a queste righe. Alcuni linguaggi consentono istruzioni che si estendono su più righe o righe che contengono più di un'istruzione. Questo metodo fornisce un flag per limitare gli indirizzi di debug a una singola istruzione.

 È possibile che una singola istruzione abbia più indirizzi di debug, come nel caso dei modelli.

## <a name="see-also"></a>Vedere anche
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
