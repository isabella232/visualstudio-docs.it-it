---
title: Guida per principianti al campionamento CPU
description: Informazioni su Visual Studio strumenti di profilatura rivelano quanto tempo viene usato dalle funzioni nell'applicazione, guidando l'utente nelle aree per velocizzare l'applicazione.
ms.custom: SEO-VS-2020
ms.date: 02/27/2017
ms.topic: how-to
f1_keywords:
- vs.performance.wizard.intropage
helpviewer_keywords:
- Profiling Tools, quick start
- performance tools, wizard
- Performance Wizard
ms.assetid: 85161cc4-18ee-49b3-9487-33680e687597
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 78907673a1175542cb1384e3a0bfffa5639f4a9d5f455cdd50d57fab42693f87
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121369176"
---
# <a name="beginners-guide-to-cpu-sampling"></a>Guida per principianti al campionamento CPU
È possibile usare gli strumenti di profilatura di Visual Studio per analizzare i problemi di prestazioni nell'applicazione. Questa procedura illustra come usare i dati di **campionamento**.

> [!NOTE]
> Si consiglia di usare lo strumento [Utilizzo CPU](../profiling/beginners-guide-to-performance-profiling.md) nella finestra degli strumenti di diagnostica anziché lo strumento di campionamento CPU precedente, a meno che non siano necessarie funzionalità speciali, ad esempio il supporto della strumentazione.

 Il **campionamento** è un metodo di profilatura statistico che consente di sapere quali funzioni svolgono la maggior parte del lavoro in modalità utente nell'applicazione. Il campionamento è un buon punto di partenza per individuare aree velocizzare l'applicazione.

 A intervalli specificati, il metodo di **campionamento** raccoglie informazioni sulle funzioni in esecuzione nell'applicazione. Al termine di una profilatura, nella visualizzazione **Riepilogo** dei dati di profilatura appare l'albero delle chiamate delle funzioni più attive, detto **Percorso critico**, in cui è stata eseguita la maggior parte delle operazioni nell'applicazione. Inoltre, la visualizzazione sono elencate le funzioni che eseguivano più lavoro individuale e fornisce un grafico della sequenza temporale che è possibile utilizzare per concentrarsi su segmenti specifici della sessione di campionamento.

 Se dal **campionamento** non si ottengono i dati necessari, altri metodi di raccolta degli strumenti di profilatura offrono tipi diversi di informazioni che potrebbero essere utili. Per altre informazioni sugli altri metodi, vedere [Procedura: Scegliere un metodo di raccolta](../profiling/how-to-choose-collection-methods.md).

> [!TIP]
> Se si analizza il codice che chiama le funzioni di Windows, assicurarsi di avere i file con estensione *pdb* più aggiornati. Senza questi file, le visualizzazioni dei rapporti elencherà i nomi delle funzioni di Windows enigmatici e difficile da comprendere. Per altre informazioni su come verificare la disponibilità dei file necessari, vedere [Procedura: Fare riferimento alle informazioni sui simboli di Windows](../profiling/how-to-reference-windows-symbol-information.md).

## <a name="create-and-run-a-performance-session"></a>Creare e attivare una sessione di prestazioni
 Per ottenere i dati che si devono analizzare, è necessario innanzitutto creare una sessione di prestazioni e quindi eseguire la sessione. La **Creazione guidata sessione di prestazioni** consente di eseguire entrambe le operazioni.

 Se non si profila un'app desktop di Windows o un'app ASP.NET, è necessario usare uno degli altri strumenti di profilatura. Vedere [Presentazione degli strumenti di profilatura](../profiling/profiling-feature-tour.md).

#### <a name="to-create-and-run-a-performance-session"></a>Per creare e attivare una sessione di prestazioni

1. Aprire la soluzione in Visual Studio. Impostare la configurazione da rilasciare Individuare la casella **Configurazioni soluzione** sulla barra degli strumenti, che è impostata su **Debug** per impostazione predefinita. Impostarla su **Versione**.

    > [!IMPORTANT]
    > Se non si è un amministratore nel computer in uso, è necessario eseguire Visual Studio come amministratore quando si utilizza il profiler. Fare clic con il pulsante destro del mouse sull'icona dell'applicazione Visual Studio e quindi su **Esegui come amministratore**.

