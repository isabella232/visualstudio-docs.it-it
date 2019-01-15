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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9218c36f550c61484054d180ecb4dccb1ca53f3d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947504"
---
# <a name="debug-hook-function-writing"></a>Scrittura di funzioni hook di debug
In questa sezione vengono descritte alcune funzioni hook di debug personalizzate che consentono di inserire il codice in alcuni punti predefiniti nell'ambito della normale elaborazione del debugger.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Funzioni hook del blocco client](../debugger/client-block-hook-functions.md)  
 Viene fornito materiale sussidiario e un prototipo per la scrittura di funzioni che convalidano o inseriscono nei report il contenuto dei dati archiviati nei blocchi _CLIENT_BLOCK.  
  
 [Funzioni hook di allocazione](../debugger/allocation-hook-functions.md)  
 Viene definita una funzione hook di allocazione, ne vengono esaminati i diversi utilizzi, vengono indicate le restrizioni e viene fornito un prototipo.  
  
 [Hook di allocazione e allocazioni di memoria CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)  
 Viene descritta la restrizione sulle funzioni hook di allocazione per ignorare in modo esplicito i blocchi `_CRT_BLOCK` se vengono effettuate chiamate alle funzioni della libreria di runtime del linguaggio C che allocano la memoria interna. In questo argomento vengono anche elencate le conseguenze nel caso in cui l'hook di allocazione non ignori i blocchi `_CRT_BLOCK` (con esempi) e la modifica della funzione predefinita di hook di allocazione, **CrtDefaultAllocHook**.  
  
 [Funzioni hook per la creazione di report](../debugger/report-hook-functions.md)  
 Viene discussa la funzione `_CrtSetReportHook`, che è possibile utilizzare per filtrare i report in modo da concentrarsi su tipi specifici di allocazioni. In questo argomento viene fornito anche un prototipo.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Tecniche di debug CRT](../debugger/crt-debugging-techniques.md)  
 È possibile collegarsi alle tecniche di debug per la libreria di runtime del linguaggio C, tra cui: utilizzo della libreria di debug CRT, macro per la creazione di report, differenze tra `malloc` e `_malloc_dbg`, scrittura di funzioni hook di debug e heap di debug CRT.