---
description: Recupera un'origine inserita tramite un indice.
title: IDiaEnumInjectedSources::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Item method
ms.assetid: 14846955-7270-451d-91d2-9cb34bb65187
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d28eb5cc69d3cdeb8ca5da95b91d79ed9c5f46ec042d53fb0704f3b77f3ea5dc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121455199"
---
# <a name="idiaenuminjectedsourcesitem"></a>IDiaEnumInjectedSources::Item
Recupera un'origine inserita tramite un indice.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Item ( 
   DWORD                index,
   IDiaInjectedSource** injectedSource
);
```

#### <a name="parameters"></a>Parametri
 index

[in] Indice [dell'oggetto IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) da recuperare. L'indice è l'intervallo da 0 a -1, dove viene restituito dal metodo `count` `count` [IDiaEnumInjectedSources::get_Count.](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md)

 injectedSource

[out] Restituisce un [oggetto IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) che rappresenta l'origine inserita.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
