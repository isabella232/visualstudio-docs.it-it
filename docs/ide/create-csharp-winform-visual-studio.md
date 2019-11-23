---
title: Creare un'app Windows Forms conC#
description: Informazioni dettagliate su come creare un'app Windows Forms in Visual Studio C#con.
ms.date: 09/26/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 4017ee2da040ccef36c58b17d896abab199c3517
ms.sourcegitcommit: 13decf878b33fc0c5d665a88067170c2861b261b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/30/2019
ms.locfileid: "71682144"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-c"></a>Creare un'app Windows Forms in Visual Studio conC#

In questa breve introduzione a Visual Studio Integrated Development Environment (IDE) verrà creata una semplice C# applicazione con interfaccia utente basata su Windows.

::: moniker range="vs-2017"

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

> [!NOTE]
> Alcune delle schermate contenute in questa esercitazione usano il tema scuro. Per passare al tema scuro, qualora questo non fosse già in uso, vedere le informazioni disponibili nella pagina [Personalizzare l'IDE e l'editor di Visual Studio](../ide/quickstart-personalize-the-ide.md).

::: moniker-end

## <a name="create-a-project"></a>Creare un progetto

Per prima cosa si crea un progetto di applicazione C#. Il tipo di progetto include fin dall'inizio tutti i file modello necessari.

::: moniker range="vs-2017"

1. Aprire Visual Studio 2017.

1. Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**.

