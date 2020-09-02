---
title: Impostazione delle opzioni generali della sessione di prestazioni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.general
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 698905f5e924bd8ddd424207a508ceaa4562ec57
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544469"
---
# <a name="set-general-performance-session-options"></a>Impostare le opzioni generali della sessione di prestazioni

È possibile impostare il metodo di raccolta e le convenzioni di denominazione per i dati di profilatura per una sessione di prestazioni degli strumenti di profilatura di Visual Studio nella pagina **Generale** della finestra di dialogo delle proprietà per la sessione di prestazioni. Per aprire questa finestra di dialogo da **Esplora prestazioni**, fare clic con il pulsante destro del mouse sulla sessione di prestazioni e quindi scegliere **Proprietà**.

## <a name="choosing-data-collection-methods"></a>Scelta del metodo di raccolta dati

Per impostare il metodo di raccolta di base, è necessario selezionare una delle opzioni in **Raccolta dati per profilatura**. Le opzioni sono descritte nella tabella seguente:

|Opzione|Articolo|
|-|-|
|**Campionamento**. Il metodo di campionamento raccoglie informazioni di profilatura a intervalli regolari. Questo metodo è utile per individuare problemi relativi all'uso del processore e rappresenta il metodo consigliato nella maggior parte dei casi per iniziare l'analisi delle prestazioni.|- [Raccolta delle statistiche sulle prestazioni tramite il campionamento](../profiling/collecting-performance-statistics-by-using-sampling.md)|
|**Strumentazione**. Il metodo di strumentazione inserisce in una copia di un modulo di profilatura codice che registra ogni ingresso, uscita e chiamata di funzione delle funzioni nel modulo durante un'esecuzione della profilatura. Questo metodo è utile per raccogliere informazioni dettagliate sui tempi per una sezione del codice e per comprendere l'impatto delle operazioni di input e output sulle prestazioni dell'applicazione.|- [Raccolta di dati di intervallo dettagliati tramite la strumentazione](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)|
|**Concorrenza**. Il metodo di concorrenza raccoglie i dati per ogni evento che blocca l'esecuzione del codice, ad esempio quando un thread attende che l'accesso bloccato a una risorsa dell'applicazione venga liberato. Questo metodo è utile per l'analisi di applicazioni multithread.|- [Raccolta di dati di concorrenza di thread e processi](../profiling/collecting-thread-and-process-concurrency-data.md)|

 È possibile raccogliere dati di memoria .NET usando i metodi di campionamento o strumentazione. Il tipo di dati viene selezionato in **Profilatura della memoria .NET**.

|Opzione|Articolo|
|-|-|
|**Raccogliere le informazioni sull'allocazione dell'oggetto .NET**. Per impostazione predefinita, i dati includono il numero e le dimensioni degli oggetti allocati. Selezionare o deselezionare questa casella di controllo per abilitare o disabilitare la raccolta di dati di memoria .NET. |- [Raccolta di dati di durata e allocazione di memoria .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)|
|**Raccogliere anche le informazioni sulla durata dell'oggetto .NET**. Selezionare questa casella di controllo per includere i dati sulle generazioni di Garbage Collection usate per recuperare gli oggetti di memoria.|- [Raccolta di dati di durata e allocazione di memoria .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) |

 Una pagina della sessione di profilatura viene visualizzata quando si comincia a profilare un'applicazione, dove è possibile sospendere, riprendere e interrompere la profilatura.

 ![Pagina della sessione di profilatura](../profiling/media/prof_profilingsessionpage.png "PROF_ProfilingSessionPage")

## <a name="set-profiling-data-file-options"></a>Impostare le opzioni dei file di dati di profilatura

|Opzione|Articolo|
|-|-|
|**Report**. Per impostazione predefinita, al file dei dati di profilatura (con estensione vsp) viene assegnato il nome dell'applicazione sottoposta a profilatura e il file viene posizionato nella cartella della soluzione o del progetto. Al nome viene aggiunta anche una stringa di data e viene anche aggiunto un numero incrementale ai file di dati che in caso contrario avrebbero nomi duplicati. Queste opzioni possono essere modificate.|- [Procedura: impostare le opzioni relative ai nomi file dei dati sulle prestazioni](../profiling/how-to-set-performance-data-file-name-options.md)|
