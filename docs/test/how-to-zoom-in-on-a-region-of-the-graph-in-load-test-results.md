---
title: Ingrandire i grafici dei risultati dei test di carico
description: Informazioni su come esaminare i dati generati durante l'esecuzione di un test di carico in modo più dettagliato usando le barre dello zoom per eseguire lo zoom avanti e scorrere fino a un'area del grafico.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.load.monitor.graphzoom
helpviewer_keywords:
- graphs, analyzing load tests
- load tests, zooming with graphs
ms.assetid: 729b4c30-4bc3-4698-91b3-17a676897443
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: ee81f279f82ee4803a5ac188b5d647769f8a148bb6e7a73328f6c36236d6318c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121366531"
---
# <a name="how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results"></a>Procedura: Eseguire lo zoom avanti su un'area del grafico nei risultati del test di carico

Al termine di un test di carico, è possibile utilizzare le barre dello zoom per eseguire lo zoom avanti e scorrere un'area del grafico. Lo zoom avanti consente di analizzare i dettagli anche minuti dei dati generati durante l'esecuzione di un test di carico.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Lo zoom avanti è disponibile solo quando si analizza il risultato di un test di carico completato e non mentre si osservano i risultati di un test in esecuzione.

Il controllo zoom è visibile nell'**Analizzatore test di carico** soltanto quando si visualizzano i risultati dei test di carico in modalità zoom. La modalità zoom viene attivata nella visualizzazione Grafici quando un test di carico è stato completato o al caricamento di un test eseguito in precedenza. È possibile visualizzare o nascondere i controlli zoom nei grafici usando l'opzione **Mostra controlli zoom** della barra degli strumenti.

Lo **zoom dell'asse x orizzontale** può essere regolato in modo da analizzare periodi specifici durante il test di carico. Lo **zoom dell'asse y verticale** può essere regolato in modo da analizzare intervalli di valori specifici per i contatori inclusi nel grafico.

È possibile regolare sia la **sequenza temporale orizzontale** sia i controlli zoom dell'**intervallo di valori verticali** usando il mouse. Il **controllo della sequenza temporale orizzontale** può essere regolato anche usando i tasti freccia SINISTRA e freccia DESTRA. Utilizzando i tasti freccia per regolare il controllo zoom, è possibile regolare l'intervallo delle finestre di 1 intervallo di campionamento per volta. L'uso combinato del tasto **MAIUSC** e dei tasti di direzione consente regolazioni in incrementi di 10 intervalli di campionamento.

Per regolare il controllo zoom tramite un tasto di direzione, impostare prima lo stato attivo sul controllo zoom usando il tasto **TAB**. Quando lo stato attivo si trova sul dispositivo di scorrimento sinistro, i tasti di direzione spostano il limite iniziale della finestra di zoom di 1 intervallo a sinistra o a destra. Quando lo stato attivo si trova sul dispositivo di scorrimento centrale, è possibile utilizzare i tasti di direzione per scorrere la finestra di zoom a sinistra o a destra di 1 intervallo di campionamento senza modificarne le dimensioni. Infine, il dispositivo di scorrimento destro viene spostato per estendere o ridurre l'intervallo della fine della finestra di zoom di 1 intervallo di campionamento.

Per riportare i controlli zoom allo stato che consente di visualizzare la cronologia e gli intervalli di valori per intero, è possibile usare le opzioni **Zoom indietro orizzontale**, **Zoom indietro verticale** o **Zoom indietro orizzontale e verticale** del menu a comparsa del grafico.

> [!TIP]
> È possibile usare l'opzione **Sincronizza controlli zoom orizzontali** nella barra degli strumenti per attivare o disattivare la sincronizzazione automatica dello zoom orizzontale. Quando la sincronizzazione è attiva, qualsiasi valore di zoom applicato a un grafico verrà applicato anche a tutti gli altri grafici nella visualizzazione Grafici.

![Controllo zoom della visualizzazione grafico](../test/media/ltest_zoomcontrol.png)

Nell'illustrazione precedente, il grafico **Sistema sotto test** è stato ingrandito al fine di esaminare problemi di soglia. Le violazioni di soglia sono state abilitate tramite l'opzione **Mostra violazioni di soglia su grafico** del menu a discesa **Opzioni grafico** presente nella barra degli strumenti.

