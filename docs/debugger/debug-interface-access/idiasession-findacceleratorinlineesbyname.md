---
description: Restituisce un'enumerazione di simboli per i frame inline corrispondenti al nome della funzione inline specificato.
title: IDiaSession::findAcceleratorInlineesByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 813be3beb3514e716a025086efdd579344686f2e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629268"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
Restituisce un'enumerazione di simboli per i frame inline corrispondenti al nome della funzione inline specificato.

## <a name="syntax"></a>Sintassi

```C++
HRESULT findAcceleratorInlineeLinesByName ( 
   LPCOLESTR             name,
   DWORD                 option,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>Parametri
 `name`

[in] Nome della funzione inline in cui eseguire la ricerca.

 `option`

[in] Opzioni di ricerca dei nomi da utilizzare durante la ricerca di frame inline che corrispondono a `name` . Per altre informazioni, vedere [Enumerazione NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md).

 `ppResult`

[out] Puntatore a un `IDiaEnumSymbols` puntatore a interfaccia inizializzato con il risultato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questa funzione cerca inline solo all'interno di funzioni stub dell'acceleratore. Ignora i record di routine C++ nativi.

## <a name="see-also"></a>Vedi anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
