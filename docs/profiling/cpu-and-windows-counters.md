---
title: Contatori CPU e Windows | Microsoft Docs
description: I contatori CPU (hardware) Windows (software) forniscono dati sulle prestazioni. Informazioni su come visualizzarli e come raccogliere dati da essi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.counters
helpviewer_keywords:
- Windows counters in Profiling Tools
- CPU counters in Profiling Tools
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 675061b7a094364122535d429a6835b43a666924011c2b6fea4203514a2222fa
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121355614"
---
# <a name="cpu-and-windows-counters"></a>Contatori CPU e Windows

Il profiler di Visual Studio consente di raccogliere dati sulle prestazioni generati dal sistema operativo (contatori Windows) e dati sulle prestazioni generati dal processore (contatori CPU).

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="windows-counters"></a>Contatori Windows

I contatori Windows fanno parte dell'infrastruttura diagnostica di Windows che offre informazioni sulle prestazioni del sistema operativo o di un'applicazione, servizio o driver. I contatori Windows dipendono dalla configurazione del computer in uso e potrebbero non essere disponibili in altri computer. I contatori di prestazioni di Windows vengono raccolti nel file di dati di profilatura come contrassegni e possono quindi essere usati per filtrare visualizzazioni e report.

## <a name="cpu-counters"></a>Contatori CPU

I contatori CPU sono una funzionalità della CPU del computer che archivia il numero di eventi correlati all'hardware. Quando si raccolgono i dati dei contatori CPU tramite il metodo di profilatura della strumentazione, i dati vengono aggiunti ai dati per le funzioni e i moduli. È possibile raccogliere più contatori CPU tramite il metodo di strumentazione. Quando si usa il metodo di campionamento, si seleziona un contatore da usare come evento da campionare.

I contatori di prestazioni sono specifici della CPU. Diversi modelli e versioni di una CPU possono avere impostazioni di configurazione sensibilmente diverse per l'abilitazione dello stesso contatore di prestazioni. Gli eventi portabili del profiler di [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] separano alcuni contatori di prestazioni comuni da processori specifici e consentono di raccogliere o campionare eventi di prestazioni generiche.

Se si vuole contare un particolare evento quando si usa il profiler, ad esempio, le richieste non soddisfatte nella cache L2, è possibile creare una sessione prestazioni relativa al mittente dell'evento. Questa operazione è possibile in qualsiasi CPU con una cache L2. La sessione prestazioni può essere spostata da una piattaforma all'altra senza alcuna modifica.

Il profiler di Visual Studio continua a supportare eventi specifici per una determinata piattaforma. Ad esempio, uno sviluppatore su una piattaforma Pentium 4 potrebbe voler contare gli eventi che sono specifici dell'architettura NetBurst. Questo evento non è portabile, ma è disponibile per gli sviluppatori per una sessione prestazioni specifica su una particolare piattaforma.

## <a name="portable-and-platform-events"></a>Eventi portabili e piattaforma

Gli eventi portabili costituiscono un gruppo di contatori della CPU che non sono specifici di un processore specifico. Tutti gli altri contatori CPU vengono chiamati eventi piattaforma e potrebbero non essere supportati su varie piattaforme.

 I contatori per gli eventi portabili e piattaforma sono definiti in file con estensione *xml* in cui vengono specificati valori specifici correlati ai contatori. Sono presenti più file per le diverse CPU poiché i dati per le CPU Intel e AMD, ad esempio, sono diversi. Il profiler di [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] usa queste informazioni per presentare all'utente i contatori appropriati, sia portabili che piattaforma, per la misurazione delle prestazioni.

### <a name="portable-events"></a>Eventi portabili

Gli eventi portabili contengono i seguenti eventi:

**Eventi generali**

|Nome evento|Descrizione evento|
|----------------|-----------------------|
|Istruzioni ritirate|Indica il numero di istruzioni eseguite fino al completamento dell'evento.|
|Cicli non interrotti|Indica solo i cicli in cui il processore non è stato arrestato, ad esempio in attesa per I/O.|

**Eventi front-end**

|Nome evento|Descrizione evento|
|----------------|-----------------------|
|Mancati riscontri ITLB|Indica il numero di mancati riscontri nel buffer ITLB (Instruction Translation Lookaside Buffer).|

**Eventi di diramazione**

