---
title: IDiaSession::findInlineesByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9860336d-f703-4ecb-bfc4-3f5beb175a76
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cdb35b9c61ddf347ee85553f69536d3757138ebe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85465706"
---
# <a name="idiasessionfindinlineesbyname"></a>IDiaSession::findInlineesByName
Recupera un'enumerazione che consente a un client di scorrere le informazioni sul numero di riga di tutte le funzioni inline che corrispondono a un nome specificato.

## <a name="syntax"></a>Sintassi

```C++
HRESULT findInlineesByName ( 
   LPCOLESTR             name,
   DWORD                 option,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametri
 `name`

in Specifica il nome da utilizzare per il confronto.

 `option`

in Specifica le opzioni di confronto applicate alla ricerca dei nomi. I valori dell'enumerazione [NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) possono essere usati singolarmente o in combinazione.

 `ppResult`

out Restituisce un oggetto [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) che contiene un elenco dei numeri di riga recuperati.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedere anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)