---
description: Recupera tutti gli elementi figlio di un identificatore padre specificato che corrispondono al nome e al tipo di simbolo.
title: IDiaSession::findChildren | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 13a1bcf4a4d5fed816ef467cdc15c5c6fb974f18
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122139147"
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
Recupera tutti gli elementi figlio di un identificatore padre specificato che corrispondono al nome e al tipo di simbolo.

## <a name="syntax"></a>Sintassi

```C++
HRESULT findChildren ( 
   IDiaSymbol*       parent,
   SymTagEnum        symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametri
 `parent`

[in] Oggetto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) che rappresenta l'elemento padre. Se questo simbolo padre è una funzione, un modulo o un blocco, i relativi elementi figlio lessicali vengono restituiti in `ppResult` . Se il simbolo padre è un tipo , vengono restituiti i relativi elementi figlio della classe. Se questo parametro è `NULL` , deve essere impostato su o , che restituisce `symtag` `SymTagExe` `SymTagNull` l'ambito globale (.exe file).

 `symtag`

[in] Specifica il tag dei simboli degli elementi figlio da recuperare. I valori vengono prelevati [dall'enumerazione SymTagEnum.](../../debugger/debug-interface-access/symtagenum.md) Impostare su `SymTagNull` per recuperare tutti gli elementi figlio.

 `name`

[in] Specifica il nome degli elementi figlio da recuperare. Impostare su `NULL` per recuperare tutti gli elementi figlio.

 `compareFlags`

[in] Specifica le opzioni di confronto applicate alla corrispondenza dei nomi. I valori [dell'enumerazione NameSearchOptions Enumeration](../../debugger/debug-interface-access/namesearchoptions.md) possono essere usati da soli o in combinazione.

 `ppResult`

[out] Restituisce un [oggetto IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) che contiene l'elenco di simboli figlio recuperati.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato come trovare le variabili locali della funzione `pFunc` che corrispondono al nome `szVarName` .

```C++
IDiaEnumSymbols* pEnum;
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );
```

## <a name="see-also"></a>Vedi anche
- [Overview](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)
- [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
