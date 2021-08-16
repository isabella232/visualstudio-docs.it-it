---
description: Recupera un tipo di simbolo specificato che contiene o è più vicino a un indirizzo virtuale relativo e a un offset specificati.
title: IDiaSession::findSymbolByRVAEx | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByRVAEx method
ms.assetid: 61344966-fed4-4c02-9e27-20356ec2ef7c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 829886c196e9d727250e9e1f7773c5cb93008cdc059799bfaa6c3feff0fa8784
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121380150"
---
# <a name="idiasessionfindsymbolbyrvaex"></a>IDiaSession::findSymbolByRVAEx
Recupera un tipo di simbolo specificato che contiene o è più vicino a un indirizzo virtuale relativo e a un offset specificati.

## <a name="syntax"></a>Sintassi

```C++
HRESULT findSymbolByRVAEx ( 
   DWORD        rva,
   SymTagEnum   symtag,
   IDiaSymbol** ppSymbol,
   LONG*        displacement
);
```

#### <a name="parameters"></a>Parametri
 `rva`

[in] Specifica l'RVA.

 `symtag`

[in] Tipo di simbolo da trovare. I valori vengono presi [dall'enumerazione SymTagEnum.](../../debugger/debug-interface-access/symtagenum.md)

 `ppSymbol`

[out] Restituisce un [oggetto IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) che rappresenta il simbolo recuperato.

 `displacement`

[out] Restituisce un valore che specifica un offset dall'indirizzo virtuale relativo specificato in `rva` .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="example"></a>Esempio

```C++
IDiaSymbol* pFunc;
LONG disp = 0;
pSession->findSymbolByRVAEx( rva, SymTagFunction, &pFunc, &disp );
```

## <a name="see-also"></a>Vedere anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