2. Dal menu **Debug** scegliere **Profiler** e quindi **Profiler prestazioni**.

3. Selezionare l'opzione **Creazione guidata sessione di prestazioni** e fare clic su **Avvia**.

4. Selezionare l'opzione **Campionamento CPU (consigliato)** e fare clic su **Fine**.

5. Avvio dell'applicazione e avvia il profiler raccogliere i dati.

6. Verificare la funzionalità che potrebbe contenere problemi di prestazioni.

7. Chiudere l'applicazione normalmente.

     Eseguita l'applicazione, la visualizzazione **Riepilogo** relativa ai dati di profilatura appare nella finestra principale di Visual Studio e viene visualizzata un'icona per la nuova sessione nella finestra **Esplora prestazioni**.

## <a name="step-2-analyze-sampling-data"></a>Passaggio 2: Analizzare i dati di campionamento
 Al termine dell'esecuzione di una sessione di prestazioni, la visualizzazione **Riepilogo** del rapporto sulla profilatura appare nella finestra principale di Visual Studio.

 È consigliabile iniziare ad analizzare i dati esaminando il **Percorso critico**, quindi l'elenco delle funzioni che svolgono la maggior parte del lavoro e infine concentrandosi sulle altre funzioni usando la **sequenza temporale di riepilogo**. È anche possibile visualizzare suggerimenti e avvisi relativi alla profilatura nella finestra **Elenco errori**.

 Tenere presente che il metodo di campionamento potrebbe non fornire le informazioni necessarie. Ad esempio, esempi vengono raccolti solo quando l'applicazione esegue codice in modalità utente. Di conseguenza, alcune funzionalità, come le operazioni di input e output, non vengono acquisite dal campionamento. Gli strumenti di profilatura fornisce diversi metodi di raccolta che consentono di concentrarsi sui dati importanti. Per altre informazioni sugli altri metodi, vedere [Procedura: Scegliere un metodo di raccolta](../profiling/how-to-choose-collection-methods.md).

 Ogni area numerata nella figura si riferisce a un passaggio della procedura.

 ![Visualizzazione del report di riepilogo per il campionamento](../profiling/media/summary_sampling.png "Summary_Sampling")

#### <a name="to-analyze-sampling-data"></a>Analizzare i dati di campionamento

1. Nella visualizzazione **Riepilogo** il **Percorso critico** indica il ramo dell'albero delle chiamate dell'applicazione con gli esempi più inclusivi. Si tratta del percorso di esecuzione che era più attivo quando sono stati raccolti dati. Valori inclusivi alti possono indicare che l'algoritmo che genera la struttura delle chiamate può essere ottimizzata. Trovare la funzione nel codice che è più basso nel percorso. Si noti che il percorso può inoltre includere funzioni di sistema o funzioni in moduli esterni.

     ![Percorso ricorrente del profiler](../profiling/media/profiler_hotpath.png "Profiler_HotPath")

    1. **Esempi inclusivi** indica quanto lavoro è stato svolto dalla funzione e dalle funzioni chiamate dalla funzione. I numeri inclusivi alti indicano le funzioni sono più dispendiose in generale.

    2. **Esempi esclusivi** indica la quantità di operazioni eseguite dal codice nel corpo della funzione, escluse quelle eseguite dalle funzioni chiamate dalla funzione. Numeri esclusivi alti possono indicare un collo di bottiglia delle prestazioni all'interno della funzione stessa.

2. Fare clic sul nome della funzione per visualizzare i **dettagli** dei dati di profilatura. La visualizzazione **Dettagli funzione** include una rappresentazione grafica dei dati di profilatura per la funzione selezionata, che indica tutte le funzioni che hanno chiamato tale funzione e tutte le funzioni chiamate dalla funzione selezionata.

    - La dimensione dei blocchi delle funzioni chiamanti e chiamate rappresenta la frequenza relativa che le funzioni chiamate o sono state chiamate.

    - Facendo clic sul nome di un chiamante o chiamata di funzione per effettuare la funzione di visualizzazione Dettagli funzione selezionata.

    - Nel riquadro inferiore della finestra **Dettagli funzione** è visualizzato il codice della funzione. Se si esamina il codice e un'opportunità per ottimizzare le prestazioni, fare clic sul nome del file di origine per aprire il file nell'editor di Visual Studio.

