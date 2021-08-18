---
title: Creare ed eseguire un test di carico
description: Informazioni su come creare un test di carico contenente unit test. È possibile creare ed eseguire test di carico usando Visual Studio Enterprise.
ms.custom: SEO-VS-2020
ms.date: 10/01/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, in load tests
- unit tests, load test walkthrough
- load tests, walkthrough
ms.assetid: bbf075a5-96d5-48ed-a03c-330f0fc04748
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: c42c6a98ab9b453131af383b5b39a1c12ed9e895
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038318"
---
# <a name="walkthrough-create-and-run-a-load-test-that-contains-unit-tests"></a>Procedura dettagliata: Creare ed eseguire un test di carico contenente unit test

In questa procedura dettagliata viene creato un test di carico contenente unit test.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Questa procedura descrive i passaggi necessari per la creazione e l'esecuzione di un test di carico tramite Visual Studio Enterprise. Un test di carico è un contenitore di test delle prestazioni Web e di unit test. È possibile creare test di carico con la **Creazione guidata test di carico**.

In un test di carico sono presenti anche molte proprietà di runtime che possono essere modificate per generare la simulazione di carico desiderata. In questa procedura dettagliata viene usata la **Creazione guidata test di carico** per aggiungere unit test a un test di carico.

In questa procedura dettagliata, si completeranno le seguenti attività:

- Creare un test di carico in cui vengono utilizzati unit test.

- Modifica di alcune impostazioni di un test di carico.

- Esecuzione di un test di carico.

- Eseguire i passaggi descritti in [Procedura dettagliata:](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) Creazione ed esecuzione di unit test per il codice gestito per creare una libreria di classi C# semplice contenente un progetto di test di carico e prestazioni Web con alcuni unit test.

## <a name="create-a-load-test-containing-unit-tests-using-the-new-load-test-wizard"></a>Creare un test di carico contenente unit test tramite la Creazione guidata test di carico

### <a name="to-start-the-new-load-test-wizard"></a>Per avviare la Creazione guidata test di carico

1. Assicurarsi di aver installato il componente Strumenti per test di carico e **prestazioni Web** descritto in Creare un progetto di test di [carico.](../test/quickstart-create-a-load-test-project.md)

