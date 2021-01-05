---
title: Scrittura di funzioni hook di debug | Microsoft Docs
description: Leggere le informazioni su numerose funzioni hook di debug personalizzate che è possibile scrivere per consentire l'inserimento del codice in punti predefiniti all'interno dell'elaborazione normale del debugger.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5e2f05005d0b43d526936bfbc8018739cb1ed88
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728937"
---
# <a name="debug-hook-function-writing"></a>Scrittura di funzioni hook di debug
In questa sezione vengono descritte alcune funzioni hook di debug personalizzate che consentono di inserire il codice in alcuni punti predefiniti nell'ambito della normale elaborazione del debugger.

## <a name="in-this-section"></a>Contenuto della sezione
 [Funzioni hook del blocco client](../debugger/client-block-hook-functions.md) Vengono fornite istruzioni e un prototipo per la scrittura di funzioni che convalidano o segnalano il contenuto dei dati archiviati nei blocchi di _CLIENT_BLOCK.

 [Funzioni hook di allocazione](../debugger/allocation-hook-functions.md) Definisce una funzione hook di allocazione, ne esamina i diversi usi, rileva le restrizioni e fornisce un prototipo.

 [Hook di allocazione e allocazioni di memoria CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md) Descrive la restrizione sulle funzioni hook di allocazione di ignorando in modo esplicito i `_CRT_BLOCK` blocchi se effettuano chiamate alle funzioni della libreria di runtime C che allocano memoria interna. In questo argomento vengono anche elencate le conseguenze nel caso in cui l'hook di allocazione non ignori i blocchi `_CRT_BLOCK` (con esempi) e la modifica della funzione predefinita di hook di allocazione, **CrtDefaultAllocHook**.

 [Funzioni hook di report](../debugger/report-hook-functions.md) `_CrtSetReportHook`Viene illustrato, che è possibile utilizzare per filtrare i report in modo da concentrarsi su tipi specifici di allocazioni. In questo argomento viene fornito anche un prototipo.

## <a name="related-sections"></a>Sezioni correlate

- [Tecniche di debug CRT](../debugger/crt-debugging-techniques.md) : collegamenti alle tecniche di debug per la libreria di Run-Time C, tra cui l'uso della libreria di debug CRT, le macro per la creazione di report, le differenze tra `malloc` e `_malloc_dbg` , la scrittura di funzioni hook di debug e l'heap di debug CRT.