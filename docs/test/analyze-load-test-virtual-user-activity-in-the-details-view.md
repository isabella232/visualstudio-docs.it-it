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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bba807eae2a7767b9b4271d0df48e962a2113285
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665367"
---
# <a name="analyzing-load-test-virtual-user-activity-in-the-details-view-of-the-load-test-analyzer"></a>Analisi dell'attività utente virtuale del test di carico nella visualizzazione Dettagli dell'Analizzatore test di carico

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Grafico attività utente virtuale**

![Grafico attività utente virtuale](../test/media/virtual_actchart.png)

La visualizzazione **Dettagli** consente di visualizzare il **Grafico attività utente virtuale**, usato per analizzare visivamente le attività eseguite dai singoli utenti virtuali durante il test di carico. Il **Grafico attività utente virtuale** consente di visualizzare modelli dell'attività utente, modelli di carico, test non riusciti o lenti correlati e richieste con altra attività utente virtuale. Il **Grafico attività utente virtuale** consente anche di determinare i picchi di utilizzo della CPU, le cadute di richieste al secondo e i test o le pagine in esecuzione durante tali picchi o cadute.

> [!NOTE]
> Prima di eseguire il test di carico per il quale si intende usare il **grafico dei dettagli relativi all'attività utente virtuale**, è necessario verificare che la proprietà **Intervallo archiviazione dettagli** sia impostata su **AllIndividualDetails** tramite l'Editor test di carico.

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
|**Eseguire il test di carico:** dopo che un test di carico è stato creato e configurato per abilitare la raccolta dati dell'attività utente virtuale, è necessario eseguire il test fino al completamento per visualizzare il **Grafico attività utente virtuale**.||
|**Visualizzare i risultati del test di carico contenenti i dati dell'attività utente virtuale:** dopo aver creato e configurato un test di carico e averne completata l'esecuzione, è possibile visualizzare i dati dell'attività utente virtuale tramite il **Grafico attività utente virtuale**.|-   [Analizzare i risultati dei test di carico](../test/analyze-load-test-results-using-the-load-test-analyzer.md)<br />-   [Procedura: Analizzare le attività degli utenti virtuali durante un test di carico](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**Isolare i problemi di prestazioni nei test di carico:** è possibile usare il **Grafico attività utente virtuale** per isolare i problemi di prestazioni nel test di carico.|-   [Procedura dettagliata: Uso del grafico attività utente virtuale per isolare i problemi](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>Vedere anche

- [Analizzare i risultati dei test di carico](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analizzare i risultati e gli errori dei test di carico nella visualizzazione Tabelle](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)