Per altre informazioni, vedere [Analizzare i risultati dei test di carico nella visualizzazione Grafici](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="display-graphs"></a>Visualizzare i grafici

Prima di modificare la visualizzazione di un grafico mediante lo zoom avanti o indietro o scorrendo un'area del grafico, seguire questa procedura per visualizzare i grafici.

Per visualizzare i grafici:

1. Eseguire un test di carico finché non viene completato.

2. Al termine dell'esecuzione del test di carico, scegliere **Sì** nella finestra di dialogo in cui viene richiesto se visualizzare i risultati dall'archivio dei risultati del test di carico.

     \- - oppure -

     Visualizzare i dettagli di un test di carico eseguito precedentemente. Per altre informazioni, vedere [Procedura: Accedere ai risultati dei test di carico per l'analisi](../test/how-to-access-load-test-results-for-analysis.md).

3. Scegliere **Grafici** se i grafici non sono visualizzati.

4. Scegliere **Mostra controlli zoom** se le barre dello zoom non sono visualizzate.

     Per ogni grafico sono disponibili due barre dello zoom. La barra dello zoom che controlla la scala verticale si trova a sinistra del grafico, mentre la barra dello zoom che controlla la scala orizzontale si trova sotto il grafico.

     Ogni barra dello zoom dispone di due quadratini di ridimensionamento. Un quadratino di ridimensionamento è un'area rettangolare che si trova alle estremità della barra dello zoom.

## <a name="zoom-and-scroll"></a>Zoom e scorrimento

Quando si visualizzano più grafici, è possibile mantenerli sincronizzati in modo da visualizzare la stessa parte dell'esecuzione del test di carico.

### <a name="to-synchronize-zooming-and-scrolling"></a>Per sincronizzare lo zoom e lo scorrimento

1. Nell'Analizzatore **test di** carico scegliere Sincronizza controlli **zoom orizzontale**.

     Quando il pulsante **Sincronizza controlli zoom orizzontali** è selezionato, lo zoom e lo scorrimento della scala cronologica di un singolo grafico vengono applicati anche alla scala cronologica degli altri grafici.

2. Scegliere nuovamente **Sincronizza controlli zoom orizzontali**.

     Quando il pulsante **Sincronizza controlli zoom orizzontali non è selezionato**, lo zoom e lo scorrimento della scala cronologica di un singolo grafico hanno effetto solo su tale grafico.

### <a name="to-zoom-and-scroll-to-a-region-of-the-graph"></a>Per eseguire lo zoom e scorrere un'area del grafico

1. Sulla barra dello zoom sotto un grafico trascinare il quadratino di ridimensionamento di sinistra verso destra.

     Viene eseguito lo zoom avanti sull'ultima parte dell'esecuzione del test. In modo analogo, trascinando il quadratino di ridimensionamento di destra verso sinistra, viene eseguito lo zoom avanti sulla prima parte dell'esecuzione del test.

2. Per eseguire lo zoom avanti su una determinata area, trascinare entrambi i quadratini di ridimensionamento verso il centro di un grafico.

     Più vicini sono i quadratini di ridimensionamento, maggiore è lo zoom avanti per visualizzare segmenti piccolissimi del test di carico.

     Scegliere la sezione centrale della barra dello zoom e trascinarla per scorrere fino a un determinato punto del test di carico.

### <a name="to-zoom-to-a-region-of-the-graph-by-choosing-and-dragging"></a>Per eseguire lo zoom su un'area del grafico selezionandola e trascinandola

1. Selezionare un'estremità dell'area dello zoom di un grafico.

2. Trascinare il puntatore del mouse verso l'altra estremità dell'area dello zoom.

3. Rilasciare il pulsante del mouse.

    Viene ingrandita l'area che è stata selezionata e trascinata.

   Nella procedura descritta di seguito viene illustrato come eseguire rapidamente lo zoom indietro su un'area senza dovere regolare le estremità della barra dello zoom.

### <a name="to-zoom-out"></a>Per eseguire lo zoom indietro

1. Fare clic con il pulsante destro del mouse su un grafico in cui è stato applicato lo zoom avanti.

2. Dal menu di scelta rapida selezionare **Zoom indietro orizzontale**.

     Viene eseguito lo zoom indietro per mostrare l'intera durata dell'esecuzione del test di carico.

## <a name="see-also"></a>Vedi anche

- [Analizzare i risultati dei test di carico nella visualizzazione Grafici](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Analizzare i risultati dei test di carico](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Procedura: Aggiungere ed eliminare contatori nei grafici](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
