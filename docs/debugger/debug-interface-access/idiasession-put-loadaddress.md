---
description: Imposta l'indirizzo di caricamento per il file eseguibile che corrisponde ai simboli nell'archivio simboli.
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
ms.workload:
- multiple
ms.openlocfilehash: 05dc21a67a88270c4d3bce46387e46ed5a8e8497
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157000"
---
# <a name="idiasessionput_loadaddress"></a>IDiaSession::put_loadAddress
Imposta l'indirizzo di caricamento per il file eseguibile che corrisponde ai simboli nell'archivio simboli.

## <a name="syntax"></a>Sintassi

```C++
HRESULT put_loadAddress ( 
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>Parametri
 `NewVal`

in Indirizzo di caricamento per il file eseguibile.

## <a name="remarks"></a>Commenti
 Le proprietà dell'indirizzo virtuale del simbolo (VA) vengono calcolate usando il valore di questo metodo. Gli indirizzi virtuali non vengono calcolati se questa proprietà non è impostata su un valore diverso da zero.

> [!NOTE]
> È necessario chiamare questo metodo quando si ottiene l'oggetto [IDiaSession](../../debugger/debug-interface-access/idiasession.md) e prima di iniziare a usare l'oggetto se è necessario usare qualsiasi proprietà virtuale nei simboli.

## <a name="see-also"></a>Vedi anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
