---
title: "Creare un'app Windows Forms con C #"
description: Informazioni su come creare un'app Windows Forms in Visual Studio C#, procedura dettagliata.
ms.date: 09/26/2019
ms.topic: tutorial
ms.devlang: CSharp
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 0a274ab647ea420c60ae4e62fb0939c44ec212fd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628823"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-c"></a>Creare un'app Windows Forms in Visual Studio con C\#

In questa breve introduzione all'ambiente Visual Studio sviluppo integrato (IDE) verrà creata una semplice applicazione C# con un'interfaccia utente basata su Windows.

::: moniker range="vs-2017"

Se non è già stato installato Visual Studio, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se non è già stato installato Visual Studio, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

> [!NOTE]
> Alcune delle schermate contenute in questa esercitazione usano il tema scuro. Per passare al tema scuro, qualora questo non fosse già in uso, vedere le informazioni disponibili nella pagina [Personalizzare l'IDE e l'editor di Visual Studio](../ide/quickstart-personalize-the-ide.md).

::: moniker-end

::: moniker range="vs-2022"

Se non è già stato installato Visual Studio, passare alla pagina di download di [Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) per installarlo gratuitamente.

> [!NOTE]
> Alcune delle schermate contenute in questa esercitazione usano il tema scuro. Per passare al tema scuro, qualora questo non fosse già in uso, vedere le informazioni disponibili nella pagina [Personalizzare l'IDE e l'editor di Visual Studio](../ide/quickstart-personalize-the-ide.md).

::: moniker-end

## <a name="create-a-project"></a>Creare un progetto

Per prima cosa si crea un progetto di applicazione C#. Il tipo di progetto include fin dall'inizio tutti i file modello necessari.

::: moniker range="vs-2017"

1. Aprire Visual Studio 2017.

1. Nella barra dei menu superiore scegliere **File** > **nuovo** > **Project**.

