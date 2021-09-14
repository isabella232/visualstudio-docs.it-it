---
description: Recupera un riferimento al simbolo per il compilatore che ha contribuito ai byte del testo dell'immagine.
title: IDiaLineNumber::get_compiland | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_compiland method
ms.assetid: c476d0b8-c473-47eb-96f5-c4e8f577b1c9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6dd3b1344f67e5a0e1513d0368197279a211531e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629699"
---
# <a name="idialinenumberget_compiland"></a>IDiaLineNumber::get_compiland
Recupera un riferimento al simbolo per il compilatore che ha contribuito ai byte del testo dell'immagine.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_compiland ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Parametri
 pRetVal

[out] Restituisce un [oggetto IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) per il compilatore che ha contribuito ai byte di testo dell'immagine.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
