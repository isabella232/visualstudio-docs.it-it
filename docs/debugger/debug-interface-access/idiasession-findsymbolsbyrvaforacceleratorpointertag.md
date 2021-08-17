---
description: Dato un valore tag corrispondente, questo metodo restituisce un'enumerazione di simboli contenuti in una funzione stub dell'acceleratore padre specificata in un indirizzo virtuale relativo specificato.
title: IDiaSession::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 356b991ad945fc8c222f1cd5be0c701ef9689a0306da7dcf56e7cf259196e128
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121344812"
---
# <a name="idiasessionfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
Dato un valore tag corrispondente, questo metodo restituisce un'enumerazione di simboli contenuti in una funzione stub dell'acceleratore padre specificata in un indirizzo virtuale relativo specificato.

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

[in] Oggetto `IDiaSymbol` che corrisponde alla funzione stub dell'acceleratore in cui eseguire la ricerca.

 `tagValue`

[in] Valore del tag del puntatore.

 `rva`

[in] Indirizzo virtuale relativo.

 `ppResult`

[out] Puntatore a un `IDiaEnumSymbols` puntatore a interfaccia inizializzato con il risultato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Chiamare questo metodo solo su `IDiaSymbol` un'interfaccia che corrisponde a una funzione stub dell'acceleratore.

## <a name="see-also"></a>Vedi anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
