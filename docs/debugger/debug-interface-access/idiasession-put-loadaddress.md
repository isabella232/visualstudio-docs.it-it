---
description: Imposta l'indirizzo di caricamento per il file eseguibile che corrisponde ai simboli in questo archivio simboli.
title: IDiaSession::put_loadAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: cd5e8e6e4343584280f9031920f2f126f8526b9e2aba1d622185452b718430a5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121391808"
---
# <a name="idiasessionput_loadaddress"></a>IDiaSession::put_loadAddress
Imposta l'indirizzo di caricamento per il file eseguibile che corrisponde ai simboli in questo archivio simboli.

## <a name="syntax"></a>Sintassi

```C++
HRESULT put_loadAddress ( 
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>Parametri
 `NewVal`

[in] Indirizzo di caricamento per il file eseguibile.

## <a name="remarks"></a>Commenti
 Le proprietà dell'indirizzo virtuale dei simboli vengono calcolate usando il valore di questo metodo. Gli indirizzi virtuali non vengono calcolati a meno che questa proprietà non sia impostata su un valore diverso da zero.

> [!NOTE]
> È necessario chiamare questo metodo quando si ottiene [l'oggetto IDiaSession](../../debugger/debug-interface-access/idiasession.md) e prima di iniziare a usare l'oggetto se è necessario usare le proprietà virtuali sui simboli.

## <a name="see-also"></a>Vedi anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
