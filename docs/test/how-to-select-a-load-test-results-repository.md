---
title: 'Procedura: selezionare un repository dei risultati del test di carico'
description: Informazioni su come identificare un server di test locale o SQL per archiviare i risultati dei test. Il server deve avere un archivio dei risultati del test di carico.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.load.dialog.connectstringmissing
- vs.test.load.dialog.databaseconnectstring
helpviewer_keywords:
- load tests, results repository
- results, load test
- load test results, repository
- Load Test Results Repository
- SQL, Load Test Results Store
ms.assetid: fa0c4dd9-612f-4a57-b8eb-458f129d9cda
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 9e0177154cec399a509046679f7336097873fbc5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075866"
---
# <a name="how-to-select-a-load-test-results-repository"></a>Procedura: Selezionare un repository dei risultati del test di carico

La scelta non è limitata a un archivio dei risultati locale. Spesso i test di carico vengono eseguiti su un insieme remoto di computer agente. Gli agenti, insieme ai controller, consentono di generare un carico simulato maggiore rispetto a un singolo computer. Per altre informazioni, vedere [Test controller e agenti di test.](configure-test-agents-and-controllers-for-load-tests.md)

I risultati ottenuti dai computer agente o locale possono essere memorizzati in qualsiasi server SQL in cui sia stato creato un archivio dei risultati del test di carico. In entrambi i casi è necessario identificare la posizione in cui si vuole archiviare i risultati del test di carico usando la finestra di **amministrazione dei controller di test**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="identify-a-results-store-for-load-test-data"></a>Identificare un archivio dei risultati per i dati dei test di carico

1. In **Esplora soluzioni** aprire il file del test di carico.

2. Dalla barra degli strumenti **Test di carico** scegliere **Gestisci Test Controller**. Verrà visualizzata la finestra di dialogo **Gestisci controller di test**. Se si utilizza un agente in remoto, è necessario selezionare un controller.

     ![Proprietà di connessione dell'archivio dei risultati del test di carico](../test/media/loadtestconnectionproperties.png) Proprietà di connessione dell'archivio dei risultati del test di carico

3. **Nell'archivio risultati test di carico** fare clic su **(...)** per visualizzare la finestra di **dialogo Proprietà** connessione .

4. In **Nome server** digitare il nome del server in cui sono stati eseguiti gli script `LoadTest`.

    > [!TIP]
    > Se si usa SQL Express nel computer locale per l'archivio dei test di carico, immettere \<computername> \sqlexpress, ad esempio **MyComputer\sqlexpress.**

5. In **Accesso al server** è possibile scegliere **Usa autenticazione di Windows**. È possibile specificare il nome utente e la password, ma, in tal caso, è necessario selezionare l'opzione **Salva password**.

6. In **Connessione al database** scegliere **Seleziona o immetti un nome di database**. Dall'elenco a discesa selezionare **LoadTest**.

7. Scegliere **OK**. Per eseguire il test della connessione, scegliere **Test connessione**.

8. Scegliere **Chiudi** nella finestra di dialogo **Gestisci controller di test**.

## <a name="see-also"></a>Vedi anche

- [Gestire i risultati dei test di carico nel repository Risultati test carico](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Test controller e agenti di test](configure-test-agents-and-controllers-for-load-tests.md)
