---
title: Scrittura di funzioni hook di debug | Microsoft Docs
description: Informazioni su una serie di funzioni hook di debug personalizzate che è possibile scrivere per inserire il codice in punti predefiniti all'interno della normale elaborazione del debugger.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: fb99734182a2a5c218cdabaff6f219d3918245c6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122059021"
---
# <a name="debug-hook-function-writing"></a>Scrittura di funzioni hook di debug
In questa sezione vengono descritte alcune funzioni hook di debug personalizzate che consentono di inserire il codice in alcuni punti predefiniti nell'ambito della normale elaborazione del debugger.

## <a name="in-this-section"></a>Contenuto della sezione
 [Funzioni hook a blocchi client](../debugger/client-block-hook-functions.md) Fornisce indicazioni e un prototipo per la scrittura di funzioni che convalidano o segnalano il contenuto dei dati archiviati in _CLIENT_BLOCK blocchi.

 [Funzioni hook di allocazione](../debugger/allocation-hook-functions.md) Definisce una funzione hook di allocazione, ne esplora i diversi usi, indica le restrizioni e fornisce un prototipo.

 [Hook di allocazione e allocazioni di memoria CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md) Descrive la restrizione sulle funzioni hook di allocazione di ignorare in modo esplicito i blocchi se eseguono chiamate alle funzioni della libreria di runtime C che `_CRT_BLOCK` allocano memoria interna. In questo argomento vengono anche elencate le conseguenze nel caso in cui l'hook di allocazione non ignori i blocchi `_CRT_BLOCK` (con esempi) e la modifica della funzione predefinita di hook di allocazione, **CrtDefaultAllocHook**.

 [Funzioni hook di report](../debugger/report-hook-functions.md) Viene illustrato `_CrtSetReportHook` , che è possibile usare per filtrare i report in modo da concentrarsi su tipi specifici di allocazioni. In questo argomento viene fornito anche un prototipo.

## <a name="related-sections"></a>Sezioni correlate

- Tecniche di debug [CRT:](../debugger/crt-debugging-techniques.md) collegamenti alle tecniche di debug per la libreria C Run-Time, tra cui l'uso della libreria di debug CRT, le macro per la creazione di report, le differenze tra e , la scrittura di funzioni hook di debug e l'heap di `malloc` `_malloc_dbg` debug CRT.