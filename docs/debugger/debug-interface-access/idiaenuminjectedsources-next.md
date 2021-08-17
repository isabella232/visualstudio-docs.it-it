---
description: Recupera un numero specificato di origini inserite nella sequenza di enumerazione.
title: IDiaEnumInjectedSources::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Next method
ms.assetid: 38af80fc-748f-4b15-bff1-823db21dd4d0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ee8e2a2f7b595bdc3484af78542dcd7d45ce1244fee9ea588ba5c1e1cff11a61
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121455159"
---
# <a name="idiaenuminjectedsourcesnext"></a>IDiaEnumInjectedSources::Next
Recupera un numero specificato di origini inserite nella sequenza di enumerazione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Next ( 
   ULONG                celt,
   IDiaInjectedSource** rgelt,
   ULONG*               pceltFetched
);
```

#### <a name="parameters"></a>Parametri
 celt

[in] Numero di origini inserite nell'enumeratore da recuperare.

 Rgelt

[out] Restituisce una matrice di [oggetti IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) che rappresenta le origini inserite desiderate.

 pceltFetched

[out] Restituisce il numero di origini inserite nell'enumeratore recuperato.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se non sono presenti altre origini inserite. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