1. Nella finestra **di dialogo Nuovo Project** nel riquadro sinistro espandere Visual **C#** e quindi scegliere **Windows Desktop**. Nel riquadro centrale scegliere il modello **App Windows Forms (.NET Framework)**. Assegnare al file il nome `HelloWorld`.

     Se non viene visualizzato il modello del progetto **App Windows Forms (.NET Framework)**, chiudere la finestra di dialogo **Nuovo progetto** e nella barra dei menu superiore scegliere **Strumenti** > **Ottieni strumenti e funzionalità**. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo per desktop .NET**, quindi scegliere **Modifica**.

     ![Carico di lavoro Sviluppo per desktop .NET nel programma di installazione di Visual Studio](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. Aprire Visual Studio.

1. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

   ![Visualizzare la finestra Crea un nuovo progetto](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Nella finestra **Crea un nuovo progetto** scegliere il modello Windows Forms App **(.NET Framework)** per C#.

   Se si preferisce, è possibile perfezionare la ricerca per ottenere rapidamente il modello desiderato. Ad esempio, immettere o digitare *Windows Forms App* nella casella di ricerca. Scegliere quindi **C# dall'elenco** Linguaggio e quindi **scegliere** Windows dall'elenco Piattaforma.  

   ![Scegliere il modello C# per l'app Windows Forms (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-winforms-project-nonfiltered.png)

   > [!NOTE]
   > Se il modello **App Windows Forms (.NET Core)** non viene visualizzato, è possibile installarlo dalla finestra **Crea un nuovo progetto**. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**.
   >
   > ![Collegamento "Installa altri strumenti e funzionalità" nel messaggio "L'elemento cercato non è stato trovato?" nella finestra "Crea un nuovo progetto"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Nella finestra di dialogo Programma di installazione di Visual Studio scegliere il carico di **lavoro Sviluppo di desktop .NET.**
   >
   > ![Carico di lavoro Sviluppo per desktop .NET nel programma di installazione di Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Successivamente, scegliere il pulsante **Modifica** nel programma di installazione di Visual Studio. Quando viene richiesto, salvare il lavoro. Scegliere quindi **Continua** per installare il carico di lavoro. Quindi tornare al passaggio 2 della procedura [Creare un progetto](#create-a-project)".

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *HelloWorld* nella casella **Nome del progetto**. Scegliere quindi **Crea**.

   ![Nella finestra Configura il nuovo progetto assegnare al progetto il nome "HelloWorld"](../get-started/csharp/media/vs-2019/csharp-name-your-winform-project-helloworld.png)

   Visual Studio aprirà il nuovo progetto.

::: moniker-end

## <a name="create-the-application"></a>Creare l'applicazione

Dopo aver selezionato il modello di progetto C# e aver assegnare un nome al file, Visual Studio un modulo. Un modulo è un'interfaccia utente di Windows. Si creerà un'applicazione "Hello World" aggiungendo controlli al form e quindi si eseguirà l'app.

### <a name="add-a-button-to-the-form"></a>Aggiungere un pulsante al modulo

1. Scegliere **Casella degli strumenti** per aprire la finestra a comparsa della casella degli strumenti.

     ![Scegliere la casella degli strumenti per aprire la finestra Casella degli strumenti](../ide/media/csharp-toolbox-toolwindow.png)

     Se l'opzione a  comparsa Casella degli strumenti non è visualizzata, è possibile aprirla dalla barra dei menu. A tale scopo, visualizzare **casella**  >  **degli strumenti**. In caso contrario, **premere** + **CTRL** + **ALT+X.**

1. Scegliere **l'icona Aggiungi** per ancorare la **finestra casella degli** strumenti.

     ![Scegliere l'icona Aggiungi per aggiungere la finestra Casella degli strumenti all'IDE](../ide/media/vb-pin-the-toolbox-window.png)

1. Scegliere il **controllo** Pulsante e trascinarlo nel form.

     ![Aggiungere un pulsante al modulo](../ide/media/csharp-add-button-form1.png)

1. Nella finestra **Proprietà** individuare **Testo**, modificare il nome da **Button1** a `Click this` e quindi premere **INVIO.**

     ![Aggiungere testo al pulsante nel modulo](../ide/media/vb-button-control-text.png)

     (Se la finestra **Proprietà** non viene visualizzata, è possibile aprirla dalla barra dei menu. A tale scopo, scegliere **Visualizza**  >  **finestra Proprietà**. In caso contrario, **premere F4.**

1. Nella sezione **Progettazione** della finestra **Proprietà** cambiare il nome da **Button1** a `btnClickThis`, quindi premere **INVIO**.

     ![Aggiungere una funzione al pulsante nel modulo](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > Se l'elenco è stato  alfabetico nella finestra Proprietà, **Button1** viene invece visualizzato nella sezione **(DataBindings).**

### <a name="add-a-label-to-the-form"></a>Aggiungere un'etichetta al modulo

È stato aggiunto un controllo pulsante per creare un'azione. Ora si aggiungerà un controllo etichetta al quale inviare del testo.

1. Selezionare il **controllo Etichetta** dalla finestra **Casella degli** strumenti e trascinarlo nel form e rilasciarlo sotto il pulsante Fare clic su **questo** pulsante.

1. Nella sezione **Progettazione** o **(DataBindings)** della  finestra Proprietà modificare il nome di **Label1** in `lblHelloWorld` e quindi premere **INVIO.**

### <a name="add-code-to-the-form"></a>Aggiungere codice al modulo

1. Nella finestra **Form1.cs &#91;Progettazione&#93;** fare doppio clic  sul pulsante Fare clic su questo pulsante per aprire la **finestra Form1.cs.**

      In alternativa, è possibile espandere **Form1.cs** in **Esplora soluzioni** e quindi scegliere **Form1.**

1. Nella finestra **Form1.cs,** dopo la **riga void privata,** digitare o immettere `lblHelloWorld.Text = "Hello World!";` come illustrato nello screenshot seguente:

     ![Aggiungere codice al modulo](../get-started/csharp/media/csharp-winforms-add-code.png)

## <a name="run-the-application"></a>Eseguire l'applicazione

1. Scegliere il **pulsante Avvia** per eseguire l'applicazione.

     ![Scegliere Avvia per eseguire il debug e l'esecuzione dell'app](../ide/media/vb-click-start-hello-world.png)

   Vengono eseguite diverse operazioni. Nell'IDE di Visual Studio viene aperta la finestra **Strumenti di diagnostica** e anche una finestra **Output**. All'esterno dell'IDE viene visualizzata una finestra di dialogo **Form1**. La finestra include il pulsante **Click this** e il testo **Label1**.

1. Scegliere il **pulsante Fare clic** su questo pulsante nella finestra di dialogo **Form1** . Osservare che il testo **Label1** diventa **Hello World!**.

    ![Finestra di dialogo Form1 con il testo Label1 ](../ide/media/vb-form1-dialog-hello-world.png)

1. Chiudere la **finestra di dialogo Form1** per arrestare l'esecuzione dell'app.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni, passare all'esercitazione successiva:

> [!div class="nextstepaction"]
> [Esercitazione: Creare un visualizzatore di immagini](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Vedi anche

* [Altre esercitazioni su C#](../get-started/csharp/index.yml)
* [Visual Basic esercitazioni](../get-started/visual-basic/index.yml)
* [Esercitazioni su C++](/cpp/get-started/tutorial-console-cpp)