1. Aprire la soluzione Bank creata in Procedura [dettagliata: Creazione ed esecuzione di unit test per codice gestito.](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo soluzione Bank, scegliere **Aggiungi** e quindi **Nuovo progetto**.

     Viene visualizzata la finestra di dialogo **Aggiungi nuovo progetto**.

1. Nella finestra **di dialogo Aggiungi nuovo Project** espandere Visual **C#** e scegliere **Test**. Nell'elenco di modelli scegliere **Progetto di test di carico e prestazioni Web** e, nel campo **Nome**, digitare `BankLoadTest`. Scegliere **OK**.

     Il progetto di test di carico e prestazioni Web di BankLoadTest viene aggiunto alla soluzione.

1. Aprire il menu di scelta rapida per il nuovo progetto di test di carico e prestazioni Web di BankLoadTest, scegliere **Aggiungi** e quindi **Test di carico**.

1. Viene avviata la **Creazione guidata test di carico**.

1. La pagina di **Benvenuto** della **Creazione guidata test di carico** è la prima pagina.

1. Scegliere **Avanti**.

### <a name="to-edit-settings-for-load-test-scenario"></a>Per modificare le impostazioni per uno scenario di test di carico

1. Nella casella di testo **Immettere un nome per lo scenario di test di carico** digitare **ScenarioSample**.

     Uno *scenario* è un meccanismo di raggruppamento. È composto da una serie di test e di proprietà per l'esecuzione di tali test sotto carico.

2. Impostare il **Profilo tempo interazione utente** su `Use normal distribution centered on recorded think times`. Il tempo interazione utente rappresenta il tempo che un utente dedica a una pagina Web prima di passare alla successiva.

1. Al termine scegliere **Avanti**.

### <a name="to-edit-load-pattern-setting-for-test-scenario"></a>Per modificare l'impostazione del modello di carico per lo scenario di test

1. Scegliere **Carico per passaggio**.

    > [!NOTE]
    > È possibile scegliere da due tipi di modelli di carico: costante e per passaggio. Ogni tipo ha una funzione specifica nell'ambito dei test di carico. Ai fini di questa procedura dettagliata scegliere **Carico per passaggio**.

2. Impostare **Numero iniziale utenti** su 10 utenti.

3. Impostare **Durata passaggio** su 10 secondi.

4. Impostare **Numero utenti per passaggio** su 10 utenti per passaggio.

5. Impostare **Numero massimo utenti** su 100 utenti.

6. Scegliere **Avanti**.

### <a name="to-select-test-mix-model-for-the-scenario"></a>Per selezionare un modello di combinazione di test per lo scenario

1. In **Come deve essere modellata la combinazione di test** selezionare In base al numero totale di **test.**

2. Scegliere **Avanti**.

### <a name="to-add-unit-tests-to-the-scenario"></a>Per aggiungere unit test allo scenario

1. Il passaggio successivo consente di **aggiungere test a uno scenario di test di carico e modificare una combinazione di test**.

2. Scegliere **Aggiungi** per selezionare i test.

3. Scegliere gli unit **test CreditTest** elencati nel riquadro Test **disponibili,** in cui sono elencati tutti i test delle prestazioni Web e gli unit test nel progetto di test di carico e delle prestazioni Web.

4. Scegliere la freccia per aggiungere il unit test **CreditTest** al **riquadro Test** selezionati.

5. Ripetere i passaggi 3 e 4 per gli unit test **DebitTest** e **FreezeAccountTest**.

6. Dopo avere aggiunto i tre unit test, scegliere **OK**.

     Viene visualizzata una combinazione di test.

7. Spostare leggermente il dispositivo di scorrimento sotto **Distribuzione** per **CreditTest** per regolare la distribuzione del test. Si noti che gli altri dispositivi di scorrimento si spostano automaticamente verso sinistra, in modo che la distribuzione rimanga uguale a 100%.

8. Scegliere **Avanti**.

### <a name="to-select-network-mix-for-test-scenario"></a>Per selezionare la combinazione di reti per lo scenario di test

1. Selezionare il tipo di connessione LAN da aggiungere alla combinazione della larghezza di banda della rete.

     È possibile aggiungere altri tipi di rete. Utilizzare i dispositivi di scorrimento per regolare la distribuzione e il peso dei test.

2. Scegliere **Avanti**.

### <a name="to-specify-computers-to-monitor-with-counter-sets-during-load-test-run"></a>Per specificare i computer da monitorare con gli insiemi di contatori durante l'esecuzione del test di carico

1. Scegliere **Avanti**.

     Per altre informazioni sugli insiemi di contatori, vedere [Specificare insiemi di contatori e regole di soglia per i computer in un test di carico](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

### <a name="to-edit-run-setting-for-load-test"></a>Per modificare l'impostazione di esecuzione per il test di carico

1. Selezionare **Durata test di carico** e quindi impostare **Durata esecuzione** su 2 minuti per eseguire uno *smoke test* del test di carico.

     Quando vengono compilati i test di carico, è consigliabile verificare di avere impostato tutto correttamente e che tutto funzioni come previsto eseguendo un breve test di carico ridotto. Questo processo è noto come *smoke test*.

2. Scegliere **Fine**. Il testo di carico si apre nell'**Editor test di carico**.

## <a name="run-the-load-test"></a>Eseguire il test di carico
 Una volta creato il test di carico, eseguirlo per visualizzare il modo in cui l'applicazione bancaria risponde alla simulazione di carico. Mentre il test di carico è in esecuzione, viene visualizzata la finestra **Analizzatore test di carico**.

### <a name="to-run-the-load-test"></a>Per eseguire il test di carico

1. Dopo aver aperto un test di carico nell'**Editor test di carico**, scegliere il pulsante verde **Esegui test** sulla barra degli strumenti. Il test di carico viene eseguito.

2. Se la simulazione di test supera una o più soglie, vengono visualizzate le icone nei nodi di controllo per indicare la violazione di soglia. Gli errori sono indicati da un cerchio rosso, gli avvisi da un triangolo giallo. Per individuare il contatore che ha superato la soglia e tracciarne il grafico, trascinare l'icona sul grafico. Questa operazione può essere effettuata durante l'esecuzione del test.

## <a name="see-also"></a>Vedi anche

- [Modificare la combinazione di test per specificare quali test includere in uno scenario di test di carico](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Specificare i tipi di rete virtuale](../test/specify-virtual-network-types-in-a-load-test-scenario.md)
- [Modificare gli scenari di test di carico](../test/edit-load-test-scenarios.md)
- [Modificare i modelli di carico per modellare le attività degli utenti virtuali](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Modificare modelli di combinazione di testo per specificare la probabilità che un utente virtuale ese1 un test](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
