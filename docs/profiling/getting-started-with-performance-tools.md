---
title: Introduzione agli strumenti per le prestazioni | Microsoft Docs
description: Informazioni sulle diverse modalità offerte da Visual Studio per raccogliere, visualizzare e analizzare i dati relativi alle prestazioni del codice.
ms.custom: SEO-VS-2020
ms.date: 11/04/2018
ms.topic: conceptual
helpviewer_keywords:
- getting started, performance
- getting started, profiling tools
ms.assetid: 02085214-a8e4-40fd-9b26-32391a7a7082
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4f168c4c88ba12ff1f1c9bd0543e9d2b74ae095c
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801513"
---
# <a name="getting-started-with-performance-tools"></a>Introduzione agli strumenti per le prestazioni

Visual Studio include vari metodi per raccogliere, visualizzare e analizzare i dati sulle prestazioni del codice. In molti casi il modo migliore per iniziare a usare gli strumenti per le prestazioni è l'uso delle impostazioni predefinite della **Creazione guidata sessione di prestazioni**. La procedura guidata raccoglie le statistiche dell'app che possono indicare problemi di prestazioni nel codice.

- Gli avvisi di prestazioni che segnalano problemi di codifica comuni in Visual Studio vengono visualizzati nella finestra **Elenco errori**. È possibile passare dagli avvisi al codice sorgente e ad argomenti dettagliati della Guida che consentono di scrivere codice più efficiente.

- I report delle prestazioni offrono visualizzazioni a diversi livelli della struttura dell'applicazione, delle righe di codice sorgente e dei processi. I report delle prestazioni visualizzano dati di esecuzione dell'app, dalle funzioni chiamanti e chiamate all'albero delle chiamate dell'intera app.

Per profilare rapidamente un progetto, un'app o un sito Web ASP.NET, selezionare **debug**  >  **Performance Profiler** e selezionare **creazione guidata sessione di prestazioni**. Per istruzioni dettagliate, vedere [Guida per principianti alla profilatura delle prestazioni](../profiling/beginners-guide-to-cpu-sampling.md) e [Procedura: Raccogliere dati sulle prestazioni per un sito Web](../profiling/how-to-collect-performance-data-for-a-web-site.md).

Per specificare e configurare manualmente una sessione di profilatura delle prestazioni, selezionare **debug**  >  **Profiler**  >  **Esplora prestazioni**. Usare la cartella **Destinazioni** e le pagine **Proprietà** in **Esplora prestazioni** per configurare le sessioni. Per istruzioni, vedere [Procedura: Creare manualmente sessioni di prestazioni](../profiling/how-to-manually-create-performance-sessions.md).

**Vedere anche:**

- [Panoramiche (strumenti per le prestazioni)](../profiling/overviews-performance-tools.md)
- [Analisi dei dati degli strumenti per le prestazioni](../profiling/analyzing-performance-tools-data.md)
- [Uso di regole per le prestazioni per analizzare i dati](../profiling/using-performance-rules-to-analyze-data.md)
- [Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)
