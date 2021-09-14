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
ms.openlocfilehash: 692ab9f7a1d792de504478349bd1fe58908485a5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629070"
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

[in] Caricare l'indirizzo per il file eseguibile.

## <a name="remarks"></a>Commenti
 Le proprietà degli indirizzi virtuali dei simboli vengono calcolate usando il valore di questo metodo. Gli indirizzi virtuali non vengono calcolati a meno che questa proprietà non sia impostata su un valore diverso da zero.

> [!NOTE]
> È necessario chiamare questo metodo quando si ottiene l'oggetto [IDiaSession](../../debugger/debug-interface-access/idiasession.md) e prima di iniziare a usare l'oggetto se è necessario usare proprietà virtuali sui simboli.

## <a name="see-also"></a>Vedi anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
