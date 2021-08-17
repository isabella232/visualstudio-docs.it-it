---
description: Recupera i numeri di riga all'interno degli identificatori di file di origine e di compilazione specificati.
title: IDiaSession::findLines | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLines method
ms.assetid: d6e84916-fd55-457e-b057-57f97b51fe73
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 23ff9b4ef926b276e3e397b3589ce89a93457872
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122044254"
---
# <a name="idiasessionfindlines"></a>IDiaSession::findLines
Recupera i numeri di riga all'interno degli identificatori di file di origine e di compilazione specificati.

## <a name="syntax"></a>Sintassi

```C++
HRESULT findLines ( 
   IDiaSymbol*           compiland,
   IDiaSourceFile*       file,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametri
 `compiland`

[in] Oggetto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) che rappresenta il compilando. Usare questa interfaccia come contesto in cui cercare i numeri di riga.

 `file`

[in] Oggetto [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) che rappresenta il file di origine in cui cercare i numeri di riga.

 `ppResult`

[out] Restituisce un [oggetto IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) che contiene un elenco dei numeri di riga recuperati.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
