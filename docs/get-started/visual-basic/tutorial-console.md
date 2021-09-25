---
title: "Esercitazione: Introduzione all'Visual Basic"
description: Informazioni dettagliate su come creare un'app console Visual Basic in Visual Studio.
ms.custom: vs-acquisition,  get-started
ms.date: 09/14/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: vb
author: anandmeg
ms.author: meghaanand
manager: jmartens
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 2729900aa714e906a4dc32c2fa0d9a8985eb4d47
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128431531"
---
# <a name="tutorial-get-started-with-visual-basic-in-visual-studio"></a>Esercitazione: introduzione a Visual Basic in Visual Studio

In questa esercitazione per Visual Basic (VB) si userà Visual Studio per creare ed eseguire diverse app console e nel frattempo si esploreranno alcune funzionalità dell'[ambiente di sviluppo integrato, ovvero IDE, Integrated Development Environment, di Visual Studio](visual-studio-ide.md).

::: moniker range="vs-2017"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range=">=vs-2019"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

## <a name="create-a-project"></a>Creare un progetto

In primo luogo si creerà un progetto di applicazione Visual Basic. Il tipo di progetto include fin dall'inizio tutti i file modello necessari.

::: moniker range="vs-2017"

1. Aprire Visual Studio 2017.

2. Nella barra dei menu superiore scegliere **File** > **Nuovo** > **Project**.

3. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **Visual Basic**, quindi selezionare **.NET Core**. Nel riquadro centrale scegliere **Console App (.NET Core)** (App console (.NET Core)). Assegnare quindi al progetto *il nome WhatIsYourName*.

   ![Modello di progetto Console App (.NET Core) nella finestra di dialogo Nuovo progetto dell'IDE di Visual Studio](media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

### <a name="add-a-workload-optional"></a>Aggiungere un carico di lavoro (facoltativo)

Se il modello di progetto **Console App (.NET Core)** non è visualizzato, è possibile ottenerlo aggiungendo il carico di lavoro **Sviluppo multipiattaforma .NET Core**. È possibile aggiungere questo carico di lavoro in uno dei due modi seguenti, a seconda degli aggiornamenti di Visual Studio 2017 installati nel computer.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Opzione 1: usare la finestra di dialogo Nuovo progetto

1. Fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro a sinistra della finestra di dialogo **Nuovo progetto**.

   ![Fare clic sul collegamento Apri il programma di installazione di Visual Studio nella finestra di dialogo Nuovo progetto](../media/vs-open-visual-studio-installer-generic.png)

1. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo multipiattaforma .NET Core**, quindi scegliere **Modifica**.

   ![Carico di lavoro Sviluppo multipiattaforma .NET Core nel programma di installazione di Visual Studio](../media/tutorial-aspnet-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Opzione 2: usare la barra del menu Strumenti

1. Annullare dalla finestra **di dialogo Project** e dalla barra dei  menu superiore scegliere Strumenti Ottieni strumenti > **e funzionalità.**

1. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo multipiattaforma .NET Core**, quindi scegliere **Modifica**.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Alcune delle schermate contenute in questa esercitazione usano il tema scuro. Per passare al tema scuro, qualora questo non fosse già in uso, vedere le informazioni disponibili nella pagina [Personalizzare l'IDE e l'editor di Visual Studio](../../ide/quickstart-personalize-the-ide.md).

1. Aprire Visual Studio.

1. Nella finestra iniziale scegliere **Crea un nuovo progetto.**

   ![Screenshot che mostra la Visual Studio iniziale con l'opzione "Crea un nuovo progetto" selezionata.](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Nella finestra **Crea un nuovo progetto** scegliere Visual Basic dall'elenco Linguaggio.  Scegliere quindi **Windows** dall'elenco Piattaforma e **Console** dall'elenco dei tipi di progetto.

   Dopo aver applicato i filtri del linguaggio, della piattaforma e del tipo di progetto, scegliere il modello **Applicazione** console e quindi **scegliere Avanti.**

   :::image type="content" source="./media/vs-2019/vb-create-new-project-console-net-core.png" alt-text="Screenshot che mostra la finestra &quot;Crea un nuovo progetto&quot; con le opzioni &quot;Visual Basic&quot;, &quot;Windows&quot; e &quot;Console&quot; selezionate nei filtri Linguaggio, Piattaforma e Tipo Project e il modello di progetto Applicazione console selezionato.":::

   > [!NOTE]
   > Se il modello Applicazione **console** non viene visualizzato, è possibile installarlo dalla **finestra Crea un nuovo** progetto. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**.
   >
   > ![Screenshot che mostra il collegamento "Installa altri strumenti e funzionalità" dal messaggio "Non è stato trovato ciò che si sta cercando" nella finestra "Crea nuovo progetto".](../../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Scegliere quindi il carico di lavoro **Sviluppo multipiattaforma .NET Core** nel programma di installazione di Visual Studio.
   >
   > ![Screenshot che mostra il carico di lavoro Sviluppo multipiattaforma .NET Core nella Programma di installazione di Visual Studio.](../../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Successivamente, scegliere il pulsante **Modifica** nel programma di installazione di Visual Studio. Quando viene richiesto, salvare il lavoro. Scegliere quindi **Continua** per installare il carico di lavoro. Quindi tornare al passaggio 2 della procedura [Creare un progetto](#create-a-project)".

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *WhatIsYourName* nella casella **Nome del progetto**. Scegliere quindi **Avanti.**

   :::image type="content" source="./media/vs-2019/vb-name-your-project-whatname.png" alt-text="Screenshot che mostra la finestra &quot;Configure your new project&quot; (Configura il nuovo progetto) con il campo Project nome impostato su 'WhatIsYourName'.":::

1. Nella finestra **Informazioni aggiuntive** dovrebbe essere già **selezionato .NET Core 3.1** per il framework di destinazione. In caso contrario, **selezionare .NET Core 3.1.** Scegliere quindi **Crea.**

   :::image type="content" source="./media/vs-2019/vb-target-framework.png" alt-text="Screenshot che mostra la finestra &quot;Informazioni aggiuntive&quot; con .NET Core 3.1 selezionato nel campo Framework di destinazione.":::

   Visual Studio aprirà il nuovo progetto.

::: moniker-end

::: moniker range=">=vs-2022"

1. Aprire Visual Studio.

1. Nella finestra iniziale scegliere **Crea un nuovo progetto.**

   :::image type="content" source="media/vs-2022/create-new-project-dark-theme.png" alt-text="Screenshot che mostra la Visual Studio iniziale con l'opzione &quot;Crea un nuovo progetto&quot; selezionata.":::

1. Nella finestra **Crea un nuovo progetto** scegliere Visual Basic dall'elenco Linguaggio.  Scegliere quindi **Windows** dall'elenco Piattaforma e **Console** dall'elenco Project tipi di dati.

   Dopo aver applicato i filtri del linguaggio, della piattaforma e del tipo di progetto, scegliere il modello **Applicazione** console e quindi **scegliere Avanti.**

   :::image type="content" source="media/vs-2022/vb-create-new-project-console-net-core.png" alt-text="Screenshot che mostra la finestra &quot;Crea un nuovo progetto&quot; con le opzioni &quot;Visual Basic&quot;, &quot;Windows&quot; e &quot;Console&quot; selezionate nei filtri Linguaggio, Piattaforma e Tipo Project e il modello di progetto Applicazione console selezionato.":::

   > [!NOTE]
   > Se il modello Applicazione **console** non viene visualizzato, è possibile installarlo dalla **finestra Crea un nuovo** progetto. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**.
   >
   > :::image type="content" source="media/vs-2022/not-finding-what-looking-for.png" alt-text="Screenshot che mostra il collegamento &quot;Installa altri strumenti e funzionalità&quot; dal messaggio &quot;Non è stato trovato ciò che si sta cercando&quot; nella finestra &quot;Crea nuovo progetto&quot;.":::
   >
   > Nella finestra di dialogo Programma di installazione di Visual Studio quindi scegliere il carico di **lavoro Sviluppo per desktop .NET.**
   >
   > :::image type="content" source="media/vs-2022/dot-net-core-xplat-dev-workload.png" alt-text="Screenshot che mostra il carico di lavoro Sviluppo di applicazioni desktop .NET nel Programma di installazione di Visual Studio.":::
   >
   > Successivamente, scegliere il pulsante **Modifica** nel programma di installazione di Visual Studio. Quando viene richiesto, salvare il lavoro. Scegliere quindi **Continua** per installare il carico di lavoro. Quindi tornare al passaggio 2 della procedura [Creare un progetto](#create-a-project)".

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *WhatIsYourName* nella casella **Nome del progetto**. Scegliere quindi **Avanti.**

   :::image type="content" source="media/vs-2022/vb-name-your-project-whatname.png" alt-text="Screenshot che mostra la finestra &quot;Configure your new project&quot; (Configura il nuovo progetto) con il campo Project nome impostato su 'WhatIsYourName'.":::

1. Nella finestra **Informazioni aggiuntive** dovrebbe essere già selezionato **.NET 6.0** per il framework di destinazione. In caso contrario, selezionare **.NET 6.0.** Scegliere quindi **Crea.**

   :::image type="content" source="media/vs-2022/vb-target-framework.png" alt-text="Screenshot che mostra la finestra &quot;Informazioni aggiuntive&quot; con .NET 6.0 selezionato nel campo Framework.":::

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

1. Usare il pulsante **Start** verde o premere **F5** per compilare ed eseguire la prima app.

1. Quando la finestra della console si apre, immettere il proprio nome. La finestra della console dovrebbe avere un aspetto simile allo screenshot seguente:

   ![Finestra della console con "What is your name?", la data, l'ora della console e il messaggio Premere un tasto per continuare](media/vb-console-what-name.png)

1. Premere un tasto per chiudere la finestra della console.

::: moniker-end

::: moniker range="vs-2019"

1. Nel progetto *WhatIsYourName* immettere il codice Visual Basic seguente immediatamente dopo la parentesi quadra di apertura che segue la riga `Sub Main(args As String())` e prima della riga `End Sub`:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Questo codice sostituisce le istruzioni <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> e <xref:System.Console.ReadKey%2A> esistenti.

   ![Screenshot che mostra il codice per il file "Program.vb" nel progetto 'WhatIsYourName' caricato nell'editor Visual Basic codice.](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. Usare il pulsante **Start** verde o premere **F5** per compilare ed eseguire la prima app.

1. Quando la finestra della console si apre, immettere il proprio nome. La finestra della console dovrebbe avere un aspetto simile allo screenshot seguente:

   ![Screenshot che mostra la finestra della console con What Is Your Name, l'ora e la data e premere un tasto qualsiasi per continuare i messaggi.](media/vb-console-what-name.png)

1. Premere un tasto per chiudere la finestra della console.

 ::: moniker-end

::: moniker range=">=vs-2022"

1. Nel progetto *WhatIsYourName* immettere il codice Visual Basic seguente nel file *Program.vb* subito dopo la parentesi quadra di apertura che segue la riga e prima `Sub Main(args As String())` della riga `End Sub` :

   ```vb
   Console.WriteLine(vbCrLf + "What is your name? ")
   Dim name = Console.ReadLine()
   Dim currentDate = DateTime.Now
   Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")
   Console.Write(vbCrLf + "Press any key to exit... ")
   Console.ReadKey(True)
   ```

   Questo codice sostituisce l'istruzione <xref:System.Console.WriteLine%2A> esistente.

   :::image type="content" source="media/vs-2022/vb-codewindow-what-name-dark.png" alt-text="Screenshot che mostra il codice per il file &quot;Program.vb&quot; nel progetto 'WhatIsYourName' caricato nell'editor Visual Basic codice.":::

1. Usare il pulsante **Start** verde o premere **F5** per compilare ed eseguire la prima app.

1. Quando la finestra della console si apre, immettere il proprio nome. La finestra della console dovrebbe avere un aspetto simile allo screenshot seguente:

   :::image type="content" source="media/vs-2022/vb-console-what-name.png" alt-text="Screenshot che mostra la finestra della console con Il nome, l'ora e la data e premere un tasto qualsiasi per continuare i messaggi.":::

1. Premere un tasto per chiudere la finestra della console.

 ::: moniker-end

## <a name="create-a-calculate-this-application"></a>Creare un'applicazione "CalculateThis"

::: moniker range="vs-2017"

1. Aprire Visual Studio 2017 e quindi nella barra dei menu superiore scegliere **File** >  > **nuovo Project**.

1. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **Visual Basic**, quindi selezionare **.NET Core**. Nel riquadro centrale scegliere **Console App (.NET Core)** (App console (.NET Core)). Quindi assegnare al file il nome *CalculateThis*.

1. Immettere il codice seguente tra la `Module Program` riga e la riga `End Module` :

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

1. Nella finestra **Crea un nuovo progetto** scegliere Visual Basic dall'elenco Lingua.  Scegliere quindi **Windows** dall'elenco Piattaforma e **Console dall'elenco** dei tipi di progetto.

1. Dopo aver applicato i filtri del linguaggio, della piattaforma e del tipo di progetto, scegliere il modello **Applicazione console** e quindi **scegliere Avanti.**

   Quindi, nella **finestra Configura il nuovo progetto** digitare o immettere *CalculateThis* nella casella Project **nome.** Scegliere quindi **Avanti**.

1. Nella finestra **Informazioni aggiuntive** è necessario che **.NET Core 3.1** sia già selezionato per il framework di destinazione. In caso contrario, **selezionare .NET Core 3.1.** Scegliere quindi **Crea**.

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

   ![Screenshot che mostra il codice per il file "Program.vb" nel progetto "CalculateThis" caricato nell'editor Visual Basic codice.](media/vb-codewindow-calculate-this.png)

1. Fare clic su **CalculateThis** per eseguire il programma. La finestra della console dovrebbe avere un aspetto simile allo screenshot seguente:

    ![Screenshot che mostra la finestra della console per l'app CalculateThis, che include le richieste sulle azioni da eseguire.](media/vb-console-calculate-this.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

1. Nella finestra **Crea un nuovo progetto** scegliere Visual Basic dall'elenco Lingua.  Scegliere quindi **Windows** dall'elenco Piattaforma e **Console** dall'elenco Project tipi di dati.

1. Dopo aver applicato i filtri del linguaggio, della piattaforma e del tipo di progetto, scegliere il modello **Applicazione console** e quindi **scegliere Avanti.**

   Quindi, nella **finestra Configura il nuovo progetto** digitare o immettere *CalculateThis* nella casella Project **nome.** Scegliere quindi **Avanti**.

1. Nella finestra **Informazioni aggiuntive** è necessario che **.NET 6.0 sia** già selezionato per il framework di destinazione. In caso contrario, selezionare **.NET 6.0.** Scegliere quindi **Crea**.

1. In *Program.vb* immettere il codice seguente tra la `Module Program` riga e la `End Module` riga:

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

   :::image type="content" source="media/vs-2022/vb-codewindow-calculate-this.png" alt-text="Screenshot che mostra il codice per il file &quot;Program.vb&quot; nel progetto &quot;CalculateThis&quot; caricato nell'editor Visual Basic codice.":::

1. Selezionare la freccia pulsante Start accanto **a CalculateThis per** eseguire il programma. La finestra della console dovrebbe avere un aspetto simile allo screenshot seguente:

   :::image type="content" source="media/vs-2022/vb-console-calculate-this.png" alt-text="Screenshot che mostra la finestra della console per l'app CalculateThis, che include le richieste sulle azioni da eseguire.":::

::: moniker-end

[!INCLUDE[../includes/git-source-control.md](../includes/git-source-control.md)]

## <a name="quick-answers-faq"></a>Domande frequenti con risposta rapida

Ecco una rapida serie di domande frequenti per evidenziare alcuni concetti chiave.

### <a name="what-is-visual-basic"></a>Che cos'è Visual Basic?

Visual Basic è un linguaggio di programmazione indipendente dai tipi progettato per garantire la massima facilità di apprendimento. Deriva dall'acronimo BASIC, che significa "Beginner's All-purpose Symbolic Instruction Code" (Codice di istruzioni simbolico multifunzione per principianti).

### <a name="what-is-visual-studio"></a>Che cos'è Visual Studio?

Visual Studio è una suite integrata per lo sviluppo di strumenti di produttività per gli sviluppatori. Si può immaginare Visual Studio come un programma utilizzabile per creare programmi e applicazioni.

### <a name="what-is-a-console-app"></a>Che cos'è un'app console?

Un'app console accetta input e visualizza l'output in una finestra della riga di comando, nota anche come console.

### <a name="what-is-net-core"></a>Informazioni su .NET Core

.NET Core è il passaggio successivo nell'evoluzione di .NET Framework. Mentre .NET Framework consentiva di condividere codice tra linguaggi di programmazione diversi, .NET Core aggiunge la possibilità di condividere codice tra piattaforme diverse. E, ciliegina sulla torta, è open source. Sia il .NET Framework che .NET Core includono librerie di funzionalità predefinite e Common Language Runtime (CLR), che funge da macchina virtuale in cui eseguire il codice.

## <a name="next-steps"></a>Passaggi successivi

L'esercitazione è stata completata. Per altre informazioni, vedere l'esercitazione seguente.

> [!div class="nextstepaction"]
> [Compilare una libreria .NET Standard con Visual Basic e .NET Core SDK in Visual Studio](/dotnet/core/tutorials/vb-library-with-visual-studio)

## <a name="see-also"></a>Vedi anche

* [Procedure dettagliate relative al linguaggio Visual Basic](/dotnet/visual-basic/walkthroughs)
* [Informazioni di riferimento per il linguaggio Visual Basic](/dotnet/visual-basic/language-reference/index)
* [IntelliSense per i file di codice di Visual Basic](../../ide/visual-basic-specific-intellisense.md)
