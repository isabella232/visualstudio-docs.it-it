---
title: 'Esercitazione: Introduzione a Visual Basic'
description: Informazioni dettagliate su come creare un'app console Visual Basic in Visual Studio.
ms.custom: seodec18, get-started
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 899c47154a3d55811579ff01786096f35272593a
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/30/2019
ms.locfileid: "70180426"
---
# <a name="tutorial-get-started-with-visual-basic-in-visual-studio"></a>Esercitazione: Introduzione a Visual Basic in Visual Studio

In questa esercitazione per Visual Basic (VB) si userà Visual Studio per creare ed eseguire diverse app console e nel frattempo si esploreranno alcune funzionalità dell'[ambiente di sviluppo integrato, ovvero IDE, Integrated Development Environment, di Visual Studio](visual-studio-ide.md).

::: moniker range="vs-2017"

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

## <a name="create-a-project"></a>Creare un progetto

In primo luogo si creerà un progetto di applicazione Visual Basic. Il tipo di progetto include fin dall'inizio tutti i file modello necessari.

::: moniker range="vs-2017"

1. Aprire Visual Studio 2017.

2. Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**.

3. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **Visual Basic**, quindi selezionare **.NET Core**. Nel riquadro centrale scegliere **Console App (.NET Core)** (App console (.NET Core)). Quindi assegnare al file il nome *HelloWorld*.

   ![Modello di progetto Console App (.NET Core) nella finestra di dialogo Nuovo progetto dell'IDE di Visual Studio](media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

### <a name="add-a-workload-optional"></a>Aggiungere un carico di lavoro (facoltativo)

Se il modello di progetto **Console App (.NET Core)** non è visualizzato, è possibile ottenerlo aggiungendo il carico di lavoro **Sviluppo multipiattaforma .NET Core**. È possibile aggiungere questo carico di lavoro in uno dei due modi seguenti, a seconda degli aggiornamenti di Visual Studio 2017 installati nel computer.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Opzione 1: usare la finestra di dialogo Nuovo progetto

1. Fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro a sinistra della finestra di dialogo **Nuovo progetto**.

   ![Fare clic sul collegamento Apri il programma di installazione di Visual Studio nella finestra di dialogo Nuovo progetto](../media/vs-open-visual-studio-installer-generic.png)

1. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo multipiattaforma .NET Core**, quindi scegliere **Modifica**.

   ![Carico di lavoro Sviluppo multipiattaforma .NET Core nel programma di installazione di Visual Studio](../media/tutorial-aspnet-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Opzione 2: usare la barra del menu Strumenti

1. Chiudere la finestra di dialogo **Nuovo progetto** e nella barra dei menu in alto scegliere **Strumenti** > **Ottieni strumenti e funzionalità**.

1. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo multipiattaforma .NET Core**, quindi scegliere **Modifica**.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Alcune delle schermate contenute in questa esercitazione usano il tema scuro. Per passare al tema scuro, qualora questo non fosse già in uso, vedere le informazioni disponibili nella pagina [Personalizzare l'IDE e l'editor di Visual Studio](../../ide/quickstart-personalize-the-ide.md).

1. Aprire Visual Studio 2019.

1. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

   ![Visualizzare la finestra "Crea un nuovo progetto"](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Nella finestra **Crea un nuovo progetto** immettere o digitare *console* nella casella di ricerca. Quindi scegliere **Visual Basic** dall'elenco Linguaggio e **Windows** dall'elenco Piattaforma. 

   Dopo aver applicato i filtri di linguaggio e piattaforma, scegliere il modello **App console (.NET Core)** e **Avanti**.

   ![Scegliere il modello Visual Basic per l'app console (.NET Framework)](./media/vs-2019/vb-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Se il modello **App console (.NET Core)** non viene visualizzato, è possibile installarlo dalla finestra **Crea un nuovo progetto**. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**.
   >
   > ![Collegamento "Installa altri strumenti e funzionalità" nel messaggio "L'elemento cercato non è stato trovato?" nella finestra "Crea un nuovo progetto"](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Scegliere quindi il carico di lavoro **Sviluppo multipiattaforma .NET Core** nel programma di installazione di Visual Studio.
   >
   > ![Carico di lavoro Sviluppo multipiattaforma .NET Core nel programma di installazione di Visual Studio](../../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Scegliere quindi il pulsante **Modifica** nel programma di installazione di Visual Studio. Quando viene richiesto, salvare il lavoro. Scegliere quindi **Continua** per installare il carico di lavoro. Quindi tornare al passaggio 2 della procedura [Creare un progetto](#create-a-project)".

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *WhatIsYourName* nella casella **Nome del progetto**. Scegliere **Crea**.

   ![Nella finestra Configura il nuovo progetto assegnare al progetto il nome "WhatIsYourName"](./media/vs-2019/vb-name-your-project-whatname.png)

   Visual Studio aprirà il nuovo progetto.

::: moniker-end

## <a name="create-a-what-is-your-name-application"></a>Creare un'applicazione "What Is Your Name?"

Verrà ora creata un'applicazione che chiede all'utente di immettere il proprio nome, che viene quindi visualizzato insieme alla data e all'ora. Ecco come:

 ::: moniker range="vs-2017"

1. Se non è già aperto, aprire il progetto *WhatIsYourName*.

1. Immettere il codice Visual Basic seguente immediatamente dopo la parentesi di apertura che segue la riga `Sub Main(args As String())` e prima della riga `End Sub`:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Questo codice sostituisce le istruzioni <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> e <xref:System.Console.ReadKey%2A> esistenti.

   ![Finestra del codice con il codice di "What Is Your Name?"](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. Quando la finestra della console si apre, immettere il proprio nome. La finestra della console dovrebbe avere un aspetto simile allo screenshot seguente:

   ![Finestra della console con "What is your name?", la data, l'ora della console e il messaggio Premere un tasto per continuare](media/vb-console-what-name.png)

1. Premere un tasto qualsiasi per chiudere la finestra della console.

::: moniker-end

::: moniker range="vs-2019"

1. Nel progetto *WhatIsYourName* immettere il codice Visual Basic seguente immediatamente dopo la parentesi quadra di apertura che segue la riga `Sub Main(args As String())` e prima della riga `End Sub`:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Questo codice sostituisce le istruzioni <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> e <xref:System.Console.ReadKey%2A> esistenti.

   ![Finestra del codice con il codice di "What Is Your Name?"](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. Quando la finestra della console si apre, immettere il proprio nome. La finestra della console dovrebbe avere un aspetto simile allo screenshot seguente:

   ![Finestra della console con "What is your name?", la data, l'ora della console e il messaggio Premere un tasto per continuare](media/vb-console-what-name.png)

1. Premere un tasto qualsiasi per chiudere la finestra della console.

 ::: moniker-end

## <a name="create-a-calculate-this-application"></a>Creare un'applicazione "CalculateThis"

::: moniker range="vs-2017"

1. Aprire Visual Studio 2017, quindi scegliere **File** > **Nuovo** > **Progetto** nella barra dei menu in alto.

1. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **Visual Basic**, quindi selezionare **.NET Core**. Nel riquadro centrale scegliere **Console App (.NET Core)** (App console (.NET Core)). Quindi assegnare al file il nome *CalculateThis*.

1. Immettere il codice seguente tra la riga `Module Program` e la riga `End Module`:

   ```vb
   Public num1 As Integer
   Public num2 As Integer
   Public answer As Integer
   Sub Main()
       Console.WriteLine("Type a number and press Enter")
       num1 = Console.ReadLine()
       Console.WriteLine("Type another number to add to it and press Enter")
       num2 = Console.ReadLine()
       answer = num1 + num2
       Console.WriteLine("The answer is " & answer)
       Console.ReadLine()
   End Sub
   ```

   La finestra del codice dovrebbe avere un aspetto analogo allo screenshot seguente:

   ![Finestra del codice che illustra il codice di CalculateThis](media/vb-codewindow-calculate-this.png)

1. Fare clic su **CalculateThis** per eseguire il programma. La finestra della console dovrebbe avere un aspetto simile allo screenshot seguente:

    ![Finestra della console che illustra l'app CalculateThis con le azioni possibili.](media/vb-console-calculate-this.png)

::: moniker-end 

::: moniker range="vs-2019"

1. Nella finestra iniziale scegliere **Crea un nuovo progetto**. 

1. Nella finestra **Crea un nuovo progetto** immettere o digitare *console* nella casella di ricerca. Quindi scegliere **Visual Basic** dall'elenco Linguaggio e **Windows** dall'elenco Piattaforma. 

1. Dopo aver applicato i filtri di linguaggio e piattaforma, scegliere il modello **App console (.NET Core)** e **Avanti**.

   Nella finestra **Configura il nuovo progetto** digitare o immettere *WhatIsYourName* nella casella **Nome del progetto**. Quindi scegliere **Crea**.

1. Immettere il codice seguente tra la riga `Module Program` e la riga `End Module`:

   ```vb
   Public num1 As Integer
   Public num2 As Integer
   Public answer As Integer
   Sub Main()
       Console.WriteLine("Type a number and press Enter")
       num1 = Console.ReadLine()
       Console.WriteLine("Type another number to add to it and press Enter")
       num2 = Console.ReadLine()
       answer = num1 + num2
       Console.WriteLine("The answer is " & answer)
       Console.ReadLine()
   End Sub
   ```

   La finestra del codice dovrebbe avere un aspetto analogo allo screenshot seguente:

   ![Finestra del codice che illustra il codice di CalculateThis](media/vb-codewindow-calculate-this.png)

1. Fare clic su **CalculateThis** per eseguire il programma. La finestra della console dovrebbe avere un aspetto simile allo screenshot seguente:

    ![Finestra della console che illustra l'app CalculateThis con le azioni possibili.](media/vb-console-calculate-this.png)

::: moniker-end

## <a name="quick-answers-faq"></a>Domande frequenti con risposta rapida

Ecco una rapida serie di domande frequenti per evidenziare alcuni concetti chiave.

### <a name="what-is-visual-basic"></a>Che cos'è Visual Basic?

Visual Basic è un linguaggio di programmazione indipendente dai tipi progettato per garantire la massima facilità di apprendimento. Deriva dall'acronimo BASIC, che significa "Beginner's All-purpose Symbolic Instruction Code" (Codice di istruzioni simbolico multifunzione per principianti).

### <a name="what-is-visual-studio"></a>Che cos'è Visual Studio?

Visual Studio è una suite integrata per lo sviluppo di strumenti di produttività per gli sviluppatori. Si può immaginare Visual Studio come un programma utilizzabile per creare programmi e applicazioni.

### <a name="what-is-a-console-app"></a>Che cos'è un'app console?

Un'app console riceve input e visualizza output in una finestra della riga di comando, detta anche console.

### <a name="what-is-net-core"></a>Informazioni su .NET Core

.NET Core è il passaggio successivo nell'evoluzione di .NET Framework. Mentre .NET Framework consentiva di condividere codice tra linguaggi di programmazione diversi, .NET Core aggiunge la possibilità di condividere codice tra piattaforme diverse. E, ciliegina sulla torta, è open source. Sia .NET Framework che .NET Core includono librerie di funzionalità precompilate, nonché un Common Language Runtime (CLR) che svolge la funzione di macchina virtuale in cui eseguire il codice.

## <a name="next-steps"></a>Passaggi successivi

L'esercitazione è stata completata. Per altre informazioni, vedere l'esercitazione seguente.

> [!div class="nextstepaction"]
> [Compilare una libreria .NET Standard con Visual Basic e .NET Core SDK in Visual Studio 2017](/dotnet/core/tutorials/vb-library-with-visual-studio)

## <a name="see-also"></a>Vedere anche

* [Procedure dettagliate relative al linguaggio Visual Basic](/dotnet/visual-basic/walkthroughs)
* [Informazioni di riferimento per il linguaggio Visual Basic](/dotnet/visual-basic/language-reference/index)
* [IntelliSense per i file di codice di Visual Basic](../../ide/visual-basic-specific-intellisense.md)
