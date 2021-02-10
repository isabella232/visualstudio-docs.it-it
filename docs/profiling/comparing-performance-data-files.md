---
title: Confronto di file di dati sulle prestazioni | Microsoft Docs
description: Utilizzare Strumenti di profilatura per confrontare due file di report (con estensione vsp o vsps). Il confronto mostra le differenze, le regressioni delle prestazioni e i miglioramenti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, comparing profiling tools report files
- profiling tools reports, comparing
ms.assetid: e6fda144-f21d-4912-9d16-1b8d3555a210
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5dd59467292769608ea2eaea4a2520870906aaed
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941242"
---
# <a name="compare-performance-data-files"></a>Confrontare i file di dati delle prestazioni

Strumenti di profilatura funzionalità di confronto dei file di dati consente di selezionare due file di report (.*VSP* o. *vsps*) file e generazione di un report che mostra le differenze, le regressioni delle prestazioni e i miglioramenti apportati da una sessione di profilatura all'altra.

In un rapporto di confronto di file di dati degli strumenti per la profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vengono messi a confronto i risultati di un'analisi in un file di dati per la profilatura e i risultati di un'analisi di base in un altro file di dati. È necessario che i due file di dati siano stati generati usando lo stesso metodo di profilatura. Il report dei confronti analizzati viene salvato come. file *vsps* .

Nella visualizzazione del rapporto di confronto i dati modificati vengono visualizzati sotto forma di tabella. La tabella contiene il delta o la modifica rispetto al valore di base. Il delta viene calcolato determinando la differenza tra il valore precedente, il valore di base e il valore risultato dalla nuova analisi.

I confronti tra i dati del profiler possono essere basati su funzioni nel codice, moduli nell'applicazione, righe, puntatori all'istruzione (IP) e tipi.

I dati di profilatura disponibili per il confronto includono le informazioni visualizzate nelle colonne. Per le definizioni di questi nomi di colonna, vedere [visualizzazioni dei rapporti di prestazioni](../profiling/performance-report-views.md).

È possibile impostare una soglia per ridurre il rumore ed escludere qualsiasi dato nella visualizzazione tabella di confronto delle righe che non sono state modificate in base un valore specificato.

## <a name="in-this-section"></a>Contenuto della sezione

[Procedura: confrontare i file di dati delle prestazioni](../profiling/how-to-compare-performance-data-files.md)
