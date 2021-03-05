---
description: Dato un valore di tag corrispondente, questo metodo restituisce un'enumerazione di simboli contenuti in una funzione stub dell'acceleratore padre specificata in corrispondenza di un indirizzo virtuale relativo specificato.
title: IDiaSession::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 50545be4b99c273b7019931463883efacbb683fb
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157063"
---
# <a name="idiasessionfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
Dato un valore di tag corrispondente, questo metodo restituisce un'enumerazione di simboli contenuti in una funzione stub dell'acceleratore padre specificata in corrispondenza di un indirizzo virtuale relativo specificato.

## <a name="syntax"></a>Sintassi

```C++
HRESULT findSymbolsByRVAForAcceleratorPointerTag ( 
   IDiaSymbol*           parent,
   DWORD                 tagValue,
   DWORD                 rva,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>Parametri
 `parent`

in Oggetto `IDiaSymbol` che corrisponde alla funzione dello stub dell'acceleratore in cui eseguire la ricerca.

 `tagValue`

in Valore del tag del puntatore.

 `rva`

in Indirizzo virtuale relativo.

 `ppResult`

out Puntatore a un `IDiaEnumSymbols` puntatore a interfaccia inizializzato con il risultato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Chiamare questo metodo solo su un' `IDiaSymbol` interfaccia che corrisponde a una funzione dello stub di tasti di scelta rapida.

## <a name="see-also"></a>Vedi anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
