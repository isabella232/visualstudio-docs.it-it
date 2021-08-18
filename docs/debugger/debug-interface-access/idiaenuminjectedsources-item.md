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
ms.openlocfilehash: 0b77564566d1f45ca860483867bc407de1e5040c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122134465"
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
