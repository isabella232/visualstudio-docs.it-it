---
title: IDiaEnumInjectedSources::get_Count | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::get_Count method
ms.assetid: 659c415b-9f7b-470d-90e2-b4c0087f8dd3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8da7e672ba447d1453d451da0040aef44ecaa799
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833521"
---
# <a name="idiaenuminjectedsourcesgetcount"></a>IDiaEnumInjectedSources::get_Count
Recupera il numero di origini inserite.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_Count ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 pRetVal

[out] Restituisce il numero di origini inserite.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)