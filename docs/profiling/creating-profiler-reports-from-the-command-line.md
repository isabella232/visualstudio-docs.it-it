---
title: Creazione di rapporti del profiler tramite la riga di comando | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 475c8da2d10dea4953486fc9c564c5bde7fb0887
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/24/2020
ms.locfileid: "85329069"
---
# <a name="create-profiler-reports-from-the-command-line"></a>Creare report del profiler dalla riga di comando
Lo strumento da riga di comando **VSPerfReport** consente di creare report con estensione *xml* o *csv* (valori delimitati da virgole) da file di dati di profilatura con estensione *vsp*. I tipi di report VSPerfReport sono molto simili alle visualizzazioni basate su tabella dell'interfaccia di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. È possibile filtrare il report per visualizzare solo il codice o per visualizzare solo un segmento del file di dati di profilatura. Per altre informazioni, vedere [VSPerfReport](../profiling/vsperfreport.md).

 È anche possibile semplificare la condivisione dei file di dati di profilatura incorporando simboli nei file con estensione *vsp* o creando file di report preanalizzati (con estensione *vsps*), più piccoli e più rapidi da aprire.

## <a name="common-tasks"></a>Attività comuni

|Attività|Contenuto correlato|
|----------|---------------------|
|**Creazione di un report di base.** Creare tutti i tipi di report VSPerfReport o solo un sottoinsieme.|-   [Creare report di base](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|
|**Confrontare due file di dati di profilatura.** Creare un report "diff" che confronta i dati delle prestazioni in due file di dati di profilatura.|-   [Procedura: creare un report di confronto del profiler da un prompt dei comandi](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|
|**Visualizzare dati calltrace ed eventi ETW (Event Trace for Windows).** Creare un rapporto calltrace che elenca le informazioni di intervallo per ogni punto di ingresso e in uscita delle funzioni dell'applicazione e ogni chiamata ad altre funzioni da parte di una determinata funzione. In alternativa creare un elenco dettagliato di tutti gli eventi ETW registrati in un'esecuzione della profilatura.|-   [Procedura: creare un report di traccia delle chiamate](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|
|**Filtrare un report.** Limitare un report solo alle funzioni presenti nel codice dell'utente o solo a un intervallo del file di dati di profilatura.|-   [Procedura: filtrare i report dalla riga di comando](../profiling/how-to-filter-reports-from-the-command-line.md)|
|**Creare file di dati di profilatura portabili.** Per semplificare la condivisione dei dati di profilatura è possibile incorporare i simboli di una sessione di profilatura nel file con estensione *vsp*. È anche possibile creare un file di dati di profilatura preanalizzato (con estensione *vsps*), più piccolo e più rapido da aprire.|-   [Creare file di dati di profilatura portabili](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|
