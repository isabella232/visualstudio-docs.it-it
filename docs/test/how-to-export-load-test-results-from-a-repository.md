---
title: Esportare i risultati del test di carico
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- results, load test
- load tests, exporting results
- Load Test Results Repository
- load test results, exporting
ms.assetid: 716c2af5-8737-4d31-956f-a0273f7c5c0c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f9b20915d5c320ff8db4da849d20267355c26590
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287753"
---
# <a name="how-to-export-load-test-results-from-a-repository"></a>Procedura: Esportare i risultati di un test di carico da un repository

Quando si esegue un test di carico, le informazioni raccolte durante l'esecuzione vengono archiviate nel repository dei risultati del test di carico. Il repository dei risultati del test di carico contiene i dati del contatore delle prestazioni e le informazioni sugli errori. Per altre informazioni, vedere [gestire i risultati dei test di carico nel repository load risultati test](../test/manage-load-test-results-in-the-load-test-results-repository.md).

È possibile gestire i risultati del test di carico dall'Editor test di carico usando la finestra di dialogo **Apri e gestisci risultati del test di carico**. È possibile aprire, importare, esportare e rimuovere i risultati test di carico.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-export-results-from-a-repository"></a>Per esportare i risultati da un repository

1. Da un progetto di test di carico e prestazioni web aprire un test di carico.

2. Scegliere **Apri e gestisci risultati** nella barra degli strumenti incorporata.

     Viene visualizzata la finestra di dialogo **Apri e gestisci risultati del test di carico**.

3. In **Immettere un nome del controller per trovare i risultati del test di carico** selezionare un controller. Selezionare **\<Local - No controller>** per accedere ai risultati archiviati localmente.

4. In **Mostra risultati per test di carico seguente** selezionare il test di carico di cui si vuole visualizzare i risultati. Selezionare questa selezione **\<Show results for all tests>** per visualizzare tutti i risultati per tutti i test.

     Se i risultati test di carico sono disponibili, saranno visualizzati nell'elenco **Risultati test di carico**. L'elenco contiene le colonne **Ora**, **Durata**, **Utente**, **Risultato**, **Test** e **Descrizione**. In **Test** è indicato il nome del test, mentre in **Descrizione** è riportata la descrizione facoltativa aggiunta prima dell'esecuzione del test. Nella colonna **Descrizione** sono visualizzate le descrizioni brevi immesse in **Commenti analisi** per i risultati del test.

5. Nell'elenco **Risultati test di carico** scegliere un risultato. È possibile utilizzare **MAIUSC**, **CTRL** o entrambi i tasti per selezionare più risultati ed esportarli in un singolo file.

6. Scegliere **Esporta**.

     Viene visualizzata la finestra di dialogo **Esporta risultati test di carico**.

7. Digitare un nome nella casella **Nome file** e scegliere **Salva**.

     I risultati vengono esportati in un file di archivio.

    > [!NOTE]
    > La finestra di dialogo **Apri e gestisci risultati del test di carico** rimane aperta dopo la visualizzazione dei risultati.

## <a name="see-also"></a>Vedi anche

- [Gestire i risultati dei test di carico nel repository del Risultati test di carico](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Procedura: eliminare i risultati di un test di carico da un repository](../test/how-to-delete-load-test-results-from-a-repository.md)
- [Analizzare i risultati dei test di carico](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Procedura: importare i risultati di un test di carico in un repository](../test/how-to-import-load-test-results-into-a-repository.md)
