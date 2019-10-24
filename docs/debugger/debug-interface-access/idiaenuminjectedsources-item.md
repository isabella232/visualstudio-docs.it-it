---
title: 'IDiaEnumInjectedSources:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Item method
ms.assetid: 14846955-7270-451d-91d2-9cb34bb65187
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91be2f4f437cfeed30b0741d10bf719ba0ed2b71
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744509"
---
# <a name="idiaenuminjectedsourcesitem"></a>IDiaEnumInjectedSources::Item
Recupera un'origine inserita per mezzo di un indice.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Item ( 
   DWORD                index,
   IDiaInjectedSource** injectedSource
);
```

#### <a name="parameters"></a>Parametri
 indice

in Indice dell'oggetto [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) da recuperare. L'indice è compreso tra 0 e `count`-1, dove `count` viene restituito dal metodo [IDiaEnumInjectedSources:: get_Count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md) .

 injectedSource

out Restituisce un oggetto [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) che rappresenta l'origine inserita.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)