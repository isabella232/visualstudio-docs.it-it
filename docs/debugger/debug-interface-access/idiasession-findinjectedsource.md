---
description: Recupera un elenco di origini inserite nell'archivio dei simboli dai provider di attributi o da altri componenti del processo di compilazione.
title: IDiaSession::findInjectedSource | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findInjectedSource method
ms.assetid: 907531b6-1ef8-4153-986d-b72611a1632d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 3c26a677b826ec706934bb75024b5aa956a9709c8715b97afd1dc0a608c3c283
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121391840"
---
# <a name="idiasessionfindinjectedsource"></a>IDiaSession::findInjectedSource
Recupera un elenco di origini inserite nell'archivio dei simboli dai provider di attributi o da altri componenti del processo di compilazione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT findInjectedSource ( 
   LPCOLESTR                 srcFile,
   IDiaEnumInjectedSources** ppResult
);
```

#### <a name="parameters"></a>Parametri
 srcFile

[in] Nome del file di origine in cui eseguire la ricerca.

 ppResult

[out] Restituisce un [oggetto IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) che contiene un elenco di tutte le origini inserite.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
