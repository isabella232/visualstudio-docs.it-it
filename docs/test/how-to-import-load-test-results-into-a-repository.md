---
title: 'Procedura: importare i risultati del test di carico in un repository'
description: Informazioni su come caricare le informazioni nel repository load Risultati test usando la finestra di dialogo Apri e gestisci Risultati test caricamento.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- results, load test
- load test results, importing
- Load Test Results Repository
- load tests, importing results
ms.assetid: a955b3d2-c8ad-40dd-8ea3-9f1a271e1eed
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 61b0fdf8ea07ba7ad5106fccdd3543228651cd2a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092488"
---
# <a name="how-to-import-load-test-results-into-a-repository"></a>Procedura: Importare i risultati del test di carico in un repository

Quando si esegue un test di carico, le informazioni raccolte durante l'esecuzione vengono archiviate nel repository dei risultati del test di carico. Il repository dei risultati del test di carico contiene i dati del contatore delle prestazioni e le informazioni sugli errori. Per altre informazioni, vedere [Gestire i risultati dei test di carico nel repository di load Risultati test](../test/manage-load-test-results-in-the-load-test-results-repository.md).

È possibile gestire i risultati del test di carico dall'Editor test di carico usando la finestra di dialogo **Apri e gestisci risultati del test di carico**. È possibile aprire, importare, esportare e rimuovere i risultati test di carico.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-import-results-into-a-repository"></a>Per importare i risultati in un repository

1. Da un progetto di test di carico e prestazioni web aprire un test di carico.

2. Scegliere **Apri e gestisci risultati** nella barra degli strumenti incorporata.

     Viene visualizzata la finestra di dialogo **Apri e gestisci risultati del test di carico**.

3. In **Immettere un nome del controller per trovare i risultati del test di carico** selezionare un controller. Selezionare questa **\<local>** opzione per accedere ai risultati archiviati in locale.

     Se disponibili, i risultati del test di carico sono visualizzati nell'elenco **Risultati test di carico**. L'elenco contiene le colonne **Ora**, **Durata**, **Utente**, **Risultato**, **Test** e **Descrizione**. In **Test** è indicato il nome del test, mentre in **Descrizione** è riportata la descrizione facoltativa aggiunta prima dell'esecuzione del test.

4. Scegliere **Importa**.

     Viene visualizzata la finestra di dialogo **Importa risultati test di carico**.

5. Nella casella **Nome file** digitare il nome di un file dei risultati del test archiviato e scegliere **Apri**.

     \- - oppure -

     Individuare il file e scegliere **Apri**.

    > [!NOTE]
    > Un file dei risultati del test archiviato specificato in questo passaggio deve essere stato creato mediante un'operazione di esportazione.

     I risultati vengono importati e visualizzati nell'elenco **Risultati test di carico**.

## <a name="see-also"></a>Vedi anche

- [Gestire i risultati dei test di carico nel repository Risultati test carico](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Analizzare i risultati dei test di carico](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Procedura: Esportare i risultati dei test di carico da un repository](../test/how-to-export-load-test-results-from-a-repository.md)
