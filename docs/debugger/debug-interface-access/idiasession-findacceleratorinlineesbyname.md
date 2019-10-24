---
title: IDiaSession::findAcceleratorInlineesByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 007477d3f0de3767b0c5ef0af977f969505884ed
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742307"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
Restituisce un'enumerazione di simboli per i frame inline che corrispondono al nome della funzione inline specificata.

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

in Nome della funzione inline in cui eseguire la ricerca.

 `option`

in Opzioni di ricerca del nome da utilizzare per la ricerca di frame inline che corrispondono a `name`. Per ulteriori informazioni, vedere [enumerazione NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md).

 `ppResult`

out Puntatore a un puntatore a interfaccia `IDiaEnumSymbols` inizializzato con il risultato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Questa funzione Cerca le inline solo nelle funzioni dello stub dell'acceleratore. Ignora i record delle C++ procedure native.

## <a name="see-also"></a>Vedere anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)