3. Per continuare l'analisi, tornare alla visualizzazione **Riepilogo** selezionando **Riepilogo** dall'elenco a discesa **Visualizza**. Esaminare quindi le funzioni in **Funzioni che svolgono più lavoro individuale**. Questo elenco vengono visualizzate le funzioni con i campioni esclusivi più alti. Il codice nel corpo della funzione di queste funzioni eseguite molto lavoro e potrebbe essere possibile ottimizzarlo. Per analizzare ulteriormente una particolare funzione, fare clic sul nome della funzione per visualizzarlo in **Dettagli funzione**.

     ![Elenco di funzioni che svolgono la maggior parte del lavoro](../profiling/media/functions_mostwork.png "Functions_MostWork")

     Per continuare l'analisi dell'esecuzione della profilatura, è possibile analizzare di nuovo un segmento di dati di profilatura usando la sequenza temporale nella visualizzazione **Riepilogo** per vedere il **Percorso critico** e le **Funzioni che svolgono più lavoro individuale** da un segmento selezionato. Ad esempio, con particolare attenzione ad un picco più piccolo nella sequenza temporale potrebbe rivelare costosi alberi delle chiamate e funzioni che non sono stati visualizzati durante l'analisi dell'intera esecuzione della profilatura.

     Per rianalyizzare un segmento, selezionare un segmento all'interno della casella Sequenza temporale di **riepilogo** e quindi fare clic su Filtra **per selezione.**

     ![Sequenza temporale della visualizzazione Riepilogo prestazioni](../profiling/media/performancesummary.png "PerformanceSummary")

4. Il profiler utilizza anche un set di regole per suggerire modi per migliorare l'esecuzione della profilatura e identificare eventuali problemi di prestazioni. Se viene rilevato un problema, verrà visualizzato un avviso nella finestra **Elenco errori**. Per aprire la finestra **Elenco errori**, scegliere **Elenco errori** nel menu **Visualizza**.

    - Per visualizzare la funzione che ha generato un avviso, in **Dettagli funzione** fare doppio clic sull'avviso.

    - Per visualizzare informazioni dettagliate sull'avviso, fare clic sull'errore con il pulsante destro del mouse e quindi scegliere **Mostra guida errore**

## <a name="step-3-revise-code-and-rerun-a-session"></a>Passaggio 3: Rivedere codice ed eseguire nuovamente una sessione
 Dopo aver individuato e ottimizzare una o più funzioni, è possibile ripetere l'esecuzione della profilatura e confrontare i dati per visualizzare la differenza che le modifiche apportate alle prestazioni dell'applicazione.

#### <a name="to-revise-code-and-rerun-the-profiler"></a>Per modificare il codice e rieseguire il profiler

1. Cambiare il codice

2. Per aprire **Esplora prestazioni**, nel menu **Debug** fare clic su **Profiler**, quindi su **Esplora prestazioni** e su **Mostra Esplora prestazioni**.

3. In **Esplora prestazioni** fare clic con il pulsante destro del mouse sulla sessione da rieseguire e quindi fare clic su **Avvio con analisi.**

4. Dopo che la sessione è stata rieseguita, viene aggiunto un altro file di dati alla cartella *Report* per la sessione in **Esplora prestazioni**. Selezionare i dati di profilatura, sia nuovi che originali, fare clic con il pulsante destro del mouse sulla selezione e quindi fare clic su **Confronta rapporto di prestazioni**.

     Verrà visualizzata una nuova finestra del report, visualizzare i risultati del confronto. Per altre informazioni sull'uso della visualizzazione di confronto, vedere [Procedura: Confrontare i file di dati delle prestazioni](../profiling/how-to-compare-performance-data-files.md).

## <a name="see-also"></a>Vedi anche
- [Esplora prestazioni](../profiling/performance-explorer.md)
- [Introduzione](../profiling/getting-started-with-performance-tools.md)
- [Cenni preliminari](../profiling/overviews-performance-tools.md)
- [Profilatura in Visual Studio](../profiling/index.yml)
- [Presentazione degli strumenti di profilatura](../profiling/profiling-feature-tour.md)
