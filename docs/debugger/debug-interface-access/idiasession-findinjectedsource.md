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
ms.openlocfilehash: 4e7e6aeec300aaf8941fa0d3ac28ddce7ace8de4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122044310"
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
