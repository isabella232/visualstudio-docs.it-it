---
title: 'IDiaSymbol:: findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f0d05946db816e6bd209e364e11d5091163941a4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741146"
---
# <a name="idiasymbolfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
Dato un valore di tag corrispondente, questo metodo restituisce un'enumerazione di simboli contenuti in questa funzione stub in corrispondenza di un indirizzo virtuale relativo specificato.

## <a name="syntax"></a>Sintassi

```C++
HRESULT findSymbolsByRVAForAcceleratorPointerTag (
   DWORD             tagValue,
   DWORD             rva,
   IDiaEnumSymbols** ppResult);
```

#### <a name="parameters"></a>Parametri
 `tagValue`

in Valore del tag del puntatore per il quale vengono trovati i record dei simboli puntati.

 `rva`

in RVA usato per filtrare i simboli che corrispondono alla variabile puntata con il valore del tag specificato.

 `ppResult`

out Puntatore a un puntatore a interfaccia `IDiaEnumSymbols` inizializzato con il risultato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

## <a name="remarks"></a>Note
 Chiamare questo metodo solo su un'interfaccia `IDiaSymbol` che corrisponde a una funzione dello stub dell'acceleratore.

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)