---
title: Introduzione agli strumenti per le prestazioni | Microsoft Docs
description: Informazioni sui diversi modi in cui Visual Studio raccogliere, visualizzare e analizzare i dati sulle prestazioni del codice.
ms.custom: SEO-VS-2020
ms.date: 11/04/2018
ms.topic: conceptual
helpviewer_keywords:
- getting started, performance
- getting started, profiling tools
ms.assetid: 02085214-a8e4-40fd-9b26-32391a7a7082
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9c0aabc9292d4c904d36b00820935aadd1545057
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122131521"
---
# <a name="getting-started-with-performance-tools"></a>Introduzione agli strumenti per le prestazioni

Visual Studio include vari metodi per raccogliere, visualizzare e analizzare i dati sulle prestazioni del codice. In molti casi il modo migliore per iniziare a usare gli strumenti per le prestazioni è l'uso delle impostazioni predefinite della **Creazione guidata sessione di prestazioni**. La procedura guidata raccoglie le statistiche dell'app che possono indicare problemi di prestazioni nel codice.

- Gli avvisi di prestazioni che segnalano problemi di codifica comuni in Visual Studio vengono visualizzati nella finestra **Elenco errori**. È possibile passare dagli avvisi al codice sorgente e ad argomenti dettagliati della Guida che consentono di scrivere codice più efficiente.

- I report delle prestazioni offrono visualizzazioni a diversi livelli della struttura dell'applicazione, delle righe di codice sorgente e dei processi. I report delle prestazioni visualizzano dati di esecuzione dell'app, dalle funzioni chiamanti e chiamate all'albero delle chiamate dell'intera app.

Per profilare rapidamente un progetto, un'app o ASP.NET, selezionare **Debug**  >  **Profiler prestazioni** e selezionare **Creazione guidata sessione di prestazioni.** Per istruzioni dettagliate, vedere [Guida per principianti alla profilatura delle prestazioni](../profiling/beginners-guide-to-cpu-sampling.md) e [Procedura: Raccogliere dati sulle prestazioni per un sito Web](../profiling/how-to-collect-performance-data-for-a-web-site.md).

Per specificare e configurare manualmente una sessione di profilatura delle prestazioni, selezionare **Debug**  >  **Profiler**  >  **Esplora prestazioni**. Usare la cartella **Destinazioni** e le pagine **Proprietà** in **Esplora prestazioni** per configurare le sessioni. Per istruzioni, vedere [Procedura: Creare manualmente sessioni di prestazioni](../profiling/how-to-manually-create-performance-sessions.md).

**Vedere anche:**

- [Panoramiche (strumenti per le prestazioni)](../profiling/overviews-performance-tools.md)
- [Analisi dei dati degli strumenti per le prestazioni](../profiling/analyzing-performance-tools-data.md)
- [Uso di regole per le prestazioni per analizzare i dati](../profiling/using-performance-rules-to-analyze-data.md)
- [Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)
