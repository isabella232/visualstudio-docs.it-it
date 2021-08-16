---
title: 'Procedura: eliminare i risultati di un test di carico da un repository'
description: Informazioni su come rimuovere informazioni da Load Risultati test Repository usando la finestra di dialogo Apri e gestisci Risultati test caricamento.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- results, load test
- load tests, deleting results
- load test results, removing
- Load Test Results Repository
- load tests, removing results
- load test results, deleting
ms.assetid: c2afe36b-d061-4f0e-9580-c18569ec08f9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: e5baef422a9dac6ec2eefef3b8e0f7f491a627422c2d1c0e9ba20c606b9e2e4b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121366680"
---
# <a name="how-to-delete-load-test-results-from-a-repository"></a>Procedura: Eliminare i risultati di un test di carico da un repository

Quando si esegue un test di carico, le informazioni raccolte durante l'esecuzione vengono archiviate nel repository dei risultati test di carico. Il repository dei risultati del test di carico contiene i dati del contatore delle prestazioni e le informazioni sugli errori. Per altre informazioni, vedere [Gestire i risultati dei test di carico in Load Risultati test Repository](../test/manage-load-test-results-in-the-load-test-results-repository.md).

È possibile gestire i risultati del test di carico dall'Editor test di carico usando la finestra di dialogo **Apri e gestisci risultati del test di carico**. È possibile aprire, importare, esportare e rimuovere i risultati test di carico.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-delete-results-from-a-repository"></a>Per eliminare i risultati da un repository

1. Da un progetto di test di carico e prestazioni web aprire un test di carico.

2. Scegliere **Apri e gestisci risultati** nella barra degli strumenti incorporata.

     Viene visualizzata la finestra di dialogo **Apri e gestisci risultati del test di carico**.

3. In **Immettere un nome del controller per trovare i risultati del test di carico** selezionare un controller. Selezionare **\<Local - No controller>** questa opzione per accedere ai risultati archiviati in locale.

4. In **Mostra risultati per test di carico seguente** selezionare il test di carico di cui si vuole visualizzare i risultati. Selezionare **\<Show results for all tests>** questa opzione per visualizzare tutti i risultati per tutti i test.

     Se i risultati test di carico sono disponibili, saranno visualizzati nell'elenco **Risultati test di carico**. L'elenco contiene le colonne **Ora**, **Durata**, **Utente**, **Risultato**, **Test** e **Descrizione**. In **Test** è indicato il nome del test, mentre in **Descrizione** è riportata la descrizione facoltativa aggiunta prima dell'esecuzione del test. Nella colonna **Descrizione** sono visualizzate le descrizioni brevi immesse in **Commenti analisi** per i risultati del test.

5. Nell'elenco **Risultati test di carico** scegliere un risultato. È possibile usare **MAIUSC**, **CTRL** o entrambi i tasti per selezionare più risultati.

6. Scegliere **Rimuovi**.

     I risultati verranno rimossi dal repository.

    > [!NOTE]
    > La finestra di dialogo **Apri e gestisci risultati del test di carico** rimane aperta dopo la rimozione dei risultati.

## <a name="see-also"></a>Vedi anche

- [Procedura: Esportare i risultati del test di carico da un repository](../test/how-to-export-load-test-results-from-a-repository.md)
- [Gestire i risultati del test di carico nel repository Risultati test carico](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Analizzare i risultati del test di carico](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Procedura: Importare i risultati del test di carico in un repository](../test/how-to-import-load-test-results-into-a-repository.md)
