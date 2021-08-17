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
ms.openlocfilehash: a83574d5b36853a62206152cea74dd0a3d85f9a9f8c771e1769afd724b87ad36
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121391888"
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
 Questa funzione cerca le inline solo all'interno delle funzioni stub dell'acceleratore. Ignora i record di routine C++ nativi.

## <a name="see-also"></a>Vedi anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
