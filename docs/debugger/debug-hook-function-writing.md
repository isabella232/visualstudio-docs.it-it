---
title: Scrittura di funzioni Hook di debug | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vc.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], CRT debug support
- debug hook functions
- hooks, debug
- hooks
- debugging [CRT], debug hook functions
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82145d39adc519bfd1324cc36805cea7b97b1664
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62563373"
---
# <a name="debug-hook-function-writing"></a>Scrittura di funzioni hook di debug
In questa sezione vengono descritte alcune funzioni hook di debug personalizzate che consentono di inserire il codice in alcuni punti predefiniti nell'ambito della normale elaborazione del debugger.

## <a name="in-this-section"></a>In questa sezione
 [Funzioni Hook del blocco client](../debugger/client-block-hook-functions.md) fornisce materiale sussidiario e un prototipo per la scrittura di funzioni che convalidano o inseriscono nei report il contenuto dei dati memorizzati in blocchi CLIENT_BLOCK.

 [Funzioni Hook di allocazione](../debugger/allocation-hook-functions.md) definisce una funzione di hook di allocazione, esamina i diversi utilizzi, fa notare le restrizioni e viene fornito un prototipo.

 [Hook di allocazione e allocazioni di memoria CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md) viene descritta la restrizione sulle funzioni di hook di allocazione di ignorare in modo esplicito `_CRT_BLOCK` blocca se vengono effettuate chiamate alle funzioni della libreria di runtime C che allocano memoria interna. In questo argomento vengono anche elencate le conseguenze nel caso in cui l'hook di allocazione non ignori i blocchi `_CRT_BLOCK` (con esempi) e la modifica della funzione predefinita di hook di allocazione, **CrtDefaultAllocHook**.

 [Funzioni Hook di report](../debugger/report-hook-functions.md) esamina `_CrtSetReportHook`, che è possibile usare per filtrare i report per concentrarsi su tipi specifici di allocazioni. In questo argomento viene fornito anche un prototipo.

## <a name="related-sections"></a>Sezioni correlate

- [Tecniche di debug CRT](../debugger/crt-debugging-techniques.md) -i collegamenti alle tecniche di debug per la libreria Run-Time di C, incluso l'uso della libreria di Debug CRT, macro per la creazione di report, le differenze tra `malloc` e `_malloc_dbg`, la scrittura di funzioni hook di debug e la libreria CRT eseguire il debug dell'heap.