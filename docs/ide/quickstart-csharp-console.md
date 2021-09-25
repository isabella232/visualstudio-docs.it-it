---
title: "Esercitazione: Creare un'app console C# con Visual Studio"
titleSuffix: ''
description: Informazioni dettagliate su come creare un'app console Hello World semplice in Visual Studio con C#.
ms.custom: vs-acquisition
ms.date: 09/14/2021
ms.topic: quickstart
ms.devlang: vb
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 99a2e2e6ba67d4604b945f61040005f13320fd7b
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128431916"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-c-console-app"></a>Guida introduttiva: Usare Visual Studio per creare la prima app console C#

In questa introduzione di 5-10 minuti all'ambiente di sviluppo integrato (IDE) di Visual Studio si creerà una semplice app C# eseguita nella console.

::: moniker range="vs-2017"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range=">=vs-2019"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

## <a name="create-a-project"></a>Creare un progetto

Per prima cosa si crea un progetto di applicazione C#. Il tipo di progetto include fin dall'inizio tutti i file modello necessari.

::: moniker range="vs-2017"

1. Aprire Visual Studio 2017.

1. Nella barra dei menu superiore scegliere **File** > **Nuovo** > **Project**.

1. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **C#** e quindi scegliere **.NET Core**. Nel riquadro centrale scegliere **Console App (.NET Core)** (App console (.NET Core)). Quindi assegnare al progetto il nome *HelloWorld*.

   ![Screenshot del modello di progetto App console (.NET Core) nella finestra di dialogo Nuovo Project nell'IDE Visual Studio.](../ide/media/new-project-csharp-dotnetcore-helloworld-console-app.png)

     Se non viene visualizzato il modello di progetto **Applicazione console (.NET Core)**, fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro a sinistra della finestra di dialogo **Nuovo progetto**.

   ![Screenshot del collegamento "Apri Programma di installazione di Visual Studio" dalla finestra di dialogo Project nuova cartella.](../ide/media/csharp-open-visual-studio-installer-hello-world.png)

     Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo multipiattaforma .NET Core**, quindi scegliere **Modifica**.

     ![Screenshot del carico di lavoro Sviluppo multipiattaforma .NET Core nel Programma di installazione di Visual Studio.](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

1. Aprire Visual Studio.

1. Nella finestra iniziale scegliere **Crea un nuovo progetto.**

   ![Screenshot della finestra "Crea un nuovo progetto".](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Nella finestra **Crea un nuovo progetto** immettere o digitare *console* nella casella di ricerca. Scegliere quindi **C#** dall'elenco Linguaggio e **Windows** dall'elenco Piattaforma. 

   Dopo aver applicato i filtri di linguaggio e piattaforma, scegliere il modello **App console (.NET Core)** e **Avanti**.

   ![Screenshot del modello C# per l'app console (.NET Framework).](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Se il modello **App console (.NET Core)** non viene visualizzato, è possibile installarlo dalla finestra **Crea un nuovo progetto**. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**.
   >
   > ![Screenshot del collegamento "Installa altri strumenti e funzionalità" dal messaggio "Impossibile trovare ciò che si sta cercando" nella finestra "Crea nuovo progetto".](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Scegliere quindi il carico di lavoro **Sviluppo multipiattaforma .NET Core** nel programma di installazione di Visual Studio.
   >
   > ![Screenshot del carico di lavoro Sviluppo multipiattaforma .NET Core nel Programma di installazione di Visual Studio.](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Successivamente, scegliere il pulsante **Modifica** nel programma di installazione di Visual Studio. Quando viene richiesto, salvare il lavoro. Scegliere quindi **Continua** per installare il carico di lavoro. Quindi tornare al passaggio 2 della procedura [Creare un progetto](#create-a-project)".

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *HelloWorld* nella casella **Nome del progetto**. Scegliere quindi **Crea.**

   ![Screenshot della finestra "Configura il nuovo progetto" con il nome "HelloWorld" per il progetto.](../get-started/csharp/media/vs-2019/csharp-name-your-helloworld-project.png)

   Visual Studio aprirà il nuovo progetto.

::: moniker-end

::: moniker range=">=vs-2022"

1. Aprire Visual Studio.

1. Nella finestra iniziale scegliere **Crea un nuovo progetto.**

   ![Screenshot della finestra "Crea un nuovo progetto" in Visual Studio 2022.](media/vs-2022/start-window-create-new-project.png)

1. Nella finestra **Crea un nuovo progetto** immettere o digitare *console* nella casella di ricerca. Scegliere quindi **C#** dall'elenco Linguaggio e **Windows** dall'elenco Piattaforma. 

   Dopo aver applicato i filtri per la lingua e la piattaforma, scegliere il **modello Applicazione** console e quindi scegliere **Avanti.**

   ![Screenshot del modello C# per l'app console (.NET Core).](media/vs-2022/quickstart-csharp-create-new-project.png)

   > [!NOTE]
   > Se il modello Applicazione **console** per .NET Core non è visualizzato, è possibile installarlo dalla finestra Crea **un nuovo** progetto:
   > - Nel messaggio Non si è trovato ciò che  si sta **cercando?** scegliere il collegamento Installa altri strumenti e funzionalità per avviare il Programma di installazione di Visual Studio.
   >
   >    ![Screenshot del collegamento "Installa altri strumenti e funzionalità" dal messaggio "Impossibile trovare ciò che si sta cercando" nella finestra "Crea nuovo progetto".](media/vs-2022/not-finding-what-looking-for.png)
   > 
   > - Nel programma di installazione di Visual Studio:
   >   - Scegliere il **carico di lavoro Sviluppo per desktop .NET.**
   >
   >      ![Screenshot del carico di lavoro Sviluppo multipiattaforma .NET Core nel Programma di installazione di Visual Studio.](media/vs-2022/dot-net-core-desktop-dev-workload.png)
   >
   >   - Fare clic sul pulsante **Modifica**. Quando viene richiesto, salvare il lavoro. 
   >   - Scegliere **Continua per** installare il carico di lavoro.
   > - Tornare al passaggio 2 della procedura["Creare un progetto".](#create-a-project)

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *HelloWorld* nella casella **Nome del progetto**. Scegliere quindi **Avanti.**

   ![Screenshot della finestra "Configura il nuovo progetto" in Visual Studio 2022 con il nome del progetto impostato su "HelloWorld".](media/vs-2022/csharp-name-your-helloworld-project.png)

1. Nella finestra **Informazioni aggiuntive** verificare che **.NET 6.0 (anteprima)** sia selezionato nel menu a discesa **Framework** e quindi scegliere **Crea.**

   ![Screenshot della finestra "Informazioni aggiuntive" in Visual Studio 2022 con Framework impostato su '.NET 6.0 (anteprima)'.](media/vs-2022/create-project-additional-info.png)

   Visual Studio aprirà il nuovo progetto.
   
::: moniker-end

## <a name="create-the-application"></a>Creare l'applicazione

::: moniker range="vs-2017"

Dopo la selezione del modello di progetto C# e l'assegnazione di un nome al progetto, in Visual Studio viene creata una semplice applicazione "Hello World".

::: moniker-end

::: moniker range="vs-2019"

Visual Studio inserisce il codice di "Hello World" predefinito nel progetto.

::: moniker-end

::: moniker range=">=vs-2022"

Visual Studio inserisce il codice di "Hello World" predefinito nel progetto. Per visualizzarlo nell'editor, selezionare il file di codice *Program.cs* nella finestra Esplora soluzioni, che in genere si trova sul lato destro del Visual Studio.

::: moniker-end

::: moniker range="<=vs-2019"

A tale scopo, chiama il metodo <xref:System.Console.WriteLine%2A> per visualizzare la stringa letterale "Hello World!" nella finestra della console.

   ![Screenshot del codice Hello World predefinito dal modello.](../ide/media/csharp-console-helloworld-template.png)

Se si preme **F5** è possibile eseguire il programma in modalità di debug. La finestra della console resta comunque visibile per un istante, quindi viene chiusa.

Ciò accade perché il metodo `Main` termina dopo l'esecuzione dell'unica istruzione, quindi l'applicazione viene chiusa.

::: moniker-end

::: moniker range=">=vs-2022"

La singola istruzione di codice chiama <xref:System.Console.WriteLine%2A> il metodo per visualizzare la stringa letterale "Hello, World!" nella finestra della console.

   ![Screenshot del codice Hello World predefinito dal modello.](media/vs-2022/csharp-console-helloworld-template.png)

Se si preme **F5** è possibile eseguire il programma in modalità di debug. Dopo l'esecuzione dell'applicazione nel debugger, la finestra della console rimane aperta. Tuttavia, se l'applicazione viene eseguita all'esterno del debugger, la finestra della console è visibile solo per un istante prima della chiusura. Questo perché il metodo `Main` termina dopo l'esecuzione della singola istruzione di codice e quindi l'applicazione termina. Per altre informazioni sull'esecuzione di un'applicazione console all'esterno del debugger, vedere [Pubblicare un'applicazione console .NET.](/dotnet/core/tutorials/publishing-with-visual-studio)

> [!NOTE]
> La singola riga di codice nell'editor è un'istruzione di primo livello [C#](/dotnet/csharp/whats-new/csharp-9#top-level-statements)ed è una semplificazione del metodo [Main](/dotnet/csharp/fundamentals/program-structure/main-command-line) boilerplate.

::: moniker-end

### <a name="add-some-code"></a>Aggiungere codice

::: moniker range="<=vs-2019"

È possibile aggiungere codice per sospendere l'applicazione in modo che la finestra della console non venga chiusa fino a quando non si preme **INVIO**.

1. Aggiungere il codice seguente subito dopo la chiamata al metodo <xref:System.Console.WriteLine%2A>:

   ```csharp
   Console.ReadLine();
   ```

1. Verificare che il codice sia simile al seguente nell'editor del codice:

   ![Screenshot del codice appena aggiunto per sospendere l'Hello World app.](../ide/media/csharp-console-helloworld-add-code.png)

::: moniker-end

::: moniker range=">=vs-2022"

Aggiungere il codice per sospendere l'applicazione in modo che il metodo non termini `main` fino a quando non si preme **INVIO.**

1. Aggiungere il codice seguente subito dopo la chiamata al metodo <xref:System.Console.WriteLine%2A>:

   ```csharp
   Console.ReadLine();
   ```

1. Verificare che il codice sia simile al seguente nell'editor del codice:

   ![Screenshot del codice appena aggiunto per sospendere l'Hello World app.](media/vs-2022/csharp-console-helloworld-add-code.png)

::: moniker-end

## <a name="run-the-application"></a>Eseguire l'applicazione

::: moniker range="<=vs-2019"

1. Fare clic sul pulsante **HelloWorld** sulla barra degli strumenti per eseguire l'applicazione in modalità di debug. In caso contrario, è possibile **premere F5.**

   ![Screenshot del pulsante Hello World che esegue l'app dalla barra degli strumenti.](../ide/media/csharp-console-hello-world-button.png)

1. Visualizzare l'app nella finestra della console.

   ![Screenshot della finestra della console che mostra il messaggio "Hello World!" il messaggio "Hello World!".](../ide/media/csharp-console-hello-world.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. Fare clic sul pulsante **HelloWorld** sulla barra degli strumenti per eseguire l'applicazione in modalità di debug. In caso contrario, è possibile **premere F5.**

   ![Screenshot del pulsante Hello World che esegue l'app dalla barra degli strumenti.](media/vs-2022/csharp-console-hello-world-button.png)

1. Visualizzare l'app nella finestra della console.

   ![Screenshot della finestra della console che mostra il messaggio "Hello, World!". il messaggio "Hello World!".](media/vs-2022/csharp-console-hello-world.png)

::: moniker-end

### <a name="close-the-application"></a>Chiudere l'applicazione

::: moniker range="<=vs-2019"

1. Premere **INVIO** per chiudere la finestra della console.

1. Chiudere il riquadro **Output** in Visual Studio.

   ![Screenshot del riquadro Output in Visual Studio.](../ide/media/csharp-hello-world-close-output-pane.png)

1. Chiudere Visual Studio.

::: moniker-end

::: moniker range=">=vs-2022"

1. Premere **INVIO** per terminare `main` il metodo e quindi premere di nuovo **INVIO** per chiudere la finestra della console.

1. Chiudere il riquadro **Output** in Visual Studio.

   ![Screenshot del riquadro Output in Visual Studio 2022.](media/vs-2022/csharp-hello-world-close-output-pane.png)

1. Chiudere Visual Studio.

::: moniker-end

## <a name="next-steps"></a>Passaggi successivi

La guida introduttiva è stata completata. Ci auguriamo che sia stata utile per l'apprendimento dell'uso di C# e dell'IDE di Visual Studio. Per altre informazioni, continuare con le esercitazioni seguenti.

> [!div class="nextstepaction"]
> [Introduzione a un'app console C# in Visual Studio](../get-started/csharp/tutorial-console.md)
