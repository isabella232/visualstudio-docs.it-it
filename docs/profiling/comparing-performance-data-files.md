---
title: Confronto di file di dati sulle prestazioni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, comparing profiling tools report files
- profiling tools reports, comparing
ms.assetid: e6fda144-f21d-4912-9d16-1b8d3555a210
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e75a5da65343a08f0c94be27837e70f4078192d5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53893049"
---
# <a name="compare-performance-data-files"></a>Confrontare i file di dati delle prestazioni
La funzionalità di confronto tra file di dati offerta dagli strumenti di profilatura consente di selezionare due file di report con estensione *vsp* o *vsps* e generare un report in cui siano indicate le differenze, la regressione delle prestazioni e i miglioramenti registrati tra una sessione di profilatura e l'altra.  
  
 In un rapporto di confronto di file di dati degli strumenti per la profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vengono messi a confronto i risultati di un'analisi in un file di dati per la profilatura e i risultati di un'analisi di base in un altro file di dati. È necessario che i due file di dati siano stati generati usando lo stesso metodo di profilatura. Il report dei confronti analizzati viene salvato come file con estensione *vsps*.  
  
 Nella visualizzazione del rapporto di confronto i dati modificati vengono visualizzati sotto forma di tabella. La tabella contiene il delta o la modifica rispetto al valore di base. Il delta viene calcolato determinando la differenza tra il valore precedente, il valore di base e il valore risultato dalla nuova analisi.  
  
 I confronti tra i dati del profiler possono essere basati su funzioni nel codice, moduli nell'applicazione, righe, puntatori all'istruzione e tipi.  
  
 I dati di profilatura disponibili per il confronto includono le informazioni visualizzate nelle colonne. Per la definizione dei nomi di queste colonne, vedere [Visualizzazioni dei report di prestazioni](../profiling/performance-report-views.md).  
  
 È possibile impostare una soglia per ridurre il rumore ed escludere qualsiasi dato nella visualizzazione tabella di confronto delle righe che non sono state modificate in base un valore specificato.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Procedura: Confrontare i file di dati delle prestazioni](../profiling/how-to-compare-performance-data-files.md)