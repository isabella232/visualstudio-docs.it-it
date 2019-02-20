---
title: NameSearchOptions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8fa637a5f403a4651541d920c6390204ee579994
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2019
ms.locfileid: "56318615"
---
# <a name="namesearchoptions"></a>NameSearchOptions
Specifica le opzioni di ricerca per i nomi dei simboli e file.

## <a name="syntax"></a>Sintassi

```C++
enum NameSearchOptions {
    nsNone,
    nsfCaseSensitive     = 0x1,
    nsfCaseInsensitive   = 0x2,
    nsfFNameExt          = 0x4,
    nsfRegularExpression = 0x8,
    nsfUndecoratedName   = 0x10,

// For backward compatibility:
    nsCaseSensitive           = nsfCaseSensitive,
    nsCaseInsensitive         = nsfCaseInsensitive,
    nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,
    nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,
    nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive
};
```

## <a name="elements"></a>Elementi
`nsNone`  
Non è stata specificata alcuna opzione.

`nsfCaseSensitive`  
Si applica una corrispondenza tra maiuscole e minuscole del nome.

`nsfCaseInsensitive`  
Si applica una corrispondenza tra maiuscole e minuscole del nome.

`nsfFNameExt`  
I nomi vengono considerati percorsi e si applica una corrispondenza di nome nomefile. ext.

`nsfRegularExpression`  
Si applica una corrispondenza tra nomi distinzione maiuscole/minuscole con un asterisco (*) e punti interrogativi (?) come caratteri jolly.

`nsfUndecoratedName`  
Si applica solo ai simboli che hanno entrambe non decorati e i nomi decorati.

## <a name="remarks"></a>Osservazioni
I valori di questa enumerazione vengono passati ai metodi seguenti:

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

## <a name="requirements"></a>Requisiti
Intestazione: dia2.h

## <a name="see-also"></a>Vedere anche
[Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)  
[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
[IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
