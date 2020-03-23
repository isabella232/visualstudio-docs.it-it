---
title: Analizzare le attività degli utenti virtuali per i test di carico
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- virtual user activity chart, viewing
ms.assetid: 8bda19b3-91c1-4daf-b6c7-09108bddadff
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c997f27e65a8e3992239fac78d52b0b4f19670c3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "78169404"
---
# <a name="how-to-analyze-what-virtual-users-are-doing-during-a-load-test-using-the-virtual-user-activity-chart"></a>Procedura: Analizzare le attività degli utenti virtuali durante un test di carico usando il grafico attività utente virtuale

Visualizzare l'attività utente virtuale associata al test di carico usando il **Grafico attività utente virtuale**. Ogni riga del grafico rappresenta un singolo utente virtuale. Il **Grafico attività utente virtuale** mostra esattamente l'attività eseguita da ogni utente virtuale durante il test. È possibile visualizzare modelli dell'attività utente, modelli di carico, test non riusciti o lenti correlati e richieste con altre attività utente virtuale. Il **Grafico attività utente virtuale** è disponibile solo al termine dell'esecuzione del test di carico.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Nelle procedure descritte di seguito viene illustrato come visualizzare il **Grafico attività utente virtuale**, come esaminare un'attività utente specifica e come usare il filtro.

## <a name="to-view-the-virtual-user-activity-chart-in-your-load-test-results"></a>Per visualizzare il Grafico attività utente virtuale nei risultati del test di carico

1. Per visualizzare i dati utente virtuale, è necessario prima configurare l'impostazione **Tutti i singoli dettagli** per la proprietà **Intervallo archiviazione dettagli** associata al test di carico. Eseguire quindi il test di carico.

2. Dopo l'esecuzione del test di carico, verrà visualizzata la pagina di riepilogo dei risultati del test. Scegliere il pulsante **Vai a dettagli utente** nella barra degli strumenti.

     -oppure-

     Aprire la visualizzazione Grafici scegliendo il pulsante **Grafici** nella barra degli strumenti. Fare clic con il pulsante destro del mouse su un grafico e scegliere **Vai a dettagli utente**.

     Se si usa questa opzione, al **Grafico attività utente virtuale** verrà applicato lo zoom automatico in modo da visualizzare la parte del test su cui è stato fatto clic con il pulsante destro del mouse. Se, ad esempio, il puntatore si trova approssimativamente sul contrassegno relativo ai 30 secondi, la visualizzazione dettagli verrà visualizzata approssimativamente in corrispondenza del contrassegno relativo ai 30 secondi nello strumento **Zoom periodo di tempo** nella parte inferiore del **Grafico attività utente virtuale**.

     È quindi possibile analizzare i dettagli di un'attività utente specifica nel **Grafico attività utente virtuale**.

## <a name="to-investigate-a-specific-users-activity-in-the-virtual-user-activity-chart"></a>Per analizzare un'attività utente specifica nel Grafico attività utente virtuale

1. Usare lo strumento Zoom periodo di tempo nella parte inferiore del **Grafico attività utente virtuale** per selezionare un'area del grafico in cui si desidera analizzare i dettagli per un utente specifico.

2. Passare con il puntatore su un dettaglio nel grafico. Si noti che le informazioni seguenti vengono visualizzate nella descrizione comando:

   - **ID utente**

   - **Scenario**

   - **Test**

   - **URL** (non visualizzato in un test o in una transazione)

   - **Risultato**

   - **Browser** (non visualizzato in un test o in una transazione)

   - **Rete**

   - **Ora di inizio**

   - **Durata**

   - **Agente**

   - **Log test** (collegamento al log test)

     > [!NOTE]
     > Per facilitare il debug dell'applicazione, se si sceglie il collegamento **Log test** viene visualizzato il risultato del test Web o dello unit test associato al log.

     È quindi possibile usare le operazioni di filtro ed evidenziazione disponibili nel **Grafico attività utente virtuale**.

## <a name="to-use-filtering-options-in-the-virtual-user-activity-chart"></a>Per utilizzare le opzioni di filtro nel Grafico attività utente virtuale

1. Nella **Legenda dettagli**utilizzare l'elenco a discesa per selezionare **Test**, **Pagina**o **Transazione**.

    **Pannello Legenda dettagli**

    ![Riquadro della legenda dei dettagli](../test/media/ltest_detailslegend.png)

2. Selezionare o deselezionare le caselle di controllo relative a pagine ASPX, errori, log, test e ricerca associati al test di carico.

    Il **Grafico attività utente virtuale** verrà aggiornato di conseguenza.

    Il **Grafico attività utente virtuale** consente di filtrare test, pagine e transazioni in base ad alcuni criteri diversi. È ad esempio possibile rimuovere determinati test dalla visualizzazione, rimuovere tutti i test superati o rimuovere i test non superati a causa di errori specifici. È anche possibile rimuovere tutti i test che non dispongono di un log.

    Ad esempio, è possibile selezionare l'opzione **(Evidenzia errori)** per visualizzare tutti gli errori nel grafico in colore rosso. È anche possibile selezionare l'opzione **(Evidenzia risultati con log)** per visualizzare tutti i risultati del test nel grafico che dispongono di log in colore verde.

    **Pannello dei risultati del filtro**

    ![Riquadro dei risultati del filtro](../test/media/ltest_filterresults.png)

3. Nei **risultati del filtro** selezionare o deselezionare le caselle di controllo per le opzioni di filtro seguenti:

   - **Mostra solo risultati con log** Vengono visualizzati solo i risultati dei test a cui è associato un log.

   - **Mostra risultati corretti** Vengono visualizzati solo i risultati dei test superati.

   - **Mostra risultati con errori** Vengono visualizzati i risultati in cui sono presenti errori, che possono risultare utili per l'esecuzione del debug.

     > [!NOTE]
     > L'elenco dei tipi di errore elencati nel nodo **Mostra risultati con errori** può essere ulteriormente analizzato scegliendo il pulsante **Tabelle** nella barra degli strumenti **del Visualizzatore risultati test prestazioni Web.** Per ulteriori informazioni, vedere [Analizzare i risultati e gli errori](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)dei test di carico nella visualizzazione Tabelle .

     Il **Grafico attività utente virtuale** verrà aggiornato di conseguenza.

## <a name="see-also"></a>Vedere anche

- [Analisi dell'attività utente virtuale nella visualizzazione Dettagli](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Procedura dettagliata: utilizzo dell'area attività utente virtuale per isolare i problemiWalkthrough: Using the virtual user activity chart to isolate issues](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)