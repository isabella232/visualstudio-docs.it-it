---
title: Dettagli intervallo Archiviazione proprietà (impostazione esecuzione test di carico)
description: Informazioni su come modificare la proprietà Intervallo dettagli Archiviazione per un'impostazione di esecuzione. I valori validi sono Tutti i singoli dettagli, Nessuno e Solo statistiche.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 867a9c21-0909-4963-bc02-d41e9393008c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: c1133e5d840e1d5e13a8d184c9459fd8757e8d7932c3580d5d44e2ac5dce2b35
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121409059"
---
# <a name="how-to-specify-the-timing-details-storage-property-for-a-load-test-run-setting"></a>Procedura: Specificare la proprietà Intervallo archiviazione dettagli per un'impostazione di esecuzione test di carico

Dopo avere creato il test di carico mediante la **Creazione guidata test di carico**, è possibile usare l'**Editor test di carico** per modificare le impostazioni in modo da soddisfare le necessità e gli obiettivi di test.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Usando l'Editor test di carico, è possibile modificare un valore della proprietà **Intervallo archiviazione dettagli** di un'impostazione di esecuzione nella finestra **Proprietà**. È possibile impostare la proprietà **Intervallo archiviazione dettagli** su una delle opzioni seguenti:

- **Tutti i singoli dettagli:** vengono raccolti e archiviati dati di intervallo individuali per i singoli test, transazioni e pagine emessi nel corso del test.

  > [!NOTE]
  > È necessario selezionare l'opzione **Tutti i singoli dettagli** per abilitare le informazioni sui dati degli utenti virtuali nei risultati del test di carico. Per altre informazioni, vedere [Analizzare l'attività utente virtuale nella visualizzazione Dettagli](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

- **Nessuno:** non vengono raccolti dettagli di intervallo individuali. Sono tuttavia disponibili i valori medi.

- **Solo statistiche:** vengono archiviati dati di intervallo individuali, ma solo come dati percentili. In questo modo, è possibile risparmiare spazio.

  **Considerazioni per la proprietà Intervallo archiviazione dettagli**

  Se la proprietà **Intervallo archiviazione dettagli** è abilitata, il tempo richiesto per eseguire ogni singolo test, transazione e pagina durante il test di carico verrà archiviato nel repository dei risultati del test di carico. In questo modo i dati del 90° e del 95° percentile possono essere visualizzati nell'Analizzatore **test** di carico nelle tabelle **Test,** **Transazioni** **e** Pagine.

  Se la proprietà **Intervallo archiviazione dettagli** è abilitata, impostando il valore su **StatisticsOnly** o **AllIndividualDetails**, tutti i singoli test, pagine e transazioni vengono temporizzati e dati percentili vengono calcolati dai dati di intervallo individuali. La differenza per quanto riguarda l'opzione **StatisticsOnly** consiste nel fatto che i singoli dati di intervallo vengono eliminati dal repository dopo il calcolo dei dati percentili. In questo modo si riduce la quantità di spazio richiesta nel repository quando si utilizzano i dettagli dell'intervallo. Tuttavia, potrebbe essere necessario elaborare i dati dettaglio dell'intervallo in altri modi mediante strumenti SQL, nel qual caso deve essere usata l'opzione **AllIndividualDetails** in modo che i dati dettaglio dell'intervallo siano disponibili per quell'elaborazione. Inoltre, se si imposta la proprietà su **AllIndividualDetails**, è possibile analizzare l'attività utente virtuale usando il Grafico attività utente virtuale nell'Analizzatore test di carico al termine dell'esecuzione del test di carico.   Per altre informazioni, vedere [Analizzare l'attività utente virtuale nella visualizzazione Dettagli](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

  La quantità di spazio richiesta nel repository dei risultati del test di carico per l'archiviazione dei dati dettaglio dell'intervallo potrebbe essere molto elevata, soprattutto per i test di carico a esecuzione prolungata. Inoltre, è necessario più tempo per archiviare questi dati nel repository dei risultati alla fine del test di carico, in quanto tali dati vengono archiviati negli agenti del test di carico fino al termine dell'esecuzione del test di carico e solo allora vengono archiviati nel repository. La proprietà **Intervallo archiviazione dettagli** è abilitata per impostazione predefinita. Se ciò costituisce un problema per l'ambiente di test, è consigliabile impostare l'**Intervallo archiviazione dettagli** su **Nessuno**.

  I dati dei dettagli di intervallo vengono archiviati nel file *LoadTestItemResults.dat* durante l'esecuzione e vengono inviati di nuovo al controller dopo il completamento del test di carico. Per un test di carico eseguito per un lungo periodo di tempo, le dimensioni del file saranno elevate. Se lo spazio su disco nel computer dell'agente è insufficiente, potrebbero avere luogo problemi.

  Se si aggiorna un progetto da una versione precedente di un test di carico di Visual Studio, attenersi alla procedura riportata di seguito per abilitare la raccolta completa dei dettagli.

## <a name="to-configure-the-timing-details-storage-property-in-a-load-test"></a>Per configurare la proprietà di archiviazione dei dettagli di intervallo in un test di carico

1. Aprire un test di carico nell'Editor test di carico.

2. Espandere il nodo **Impostazioni di esecuzione** nel test di carico.

3. Scegliere le impostazioni di esecuzione test che si vuole configurare, ad esempio **Run Settings1[Active]**.

4. Aprire la **finestra** Proprietà. Scegliere **Finestra Proprietà** dal menu **Visualizza**.

5. Nella categoria **Risultati** scegliere la proprietà **Intervallo archiviazione dettagli** e selezionare **Tutti i singoli dettagli**.

     Dopo aver configurato l'impostazione **Tutti i singoli dettagli** per la proprietà **Intervallo archiviazione dettagli** è possibile eseguire il test di carico e visualizzare il **Grafico attività utente virtuale**. Per altre informazioni, vedere Procedura: Analizzare le attività [degli utenti virtuali durante un test di carico.](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)

## <a name="see-also"></a>Vedi anche

- [Analisi dell'attività utente virtuale nella visualizzazione Dettagli](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Procedura dettagliata: Uso del Grafico attività utente virtuale per isolare i problemi](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)
