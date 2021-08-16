---
description: Recupera un tipo di simbolo specificato che contiene o è più vicino a un indirizzo virtuale specificato.
title: IDiaSession::findSymbolByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByVA method
ms.assetid: 0350df23-9a5d-4e8d-8c26-7f571d8fb1af
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 14764b3836509957a4f35d42b404f6842734acf8b59dfbde8544ede7e44cfff1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121380164"
---
# <a name="idiasessionfindsymbolbyva"></a>IDiaSession::findSymbolByVA
Recupera un tipo di simbolo specificato che contiene o è più vicino a un indirizzo virtuale specificato.

## <a name="syntax"></a>Sintassi

```C++
HRESULT findSymbolByVA ( 
   ULONGLONG    va,
   SymTagEnum   symtag,
   IDiaSymbol** ppSymbol
);
```

#### <a name="parameters"></a>Parametri
 `va`

[in] Specifica l'indirizzo virtuale.

 `symtag`

[in] Tipo di simbolo da trovare. I valori vengono presi [dall'enumerazione SymTagEnum.](../../debugger/debug-interface-access/symtagenum.md)

 `ppSymbol`

[out] Restituisce un [oggetto IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) che rappresenta il simbolo recuperato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="example"></a>Esempio

```C++
IDiaSymbol* pFunc;
pSession->findSymbolByVA( va, SymTagFunction, &pFunc );
```

## <a name="see-also"></a>Vedere anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