1. Nella finestra di dialogo **nuovo progetto** nel riquadro sinistro espandere oggetto **C#visivo**, quindi scegliere desktop di **Windows**. Nel riquadro centrale scegliere il modello **App Windows Forms (.NET Framework)** . Assegnare al file il nome `HelloWorld`.

     Se non viene visualizzato il modello del progetto **App Windows Forms (.NET Framework)** , chiudere la finestra di dialogo **Nuovo progetto** e nella barra dei menu superiore scegliere **Strumenti** > **Ottieni strumenti e funzionalità**. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo per desktop .NET**, quindi scegliere **Modifica**.

     ![Carico di lavoro Sviluppo per desktop .NET nel programma di installazione di Visual Studio](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. Aprire Visual Studio 2019.

1. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

   ![Visualizzare la finestra Crea un nuovo progetto](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Nella finestra **Crea un nuovo progetto** scegliere il modello **App Windows Forms (.NET Framework)** per C#.

   Se si preferisce, è possibile affinare la ricerca per ottenere rapidamente il modello desiderato. Ad esempio, immettere o digitare *Windows Forms app* nella casella di ricerca. Scegliere **C#** quindi dall'elenco lingua, quindi scegliere **Windows** dall'elenco piattaforma.  

   ![Scegliere il C# modello per l'app Windows Forms (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-winforms-project-nonfiltered.png)

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

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *HelloWorld* nella casella **Nome del progetto**. Scegliere **Crea**.

   ![Nella finestra Configura il nuovo progetto assegnare al progetto il nome "HelloWorld"](../get-started/csharp/media/vs-2019/csharp-name-your-winform-project-helloworld.png)

   Visual Studio aprirà il nuovo progetto.

::: moniker-end

## <a name="create-the-application"></a>Creare l'applicazione

Dopo aver selezionato il C# modello di progetto e denominato il file, Visual Studio apre un modulo per l'utente. Un modulo è un'interfaccia utente di Windows. Verrà creata un'applicazione "Hello World" aggiungendo i controlli al modulo e quindi verrà eseguita l'app.

### <a name="add-a-button-to-the-form"></a>Aggiungere un pulsante al modulo

1. Scegliere **Casella degli strumenti** per aprire la finestra a comparsa della casella degli strumenti.

     ![Scegliere la casella degli strumenti per aprire la finestra casella degli strumenti](../ide/media/csharp-toolbox-toolwindow.png)

     (Se l'opzione di apertura a comparsa della **Casella degli strumenti** non viene visualizzata, è possibile aprirla dalla barra dei menu. A tale scopo, **visualizzare** > **casella degli strumenti**. In alternativa, premere **CTRL**+**ALT**+**X**.)

1. Scegliere l'icona **Aggiungi** per ancorare la finestra **casella degli strumenti** .

     ![Scegliere l'icona Aggiungi per aggiungere la finestra casella degli strumenti all'IDE](../ide/media/vb-pin-the-toolbox-window.png)

1. Scegliere il controllo **Button** , quindi trascinarlo sul form.

     ![Aggiungere un pulsante al modulo](../ide/media/csharp-add-button-form1.png)

1. Nella finestra **Proprietà** individuare il **testo**, modificare il nome da **Button1** a `Click this`e quindi premere **invio**.

     ![Aggiungere testo al pulsante nel modulo](../ide/media/vb-button-control-text.png)

     (Se la finestra **Proprietà** non viene visualizzata, è possibile aprirla dalla barra dei menu. A tale scopo, scegliere **visualizza** > **finestra Proprietà**. In alternativa premere **F4**.)

1. Nella sezione **Progettazione** della finestra **Proprietà** cambiare il nome da **Button1** a `btnClickThis`, quindi premere **INVIO**.

     ![Aggiungere una funzione al pulsante nel modulo](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > Se l'elenco è stato in ordine alfabetico nella finestra **Proprietà** , **Button1** viene visualizzato nella sezione **(DataBindings)** .

### <a name="add-a-label-to-the-form"></a>Aggiungere un'etichetta al modulo

È stato aggiunto un controllo pulsante per creare un'azione. Ora si aggiungerà un controllo etichetta al quale inviare del testo.

1. Selezionare il controllo **Etichetta** nella **Casella degli strumenti**, quindi trascinarlo sul modulo e rilasciarlo sotto il pulsante **Click this**.

1. Nella sezione **progettazione** o nella sezione **(DataBindings)** della finestra **proprietà** modificare il nome di **Label1** in `lblHelloWorld`, quindi premere **invio**.

### <a name="add-code-to-the-form"></a>Aggiungere codice al modulo

1. Nella finestra **di &#91;progettazione&#93; di Form1.cs** fare doppio clic su **questo** pulsante per aprire la finestra di **Form1.cs** .

      In alternativa, è possibile espandere **Form1.cs** in **Esplora soluzioni**, quindi scegliere **Form1**.

1. Nella finestra **Form1.cs** , dopo la riga **privata void** , digitare o immettere `lblHelloWorld.Text = "Hello World!";` come illustrato nello screenshot seguente:

     ![Aggiungere codice al modulo](../get-started/csharp/media/csharp-winforms-add-code.png)

## <a name="run-the-application"></a>Esecuzione dell'applicazione

1. Per eseguire l'applicazione, scegliere il pulsante **Avvia** .

     ![Scegliere Avvia per eseguire il debug ed eseguire l'app](../ide/media/vb-click-start-hello-world.png)

   Vengono eseguite diverse operazioni. Nell'IDE di Visual Studio viene aperta la finestra **Strumenti di diagnostica** e anche una finestra **Output**. All'esterno dell'IDE viene visualizzata una finestra di dialogo **Form1**. La finestra include il pulsante **Click this** e il testo **Label1**.

1. Scegliere il pulsante **fare clic su questo** pulsante nella finestra di dialogo **Form1** . Osservare che il testo **Label1** diventa **Hello World!** .

    ![Finestra di dialogo Form1 con il testo Label1 ](../ide/media/vb-form1-dialog-hello-world.png)

1. Chiudere la finestra di dialogo **Form1** per arrestare l'esecuzione dell'app.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni, continuare con l'esercitazione seguente:

> [!div class="nextstepaction"]
> [Esercitazione: creare un visualizzatore di immagini](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Vedere anche

* [Altre C# esercitazioni](/visualstudio/get-started/csharp/)
* [Esercitazioni Visual Basic](/visualstudio/get-started/visual-basic/)
* [C++esercitazioni](/cpp/get-started/tutorial-console-cpp)
