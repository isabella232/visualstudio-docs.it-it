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
ms.openlocfilehash: 01d004491feedff26c350cd7d40c544bc6b6de0f
ms.sourcegitcommit: 208395bc122f8d3dae3f5e5960c42981cc368310
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "64783745"
---
# <a name="idiasessionputloadaddress"></a>IDiaSession::put_loadAddress
Imposta l'indirizzo di caricamento del file eseguibile che corrisponde ai simboli in questo archivio dei simboli.

## <a name="syntax"></a>Sintassi

```C++
HRESULT put_loadAddress ( 
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>Parametri
 `NewVal`

[in] Carica l'indirizzo del file eseguibile.

## <a name="remarks"></a>Note
 Proprietà dei simboli indirizzo virtuale (valutazione della vulnerabilità) vengono calcolate utilizzando il valore di questo metodo. Gli indirizzi virtuali non vengono calcolati solo se questa proprietà è impostata su diverso da zero.

> [!NOTE]
> È necessario chiamare questo metodo quando si riceve la [IDiaSession](../../debugger/debug-interface-access/idiasession.md) dell'oggetto e prima di iniziare a utilizzare l'oggetto se è necessario usare qualsiasi proprietà virtuali sui simboli.

## <a name="see-also"></a>Vedere anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)