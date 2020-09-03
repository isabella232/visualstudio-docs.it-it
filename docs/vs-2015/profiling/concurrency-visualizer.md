---
title: Visualizzatore di concorrenza | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.viewnavigation
- vs.cv.overview
- vs.cv.performance.gettingstarted
- vs.cv.gettingstarted
helpviewer_keywords:
- Concurrency Visualizer, Concurrency Visualizer
ms.assetid: ae5879a0-1e1a-455a-ba72-148e57f59289
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e7061acabbe5ce18ff6e1f210fe0003bdaf88980
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "82586816"
---
# <a name="concurrency-visualizer"></a>Visualizzatore di concorrenze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
> Il Visualizzatore di concorrenza è un'estensione facoltativa di Visual Studio. Scaricare il Visualizzatore di concorrenza e gli strumenti di raccolta del visualizzatore di concorrenza dai collegamenti seguenti:  
> 
> - Scaricare l'estensione              [Visualizzatore di concorrenza](https://visualstudiogallery.msdn.microsoft.com/a6c24ce9-beec-4545-9261-293061436ee9) .  
>   - Scaricare gli              [strumenti di raccolta del Visualizzatore di concorrenza per Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=49103).  
> 
>   L’ [utilità della riga di comando per il visualizzatore di concorrenza (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md) consente di raccogliere tracce dalla riga di comando che possono essere visualizzate nel visualizzatore di concorrenza per Visual Studio 2015. Lo strumento può essere usato nei computer in cui non è installato Visual Studio.  
  
 Il Visualizzatore di concorrenza permette di esaminare l'esecuzione di app in multi-threading. Le visualizzazioni nel Visualizzatore di concorrenza forniscono dati grafici, tabulari e in formato testo che mostrano le relazioni temporali tra i thread nel programma e il sistema nel suo complesso. È possibile usare il Visualizzatore di concorrenza per individuare problemi relativi a colli di bottiglia delle prestazioni, sottoutilizzo della CPU, conflitto di thread, migrazione di thread, ritardi di sincronizzazione, aree di I/O sovrapposte e per ottenere altre informazioni. Nelle visualizzazioni sono disponibili dati su cui è possibile agire mediante il collegamento dell'output grafico agli stack di chiamate e al codice sorgente.  
  
 Il Visualizzatore di concorrenza si basa sulla funzionalità [Event Tracing for Windows](https://msdn.microsoft.com/library/bb968803(VS.85).aspx) .  
  
> [!NOTE]
> Il Visualizzatore di concorrenza non supporta progetti Web.  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Visualizzazione Uso](../profiling/utilization-view.md)|Descrive come visualizzare e analizzare l'attività del sistema attraverso tutti i processori.|  
|[Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)|Descrive come analizzare le interazioni tra thread nel programma.|  
|[Visualizzazione Core](../profiling/cores-view.md)|Descrive come analizzare la migrazione di thread tra componenti principali.|  
|[Modelli comuni per applicazioni multithreading con comportamento non corretto](../profiling/common-patterns-for-poorly-behaved-multithreaded-applications.md)|Descrive vari modelli comuni e ne illustra l'uso nel Visualizzatore di concorrenza.|  
|[Sviluppo parallelo nel blog di Visual Studio](https://docs.microsoft.com/archive/blogs/visualizeparallel/)|Fornisce suggerimenti e procedure consigliate per il Visualizzatore di concorrenza.|  
|[Visualizzazioni dei rapporti di prestazioni](../profiling/performance-report-views.md)|Fornisce informazioni di riferimento relative a report e visualizzazioni degli strumenti per la profilatura di Visual Studio.|  
|[SDK del visualizzatore di concorrenza](../profiling/concurrency-visualizer-sdk.md)|Spiega come eseguire la strumentazione del codice sorgente per visualizzare informazioni aggiuntive nel Visualizzatore di concorrenza.|  
|[Utilità della riga di comando del visualizzatore di concorrenza (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)|Spiega come usare l'utilità riga di comando del Visualizzatore di concorrenza (CVCollectionCmd.exe) per raccogliere ed elaborare le tracce sulle macchine che non hanno Visual Studio.|  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti di profilatura](../profiling/profiling-tools.md)
