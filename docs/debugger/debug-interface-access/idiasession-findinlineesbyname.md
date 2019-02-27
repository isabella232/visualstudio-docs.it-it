---
title: IDiaSession::findInlineesByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 9860336d-f703-4ecb-bfc4-3f5beb175a76
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1cb665e3c0965a2e85c8d28202114c95928988d5
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628689"
---
# <a name="idiasessionfindinlineesbyname"></a>IDiaSession::findInlineesByName
Recupera un'enumerazione che consente a un client di eseguire l'iterazione attraverso le informazioni sul numeri di riga di tutte le funzioni rese inline che corrisponde al nome specificato.

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

[in] Specifica il nome da utilizzare per il confronto.

 `option`

[in] Specifica le opzioni di confronto applicate alla ricerca del nome. I valori di [enumerazione NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) enumerazione può essere utilizzata singolarmente o in combinazione.

 `ppResult`

[out] Restituisce un [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) oggetto che contiene un elenco di numeri di riga che sono stati recuperati.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)