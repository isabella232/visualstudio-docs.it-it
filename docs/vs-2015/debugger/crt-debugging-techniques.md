---
title: Tecniche di debug CRT | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- c.runtime.debugging
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [CRT]
- CRT, debugging
- debugging [C++], CRT debug support
ms.assetid: 9be561f6-14a8-44ff-925d-d911d5b8e6ff
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a69defe75b80ef1f395931017dfc942398ca2710
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68161488"
---
# <a name="crt-debugging-techniques"></a>Tecniche di debug CRT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se si effettua il debug di un programma che utilizza la libreria di runtime del linguaggio C, possono essere utili le seguenti tecniche di debug.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Uso della libreria di debug CRT](../debugger/crt-debug-library-use.md)  
 Viene descritto il supporto per il debug fornito dalla libreria di runtime del linguaggio C e vengono fornite le istruzioni per accedere agli strumenti.  
  
 [Macro per la creazione di report](../debugger/macros-for-reporting.md)  
 Vengono fornite informazioni sulle macro **_RPTn** e **_RPTFn**, definite in CRTDBG.H, che sostituiscono l'utilizzo di istruzioni `printf` per il debug.  
  
 [Versioni di debug di funzioni di allocazione heap](../debugger/debug-versions-of-heap-allocation-functions.md)  
 Vengono descritte le speciali versioni di debug delle funzioni di allocazione heap, ad esempio: i vantaggi delle chiamate in modo esplicito, come CRT mappa le chiamate, come evitare la conversione, registrazione dei tipi separati di allocazioni nei blocchi client e i risultati della mancata definizione di _DEBUG.  
  
 [Informazioni dettagliate sull'heap di debug CRT](../debugger/crt-debug-heap-details.md)  
 Vengono forniti collegamenti a gestione della memoria e heap di debug, tipi di blocchi sull'heap di debug, utilizzo dell'heap di debug, funzioni per la creazione di report sullo stato dell'heap e registrazione delle richieste di allocazione dell'heap.  
  
 [Scrittura di funzioni hook di debug](../debugger/debug-hook-function-writing.md)  
 Vengono elencati i collegamenti a funzioni hook di blocchi client, funzioni hook di allocazione, hook di allocazione, allocazioni di memoria CRT e funzioni hook per la creazione di report.  
  
 [Individuazione di perdite di memoria tramite la libreria CRT](../debugger/finding-memory-leaks-using-the-crt-library.md)  
 Vengono illustrate le tecniche per rilevare e isolare le perdite di memoria utilizzando il debugger e la libreria di runtime del linguaggio C.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Debug del codice nativo](../debugger/debugging-native-code.md)  
 Vengono descritti alcuni problemi di debug comuni nonché alcune tecniche per applicazioni C e C++.  
  
 [Sicurezza del debugger](../debugger/debugger-security.md)  
 Vengono fornite indicazioni utili per un debug sicuro.
