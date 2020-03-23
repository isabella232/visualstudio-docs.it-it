---
title: Esportare i risultati del test di carico
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load tests, exporting results
- Load Test Results Repository
- load test results, exporting
ms.assetid: 716c2af5-8737-4d31-956f-a0273f7c5c0c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f72dbd687bc9177cd4cfd36416acb23445d30c8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589045"
---
# <a name="how-to-export-load-test-results-from-a-repository"></a>Procedura: Esportare i risultati di un test di carico da un repository

Quando si esegue un test di carico, le informazioni raccolte durante l'esecuzione vengono archiviate nel repository dei risultati del test di carico. Il repository dei risultati del test di carico contiene i dati del contatore delle prestazioni e le informazioni sugli errori. Per ulteriori informazioni, vedere Gestire i risultati dei test di [carico nel repository dei risultati](../test/manage-load-test-results-in-the-load-test-results-repository.md)del test di carico .

È possibile gestire i risultati del test di carico dall'Editor test di carico usando la finestra di dialogo **Apri e gestisci risultati del test di carico**. È possibile aprire, importare, esportare e rimuovere i risultati test di carico.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-export-results-from-a-repository"></a>Per esportare i risultati da un repository

1. Da un progetto di test di carico e prestazioni web aprire un test di carico.

2. Scegliere **Apri e gestisci risultati** nella barra degli strumenti incorporata.

     Viene visualizzata la finestra di dialogo **Apri e gestisci risultati del test di carico**.

3. In **Immettere un nome del controller per trovare i risultati del test di carico** selezionare un controller. Selezionare Locale ** \<- Nessun controller>** per accedere ai risultati archiviati localmente.

4. In **Mostra risultati per test di carico seguente** selezionare il test di carico di cui si vuole visualizzare i risultati. Selezionare Mostra ** \<risultati per tutti i test>** per visualizzare tutti i risultati per tutti i test.

     Se i risultati test di carico sono disponibili, saranno visualizzati nell'elenco **Risultati test di carico**. L'elenco contiene le colonne **Ora**, **Durata**, **Utente**, **Risultato**, **Test** e **Descrizione**. In **Test** è indicato il nome del test, mentre in **Descrizione** è riportata la descrizione facoltativa aggiunta prima dell'esecuzione del test. Nella colonna **Descrizione** sono visualizzate le descrizioni brevi immesse in **Commenti analisi** per i risultati del test.

5. Nell'elenco **Risultati test di carico** scegliere un risultato. È possibile utilizzare **MAIUSC**, **CTRL** o entrambi i tasti per selezionare più risultati ed esportarli in un singolo file.

6. Scegliere **Esporta**.

     Viene visualizzata la finestra di dialogo **Esporta risultati test di carico**.

7. Digitare un nome nella casella **Nome file** e scegliere **Salva**.

     I risultati vengono esportati in un file di archivio.

    > [!NOTE]
    > La finestra di dialogo **Apri e gestisci risultati del test di carico** rimane aperta dopo la visualizzazione dei risultati.

## <a name="see-also"></a>Vedere anche

- [Gestire i risultati dei test di carico nel repository dei risultati del test di caricoManage load test results in the Load Test Results Repository](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Procedura: eliminare i risultati dei test di carico da un repositoryHow to: Delete load test results from a repository](../test/how-to-delete-load-test-results-from-a-repository.md)
- [Analizzare i risultati dei test di caricoAnalyze load test results](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Procedura: importare i risultati dei test di carico in un repositoryHow to: Import load test results into a repository](../test/how-to-import-load-test-results-into-a-repository.md)
