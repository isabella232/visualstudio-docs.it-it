---
description: Recupera i file di origine tramite compilazione e nome.
title: IDiaSession::findFile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d1d8d9b32e850214d45703107dcdc5e22a1b9a8d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122074716"
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
Recupera i file di origine tramite compilazione e nome.

## <a name="syntax"></a>Sintassi

```C++
HRESULT findFile ( 
   IDiaSymbol*           pCompiland,
   LPCOLESTR             name,
   DWORD                 option,
   IDiaEnumSourceFiles** ppResult
);
```

#### <a name="parameters"></a>Parametri
 `pCompiland`

[in] Oggetto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) che rappresenta il compilando da usare come contesto per la ricerca. Impostare questo parametro su `NULL` per trovare i file di origine in tutti i compilandi.

 `name`

[in] Specifica il nome del file di origine da recuperare. Impostare questo parametro su `NULL` per recuperare tutti i file di origine.

 `option`

[in] Specifica le opzioni di confronto applicate alla ricerca dei nomi. I valori [dell'enumerazione NameSearchOptions Enumeration](../../debugger/debug-interface-access/namesearchoptions.md) possono essere usati da soli o in combinazione.

 `ppResult`

[out] Restituisce un [oggetto IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) che contiene un elenco dei file di origine recuperati.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="example"></a>Esempio

```C++
IDiaEnumSourceFiles* pEnum;
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );
```

## <a name="see-also"></a>Vedere anche
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)
