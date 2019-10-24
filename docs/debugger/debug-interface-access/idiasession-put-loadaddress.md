---
title: IDiaSession::put_loadAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39db3bc0e0107e734f5de3f6902a2ca0fcc55bb0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741895"
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

## <a name="remarks"></a>Note
 Le proprietà dell'indirizzo virtuale del simbolo (VA) vengono calcolate usando il valore di questo metodo. Gli indirizzi virtuali non vengono calcolati se questa proprietà non è impostata su un valore diverso da zero.

> [!NOTE]
> È necessario chiamare questo metodo quando si ottiene l'oggetto [IDiaSession](../../debugger/debug-interface-access/idiasession.md) e prima di iniziare a usare l'oggetto se è necessario usare qualsiasi proprietà virtuale nei simboli.

## <a name="see-also"></a>Vedere anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)