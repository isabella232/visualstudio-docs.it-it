---
title: Creare un progetto di test di carico e Web
description: Informazioni su come creare ed eseguire un progetto di test di carico e prestazioni Web in Visual Studio questo avvio rapido.
ms.custom: SEO-VS-2020
ms.date: 03/14/2018
ms.topic: quickstart
helpviewer_keywords:
- load testing, quickstart
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: dfc8f4835c2534c80109b3fc93eb7907bcef729d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122054236"
---
# <a name="quickstart-create-a-load-test-project"></a>Guida introduttiva: Creare un progetto di test di carico

In questa Guida introduttiva di 10 minuti si apprenderà come creare ed eseguire un progetto di test di carico e prestazioni Web in Visual Studio. I test di carico eseguono prestazioni Web o unit test per simulare l'accesso di molti utenti a un server nello stesso momento.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="software-requirements"></a>Requisiti software

I progetti di test di carico e prestazioni Web sono disponibili solo nell'**edizione Enterprise** di Visual Studio.

## <a name="install-the-load-testing-component"></a>Installare il componente di test di carico

Se il componente degli strumenti per test di carico e delle prestazioni Web non è già installato, è necessario installarlo tramite il programma di installazione di Visual Studio.

1. Aprire **Programma di installazione di Visual Studio** dal menu **Start** di Windows. È anche possibile accedervi in Visual Studio dalla finestra di dialogo nuovo progetto o scegliendo Strumenti  >  **Ottieni** strumenti e funzionalità dalla barra dei menu.

1. In **Programma di installazione di Visual Studio** scegliere la scheda **Singoli componenti** e scorrere verso il basso fino alla sezione **Debug e test**. Selezionare **Strumenti per test di carico e delle prestazioni Web**.

   ![Componente Strumenti per test di carico e delle prestazioni Web](media/web-perf-load-testing-tools-component.png)

1. Fare clic sul pulsante **Modifica**.

   Il componente Strumenti per test di carico e delle prestazioni Web è stato installato.

## <a name="create-a-load-test-project"></a>Creare un progetto di test di carico

In questa sezione si creerà un progetto di test di carico in C#. È anche possibile creare un progetto di test di carico di Visual Basic, se si preferisce.

::: moniker range="vs-2017"

1. Aprire Visual Studio.

2. Scegliere **File** > **nuovo** > **Project** dalla barra dei menu.

   Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

3. Nella finestra di dialogo **Nuovo progetto** espandere **Installato** e **Visual C#** e quindi scegliere la categoria **Test**. Scegliere il modello **Progetto di test di carico e prestazioni Web**.

   ![Modello Progetto di test di carico e prestazioni Web](media/web-perf-load-test-project-template.png)

4. Immettere un nome per il progetto se non si vuole usare il nome predefinito e quindi scegliere **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Aprire Visual Studio.

2. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

3. Nella pagina **Crea un nuovo progetto** digitare **test web** nella casella di ricerca e quindi selezionare il modello **Progetto di test di carico e prestazioni Web \[Deprecato]** per C#. Scegliere **Avanti**.

4. Immettere un nome per il progetto se non si vuole usare il nome predefinito e quindi scegliere **Crea**.

::: moniker-end

   Visual Studio crea il progetto e visualizza i file in **Esplora soluzioni**. Il progetto contiene inizialmente un file di test Web denominato *WebTest1.webtest*.

## <a name="add-a-load-test-to-the-project"></a>Aggiungere un test di carico al progetto

1. Dal menu di scelta rapida o dal menu di scelta rapida del nodo del progetto **in** Esplora soluzioni scegliere **Aggiungi**  >  **test di carico**.

   Viene avviata la **Creazione guidata test di carico**.

1. Selezionare l'opzione **Test di carico locale** e quindi scegliere **Avanti**. Per altre informazioni sul test di carico basato su cloud, fare clic [qui](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts&preserve-view=true).

   ![Prima pagina della Creazione guidata test di carico](media/load-test-wizard-page-1.png)

1. Scegliere **Avanti** per eseguire la procedura guidata fino a raggiungere la pagina **Aggiungere i test a uno scenario di test di carico e modificare la combinazione di test**. Fare clic sul pulsante **Aggiungi**.

   Si apre la finestra di dialogo **Aggiungi test**.

1. Sotto **Test disponibili** selezionare **WebTest1** e quindi scegliere la freccia destra per spostarlo nella finestra **Test selezionati**. Fare clic su **OK** .

   ![Finestra di dialogo Aggiungi test](media/add-tests-dialog-box.png)

1. Nella **Creazione guidata test di carico** scegliere il pulsante **Fine**.

   Il test di carico viene aggiunto al progetto e il file del test di carico viene aperto nella finestra dell'editor.

## <a name="run-the-load-test"></a>Eseguire il test di carico

Abbiamo creato un test di carico che non esegue molte operazioni ma procederemo comunque alla sua esecuzione.

Dal menu di scelta rapida o menu a comparsa del test di carico aperto nell'editor scegliere **Esegui test di carico**.

![Menu Esegui test di carico](media/run-load-test.png)

Viene avviata l'esecuzione del test di carico. La finestra **Risultati test** indica che il test è in corso e l'analizzatore test di carico viene visualizzato nella finestra dell'editor. Dopo il completamento del test, che richiede cinque minuti se sono state accettate le impostazioni predefinite, nell'editor viene visualizzato un riepilogo. È possibile scegliere **Grafici**, **Tabelle**, o **Dettagli** per ottenere informazioni diverse sui risultati del test di carico.

![Finestra dell'analizzatore test di carico](media/load-test-analyzer.png)

## <a name="next-steps"></a>Passaggi successivi

Dopo aver creato un progetto di test di carico semplice, il passaggio successivo consiste nel configurare scenari, insiemi di contatori e impostazioni esecuzione test.

> [!div class="nextstepaction"]
> [Modifica impostazioni test](edit-load-tests.md)
