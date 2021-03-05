---
description: Dato un valore di tag corrispondente, questo metodo restituisce un'enumerazione di simboli contenuti in questa funzione stub in corrispondenza di un indirizzo virtuale relativo specificato.
title: 'IDiaSymbol:: findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 05d468eca9d924fc9c87ed48e01ddee7aa9d3894
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156622"
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

out Puntatore a un `IDiaEnumSymbols` puntatore a interfaccia inizializzato con il risultato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

## <a name="remarks"></a>Commenti
 Chiamare questo metodo solo su un' `IDiaSymbol` interfaccia che corrisponde a una funzione dello stub di tasti di scelta rapida.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
