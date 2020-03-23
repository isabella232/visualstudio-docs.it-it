---
title: Analisi dell'attività utente virtuale del test di carico
ms.date: 10/03/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.activitychart
helpviewer_keywords:
- virtual user activity chart
- load test, virtual user activity chart
ms.assetid: 63f4bd42-3cfb-4eee-af68-e8334976539e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0289ff0d4a20eacc4f6801d9300d39df594bc79e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591235"
---
# <a name="analyzing-load-test-virtual-user-activity-in-the-details-view-of-the-load-test-analyzer"></a>Analisi dell'attività utente virtuale del test di carico nella visualizzazione Dettagli dell'Analizzatore test di carico

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Grafico attività utente virtuale**

![Grafico attività utente virtuale](../test/media/virtual_actchart.png)

La visualizzazione **Dettagli** consente di visualizzare il **Grafico attività utente virtuale**, usato per analizzare visivamente le attività eseguite dai singoli utenti virtuali durante il test di carico. Il **Grafico attività utente virtuale** consente di visualizzare modelli dell'attività utente, modelli di carico, test non riusciti o lenti correlati e richieste con altra attività utente virtuale. Il **Grafico attività utente virtuale** consente anche di determinare i picchi di utilizzo della CPU, le cadute di richieste al secondo e i test o le pagine in esecuzione durante tali picchi o cadute.

> [!NOTE]
> Prima di eseguire il test di carico per il quale si desidera utilizzare il **grafico dettagli attività utente virtuale**, è necessario verificare che la proprietà **Intervallo archiviazione dettagli** sia impostata sull'opzione **AllIndividualDetails** utilizzando l'Editor test prestazioni di carico.

**Riquadro Legenda dettagli**

![Riquadro della legenda dei dettagli](../test/media/ltest_detailslegend.png)

Il riquadro Legenda dettagli è visibile nel **Grafico attività utente virtuale**. Il riquadro Legenda dettagli consente di filtrare test, pagine e transazioni in base a diversi criteri. È ad esempio possibile rimuovere determinati test dalla visualizzazione, rimuovere tutti i test superati o rimuovere i test non superati a causa di errori specifici. È anche possibile rimuovere tutti i test che non dispongono di un log.

È possibile evidenziare i test non superati, in modo che vengano visualizzati in rosso. È inoltre possibile evidenziare i test che dispongono di log. Tali test verranno visualizzati in verde.

**Riquadro Risultati filtro**

![Riquadro dei risultati del filtro](../test/media/ltest_filterresults.png)

Il riquadro Risultati filtro è visibile nel **Grafico attività utente virtuale**. Il pannello Risultati filtro può essere usato per filtrare in base ai seguenti criteri:

- **Mostra solo risultati con log** Vengono visualizzati solo i risultati dei test a cui è associato un log.

- **Mostra risultati corretti** Vengono visualizzati solo i risultati dei test superati.

- **Mostra risultati con errori** Vengono visualizzati i risultati in cui sono presenti errori che possono risultare utili per l'esecuzione del debug.

## <a name="tasks"></a>Attività

|Attività|Argomenti correlati|
|-|-|
|**Eseguire il test** di carico: Dopo aver creato un test di carico e averlo configurato per abilitare la raccolta dei dati dell'attività utente virtuale, è necessario eseguire il test fino al completamento per visualizzare il **Grafico attività utente virtuale.**||
|Visualizzare i risultati del test di **carico che contengono i dati dell'attività utente virtuale:View the load test results that contain the virtual user activity data:** Dopo che il test di carico è stato creato, configurato e completato l'esecuzione, è possibile visualizzare i dati dell'attività utente virtuale utilizzando il **Grafico attività utente virtuale.**|-   [Analizzare i risultati dei test di caricoAnalyze load test results](../test/analyze-load-test-results-using-the-load-test-analyzer.md)<br />-   [Procedura: analizzare le operazioni eseguite dagli utenti virtuali durante un test di caricoHow to: Analyze what virtual users are doing during a load test](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**Isolare i problemi di prestazioni nei test di carico:Isolate performance issues in load tests:** È possibile utilizzare il **Grafico attività utente virtuale** per isolare i problemi di prestazioni nel test di carico.|-   [Procedura dettagliata: utilizzo dell'area attività utente virtuale per isolare i problemiWalkthrough: Using the virtual user activity chart to isolate issues](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>Vedere anche

- [Analizzare i risultati dei test di caricoAnalyze load test results](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analizzare i risultati e gli errori dei test di carico nella visualizzazione Tabelle](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
