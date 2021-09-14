---
title: Eseguire il debug delle versioni delle funzioni di allocazione heap | Microsoft Docs
description: Usare le versioni di debug delle funzioni di allocazione heap nella libreria di runtime C. Queste funzioni hanno gli stessi nomi delle versioni di versione con _dbg aggiunte.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- debugging [CRT], heap allocation functions
- debugging memory leaks, CRT debug library functions
- malloc function
- memory leaks, CRT debug library functions
- heap allocation, debug
- _malloc_dbg function
ms.assetid: 91748bdc-f4cd-4d8b-ab98-0493dab7ed0d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 47a704d69fb0a3487deaf14962a65d0b04fe00ad
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626519"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Versioni di debug di funzioni di allocazione heap
La libreria di runtime del linguaggio C contiene speciali versioni di debug delle funzioni di allocazione heap. Queste funzioni presentano lo stesso nome delle corrispondenti versioni di rilascio, con l'unica differenza del suffisso _dbg. Questo argomento illustra le differenze tra la versione di rilascio di una funzione CRT e la versione _dbg, utilizzando `malloc` e `_malloc_dbg` come esempi.

 Quando [_DEBUG](/cpp/c-runtime-library/debug) definito, CRT esegue il mapping di tutte le chiamate [malloc](/cpp/c-runtime-library/reference/malloc) [a _malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg). Pertanto non è necessario riscrivere il codice utilizzando `_malloc_dbg` anziché `malloc` per sfruttarne i vantaggi durante il debug.

 È tuttavia possibile chiamare `_malloc_dbg` esplicitamente. La chiamata esplicita di `_malloc_dbg` presenta alcuni vantaggi supplementari:

- Registrazione delle allocazioni del tipo `_CLIENT_BLOCK`.

- Memorizzazione del file sorgente e del numero di riga nel punto in cui ha avuto luogo la richiesta di allocazione.

  Se non si vogliono convertire le chiamate a , è possibile ottenere le informazioni sul file di origine definendo _CRTDBG_MAP_ALLOC , che fa sì che il `malloc` `_malloc_dbg` preprocessore [](/cpp/c-runtime-library/crtdbg-map-alloc)eserciti direttamente il mapping di tutte le chiamate a invece di basarsi su un wrapper intorno a `malloc` `_malloc_dbg` `malloc` .

  Per registrare i tipi separati di allocazioni in blocchi client, è necessario chiamare `_malloc_dbg` direttamente e impostare il parametro `blockType` su `_CLIENT_BLOCK`.

  Quando _DEBUG non è definito, le chiamate a non vengono disturbate, le chiamate a vengono risolte in , la definizione di _CRTDBG_MAP_ALLOC viene ignorata e le informazioni sul file di origine relative alla richiesta di allocazione non `malloc` `_malloc_dbg` vengono `malloc` fornite. [](/cpp/c-runtime-library/crtdbg-map-alloc) Dal momento che `malloc` non presenta alcun parametro di tipo di blocco, le richieste di tipi `_CLIENT_BLOCK` vengono gestite come allocazioni standard.

## <a name="see-also"></a>Vedi anche

- [Tecniche di debug CRT](../debugger/crt-debugging-techniques.md)