|Nome evento|Descrizione evento|
|----------------|-----------------------|
|Rami ritirati|Indica il numero di istruzioni di diramazione eseguite fino al completamento dell'evento.|
|Rami stimati in modo errato|Indica i rami stimati in modo errato in seguito alla previsione errata di un percorso da parte del processore. I rami stimati in modo errato influiscono sulle prestazioni perché il processore deve ignorare tutte le operazioni eseguite e ripartire da un percorso corretto.|

**Eventi di memoria:**

|Nome evento|Descrizione evento|
|----------------|-----------------------|
|Richieste non soddisfatte lettura cache L2|Indica il numero di richieste non soddisfatte di lettura cache di secondo livello.|
|Riferimenti lettura cache L2|Indica il numero di riferimenti di lettura nella cache di secondo livello. Include le richieste non soddisfatte di caricamento e le richieste soddisfatte e non soddisfate di lettura per titolarità (RFO).|

## <a name="view-available-counters"></a>Visualizzare i contatori disponibili

È possibile elencare i contatori di CPU disponibili nell'IDE di Visual Studio in una finestra del prompt dei comandi.

### <a name="visual-studio-ui"></a>Interfaccia utente di Visual Studio

Per elencare i contatori disponibili in un computer nell'IDE di Visual Studio, è necessario che una sessione di prestazioni del profiler sia aperta in Esplora prestazioni.

#### <a name="to-view-a-list-of-a-list-of-all-cpu-counters-that-are-supported-on-the-current-platform"></a>Per visualizzare un elenco di tutti i contatori CPU supportati sulla piattaforma corrente

1. In Esplora prestazioni fare clic con il pulsante destro del mouse sulla sessione di prestazioni e quindi **scegliere Proprietà.**

2. Eseguire una delle operazioni seguenti:

   - Fare clic su **Campionamento** e quindi selezionare **Contatore di prestazioni** dall'elenco eventi **Esempio**. I contatori CPU sono elencati in **Contatori di prestazioni disponibili**.

      **Nota** Fare clic su **Annulla** per tornare alla configurazione di campionamento precedente.

     -oppure-

   - Selezionare **Contatori CPU** e quindi **Raccogli contatori CPU**. I contatori CPU sono elencati in **Contatori disponibili**.

      **Nota** Fare **clic su** Annulla per tornare alla configurazione precedente dell'insieme di contatori.

#### <a name="to-view-a-list-of-a-list-of-window-counters-that-are-supported-on-the-current-platform"></a>Per visualizzare un elenco di tutti i contatori Windows supportati sulla piattaforma corrente

1. In Esplora prestazioni fare clic con il pulsante destro del mouse sulla sessione di prestazioni e quindi **scegliere Proprietà.**

2. Fare clic su **Contatori Windows**.

3. Selezionare **Raccogliere contatori Windows**.

4. Selezionare un gruppo di contatori dall'elenco **Categoria contatori**. Il contatore di Windows per il gruppo viene visualizzato nella casella di riepilogo.

     **Nota** Fare clic su **Annulla** per tornare alla configurazione di raccolta contatori precedente.

### <a name="command-line"></a>Riga di comando

Con lo strumento da riga di comando [VSPerfCmd](../profiling/vsperfcmd.md) è possibile elencare i contatori CPU disponibili in un computer dalla riga di comando.

#### <a name="to-list-of-cpu-counters-that-are-supported-on-the-current-platform"></a>Per visualizzare un elenco di tutti i contatori CPU supportati sulla piattaforma corrente

1. Aprire una finestra del prompt dei comandi.

2. Tipo

     **\<Visual Studio Performance Tools Directory>\VSPerfCmd /querycounters**

     dove *\<Visual Studio Performance Tools Directory>* è il percorso della directory degli strumenti per le prestazioni dell'Visual Studio installazione. Per ottenere il percorso degli strumenti per le prestazioni, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

## <a name="see-also"></a>Vedi anche

- [Cenni preliminari](../profiling/overviews-performance-tools.md)
- [Procedura: Scegliere gli eventi di campionamento](../profiling/how-to-choose-sampling-events.md)
- [Procedura: Raccogliere i dati dei contatori CPU](../profiling/how-to-collect-cpu-counter-data.md)
- [Procedura: Raccogliere i dati dei contatori Windows](../profiling/how-to-collect-windows-counter-data.md)
