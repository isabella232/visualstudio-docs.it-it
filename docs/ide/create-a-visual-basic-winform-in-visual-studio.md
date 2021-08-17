---
title: Creare un'app Windows Forms con Visual Basic
description: Informazioni dettagliate su come creare un'app Windows Forms in Visual Studio con Visual Basic.
ms.date: 09/27/2019
ms.topic: tutorial
ms.devlang: vb
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: cc70ff9887866f0109edb6fbc41b50be5a292f043723319805cd3674f7e1ce59
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121373881"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-visual-basic"></a>Creare un'app Windows Forms in Visual Studio con Visual Basic

In questa breve introduzione all'ambiente di sviluppo integrato (IDE) di Visual Studio si creerà una semplice applicazione di Visual Basic con un'interfaccia utente basata su Windows.

::: moniker range="vs-2017"

Se non è già stato installato Visual Studio, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se non è già stato installato Visual Studio, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

> [!NOTE]
> Alcune delle schermate contenute in questa esercitazione usano il tema scuro. Per passare al tema scuro, qualora questo non fosse già in uso, vedere le informazioni disponibili nella pagina [Personalizzare l'IDE e l'editor di Visual Studio](../ide/quickstart-personalize-the-ide.md).

::: moniker-end

::: moniker range="vs-2022"

Se non è già stato installato Visual Studio, passare alla pagina di download di [Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) per installarla gratuitamente.

> [!NOTE]
> Alcune delle schermate contenute in questa esercitazione usano il tema scuro. Per passare al tema scuro, qualora questo non fosse già in uso, vedere le informazioni disponibili nella pagina [Personalizzare l'IDE e l'editor di Visual Studio](../ide/quickstart-personalize-the-ide.md).

::: moniker-end

## <a name="create-a-project"></a>Creare un progetto

In primo luogo si creerà un progetto di applicazione Visual Basic. Il tipo di progetto include fin dall'inizio tutti i file modello necessari.

::: moniker range="vs-2017"

1. Aprire Visual Studio 2017.

1. Nella barra dei menu superiore scegliere **File** > **nuovo** > **Project**.

1. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **Visual Basic**, quindi selezionare **Desktop di Windows**. Nel riquadro centrale scegliere il modello **App Windows Forms (.NET Framework)**. Assegnare al file il nome `HelloWorld`.

     Se non viene visualizzato il modello del progetto **App Windows Forms (.NET Framework)**, chiudere la finestra di dialogo **Nuovo progetto** e nella barra dei menu superiore scegliere **Strumenti** > **Ottieni strumenti e funzionalità**. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo per desktop .NET**, quindi scegliere **Modifica**.

     ![Carico di lavoro Sviluppo per desktop .NET nel programma di installazione di Visual Studio](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. Aprire Visual Studio.

1. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

   ![Visualizzare la finestra Crea un nuovo progetto](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Nella finestra **Crea un nuovo progetto** scegliere il modello Windows Forms App **(.NET Framework)** per Visual Basic.

   Se si preferisce, è possibile perfezionare la ricerca per ottenere rapidamente il modello desiderato. Ad esempio, immettere o digitare *Windows Forms App* nella casella di ricerca. Scegliere quindi **Visual Basic** dall'elenco Lingua e quindi **scegliere** Windows dall'elenco Piattaforma.  

   ![Scegliere il modello Visual Basic per l'app Windows Forms (.NET Framework)](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Se il modello **App Windows Forms (.NET Core)** non viene visualizzato, è possibile installarlo dalla finestra **Crea un nuovo progetto**. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**.
   >
   > ![Collegamento "Installa altri strumenti e funzionalità" nel messaggio "L'elemento cercato non è stato trovato?" nella finestra "Crea un nuovo progetto"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Scegliere quindi il carico di lavoro **Sviluppo per desktop .NET** nel programma di installazione di Visual Studio.
   >
   > ![Carico di lavoro Sviluppo per desktop .NET nel programma di installazione di Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Successivamente, scegliere il pulsante **Modifica** nel programma di installazione di Visual Studio. Quando viene richiesto, salvare il lavoro. Scegliere quindi **Continua** per installare il carico di lavoro. Quindi tornare al passaggio 2 della procedura [Creare un progetto](#create-a-project)".

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *HelloWorld* nella casella **Nome del progetto**. Scegliere quindi **Crea**.

   ![Nella finestra Configura il nuovo progetto assegnare al progetto il nome "HelloWorld"](../get-started/visual-basic/media/vs-2019/vb-name-your-winform-project-helloworld.png)

   Visual Studio aprirà il nuovo progetto.

::: moniker-end

## <a name="create-the-application"></a>Creare l'applicazione

Dopo aver selezionato il modello di progetto Visual Basic e assegnato un nome al file, in Visual studio viene aperto un modulo. Un modulo è un'interfaccia utente di Windows. Si creerà un'applicazione "Hello World" aggiungendo controlli al form e quindi si eseguirà l'app.

### <a name="add-a-button-to-the-form"></a>Aggiungere un pulsante al modulo

1. Fare clic su **Casella degli strumenti** per aprire la finestra a comparsa della casella degli strumenti.

     ![Fare clic su Casella degli strumenti per aprire la finestra della casella degli strumenti](../ide/media/vb-toolbox-toolwindow.png)

     Se l'opzione a  comparsa Casella degli strumenti non è visualizzata, è possibile aprirla dalla barra dei menu. A tale scopo, visualizzare **la casella degli**  >  **strumenti**. In caso contrario, **premere** + **CTRL** + **ALT+X.**

1. Fare clic sull'icona **Blocca** per ancorare la **Casella degli strumenti**.

     ![Fare clic sull'icona Blocca per ancorare la Casella degli strumenti all'IDE](../ide/media/vb-pin-the-toolbox-window.png)

1. Fare clic sul controllo **Pulsante** e trascinarlo nel modulo.

     ![Aggiungere un pulsante al modulo](../ide/media/vb-add-a-button-to-form1.png)

1. Nella sezione **Aspetto** o nella sezione **Tipi di carattere** della finestra **Proprietà** digitare `Click this` e quindi premere **INVIO**.

     ![Aggiungere testo al pulsante nel modulo](../ide/media/vb-button-control-text.png)

     (Se la finestra **Proprietà** non viene visualizzata, è possibile aprirla dalla barra dei menu. A tale scopo, fare clic **su**  >  **Visualizza finestra Proprietà**. In caso contrario, **premere F4.**

1. Nella sezione **Progettazione** della finestra **Proprietà** cambiare il nome da **Button1** a `btnClickThis`, quindi premere **INVIO**.

     ![Aggiungere una funzione al pulsante nel modulo](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > Se l'elenco è stato  alfabetico nella finestra Proprietà, **Button1** viene invece visualizzato nella sezione **(DataBindings).**

### <a name="add-a-label-to-the-form"></a>Aggiungere un'etichetta al modulo

È stato aggiunto un controllo pulsante per creare un'azione. Ora si aggiungerà un controllo etichetta al quale inviare del testo.

1. Selezionare il **controllo Etichetta** dalla finestra **Casella degli** strumenti e trascinarlo nel form e rilasciarlo sotto il pulsante Fare clic su **questo** pulsante.

1. Nella sezione **Progettazione** o **(DataBindings)** della  finestra Proprietà modificare il nome di **Label1** in `lblHelloWorld` e quindi premere **INVIO.**

### <a name="add-code-to-the-form"></a>Aggiungere codice al modulo

1. Nella finestra **Form1.vb &#91;Design&#93;** fare doppio clic sul pulsante **Click this** per aprire la finestra **Form1.vb**.

      In alternativa è possibile espandere **Form1.vb** in **Esplora soluzioni** e quindi fare clic su **Form1**.

1. Nella finestra **Form1.vb,** tra le righe **Private Sub** ed **End Sub,** digitare o immettere `lblHelloWorld.Text = "Hello World!"` come illustrato nello screenshot seguente:

     ![Aggiungere codice al modulo](../ide/media/vb-add-code-to-the-form.png)

## <a name="run-the-application"></a>Eseguire l'applicazione

1. Fare clic sul pulsante **Avvia** per eseguire l'applicazione.

     ![Fare clic su Avvia per eseguire il debug e avviare l'app](../ide/media/vb-click-start-hello-world.png)

   Vengono eseguite diverse operazioni. Nell'IDE di Visual Studio viene aperta la finestra **Strumenti di diagnostica** e anche una finestra **Output**. All'esterno dell'IDE viene visualizzata una finestra di dialogo **Form1**. La finestra include il pulsante **Click this** e il testo **Label1**.

1. Fare clic sul pulsante **Click this** nella finestra di dialogo **Form1**. Osservare che il testo **Label1** diventa **Hello World!**.

    ![Finestra di dialogo Form1 con il testo Label1 ](../ide/media/vb-form1-dialog-hello-world.png)

1. Chiudere la **finestra di dialogo Form1** per arrestare l'esecuzione dell'app.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni, passare all'esercitazione successiva:

> [!div class="nextstepaction"]
> [Esercitazione: Creare un visualizzatore di immagini](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Vedi anche

* [Altre Visual Basic esercitazioni](../get-started/visual-basic/index.yml)
* [Esercitazioni su C#](../get-started/csharp/index.yml)
* [Esercitazioni su C++](/cpp/get-started/tutorial-console-cpp)