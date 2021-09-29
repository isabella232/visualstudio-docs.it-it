---
title: Creare per la prima volta un'app console con Visual Basic
description: Informazioni su come creare un'app console Hello World semplice in Visual Studio con Visual Basic, passo dopo passo.
ms.custom: vs-acquisition
ms.date: 09/14/2021
ms.topic: quickstart
ms.devlang: vb
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 0ece22de8280742a099432fd5b3e527631718cfb
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128427823"
---
# <a name="quickstart-create-your-first-console-app-in-visual-studio-with-visual-basic"></a>Guida introduttiva: Creare per la prima volta un'app console in Visual Studio con Visual Basic

In questa introduzione di 5-10 minuti all'ambiente di sviluppo integrato (IDE) di Visual Studio si creerà una semplice applicazione di Visual Basic che viene eseguita nella console.

::: moniker range="vs-2017"

Se non è già stato installato Visual Studio, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range=">=vs-2019"

Se non è già stato installato Visual Studio, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

## <a name="create-a-project"></a>Creare un progetto

In primo luogo si creerà un progetto di applicazione Visual Basic. Il tipo di progetto include fin dall'inizio tutti i file modello necessari.

::: moniker range="vs-2017"

1. Aprire Visual Studio 2017.

1. Nella barra dei menu superiore scegliere **File** > **nuovo** > **Project**.

1. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **Visual Basic**, quindi selezionare **.NET Core**. Nel riquadro centrale scegliere **Console App (.NET Core)** (App console (.NET Core)). Quindi assegnare al progetto il nome *HelloWorld*.

   ![Modello di progetto Console App (.NET Core) nella finestra di dialogo Nuovo progetto dell'IDE di Visual Studio](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

   Se non viene visualizzato il modello di progetto **Console App (.NET Core)** (App console (.NET Core)), fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro della finestra di dialogo **Nuovo progetto**.

   ![Fare clic sul collegamento Apri il programma di installazione di Visual Studio nella finestra di dialogo Nuovo progetto](../ide/media/vb-open-visual-studio-installer-hello-world.png)

   Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo multipiattaforma .NET Core**, quindi scegliere **Modifica**.

   ![Carico di lavoro Sviluppo multipiattaforma .NET Core nel programma di installazione di Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Alcuni degli screenshot contenuti in questo Avvio rapido usano il tema scuro. Per passare al tema scuro, qualora questo non fosse già in uso, vedere le informazioni disponibili nella pagina [Personalizzare l'IDE e l'editor di Visual Studio](quickstart-personalize-the-ide.md).

1. Aprire Visual Studio.

1. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

   ![Screenshot che mostra la finestra iniziale in Visual Studio con l'opzione "Crea un nuovo progetto" evidenziata.](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Nella finestra **Crea un nuovo progetto** scegliere Visual Basic dall'elenco Lingua.  Scegliere quindi **Windows** dall'elenco Piattaforma e **Console dall'elenco** dei tipi di progetto.

   Dopo aver applicato i filtri del linguaggio, della piattaforma e del tipo di progetto, scegliere il modello **Applicazione console** e quindi **scegliere Avanti.**

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-create-new-project-console-net-core.png" alt-text="Screenshot che mostra la finestra &quot;Crea un nuovo progetto&quot; con &quot;Visual Basic&quot;, &quot;Windows&quot; e &quot;Console&quot; selezionati nei filtri del linguaggio, della piattaforma e del tipo di progetto. Il modello di progetto &quot;Applicazione console&quot; è evidenziato.":::

   > [!NOTE]
   > Se il modello Applicazione **console** non viene visualizzato, è possibile installarlo dalla finestra **Crea un nuovo** progetto. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**.
   >
   > ![Screenshot che mostra il collegamento "Installa altri strumenti e funzionalità" evidenziato nel messaggio "Non è possibile trovare ciò che si sta cercando".](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Scegliere quindi il carico di lavoro **Sviluppo multipiattaforma .NET Core** nel programma di installazione di Visual Studio.
   >
   > ![Screenshot che mostra il carico di lavoro "Sviluppo multipiattaforma.NET Core" nel Programma di installazione di Visual Studio.](../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Successivamente, scegliere il pulsante **Modifica** nel programma di installazione di Visual Studio. Quando viene richiesto, salvare il lavoro. Scegliere quindi **Continua** per installare il carico di lavoro. Quindi tornare al passaggio 2 della procedura [Creare un progetto](#create-a-project)".

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *HelloWorld* nella casella **Nome del progetto**. Scegliere quindi **Avanti**.

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-name-your-console-project-hello-world.png" alt-text="nella schermata che mostra la finestra &quot;Configura il nuovo progetto&quot; con &quot;HelloWorld&quot; immesso nel campo Project nome.":::

1. Nella finestra **Informazioni aggiuntive** è necessario che **.NET Core 3.1** sia già selezionato per il framework di destinazione. In caso contrario, selezionare **.NET Core 3.1.** Scegliere quindi **Crea**.

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-target-framework.png" alt-text="Screenshot che mostra la finestra Informazioni aggiuntive con '.NET Core 3.1' selezionato nel campo Framework.":::

   Visual Studio aprirà il nuovo progetto.

::: moniker-end

::: moniker range=">=vs-2022"

1. Aprire Visual Studio.

1. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

   :::image type="content" source="media/vs-2022/create-new-project-dark-theme.png" alt-text="Screenshot che mostra la finestra iniziale in Visual Studio con l'opzione &quot;Crea un nuovo progetto&quot; evidenziata.":::

1. Nella finestra **Crea un nuovo progetto** scegliere Visual Basic dall'elenco Lingua.  Scegliere quindi **Windows** dall'elenco Piattaforma e **Console dall'elenco** dei tipi di progetto.

   Dopo aver applicato i filtri del linguaggio, della piattaforma e del tipo di progetto, scegliere il modello **Applicazione console** e quindi **scegliere Avanti.**

   :::image type="content" source="media/vs-2022/vb-create-new-project-console-net-core.png" alt-text="Screenshot che mostra la finestra &quot;Crea un nuovo progetto&quot; con &quot;Visual Basic&quot;, &quot;Windows&quot; e &quot;Console&quot; selezionati nei filtri del linguaggio, della piattaforma e del tipo di progetto. Il modello di progetto &quot;Applicazione console&quot; è evidenziato.":::

   > [!NOTE]
   > Se il modello Applicazione **console** non viene visualizzato, è possibile installarlo dalla finestra **Crea un nuovo** progetto. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**.
   >
   > :::image type="content" source="media/vs-2022/not-finding-what-looking-for.png" alt-text="Screenshot che mostra il collegamento &quot;Installa altri strumenti e funzionalità&quot; evidenziato nel messaggio &quot;Non è possibile trovare ciò che si sta cercando&quot;.":::
   > 
   > Nella finestra di dialogo Programma di installazione di Visual Studio quindi scegliere il carico di **lavoro Sviluppo desktop .NET.**
   >
   > :::image type="content" source="media/vs-2022/dot-net-core-xplat-dev-workload.png" alt-text="Screenshot che mostra il carico di lavoro &quot;Sviluppo di desktop .NET&quot; nel Programma di installazione di Visual Studio.":::
   >
   > Successivamente, scegliere il pulsante **Modifica** nel programma di installazione di Visual Studio. Quando viene richiesto, salvare il lavoro. Scegliere quindi **Continua** per installare il carico di lavoro. Quindi tornare al passaggio 2 della procedura [Creare un progetto](#create-a-project)".

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *HelloWorld* nella casella **Nome del progetto**. Scegliere quindi **Avanti**.

   :::image type="content" source="media/vs-2022/vb-name-your-project-hello-world.png" alt-text="Screenshot che mostra la finestra &quot;Configura il nuovo progetto&quot; con &quot;HelloWorld&quot; immesso nel campo Project nome.":::

1. Nella finestra **Informazioni aggiuntive** è necessario che **.NET 6.0 sia** già selezionato per il framework di destinazione. In caso contrario, **selezionare .NET 6.0 nell'elenco** a discesa Framework.  Scegliere quindi **Crea**.

   :::image type="content" source="media/vs-2022/vb-target-framework.png" alt-text="Screenshot che mostra la finestra Informazioni aggiuntive con '.NET 6.0' selezionato nel campo Framework.":::

   Visual Studio aprirà il nuovo progetto.

::: moniker-end

## <a name="create-the-application"></a>Creare l'applicazione

::: moniker range="vs-2019"

Dopo la selezione del modello di progetto Visual Basic e l'assegnazione di un nome al progetto, in Visual Studio viene creata una semplice applicazione "Hello World". Chiama il metodo <xref:System.Console.WriteLine%2A> per visualizzare la stringa letterale "Hello World!" nella finestra della console.

![Screenshot che mostra il codice predefinito "Hello World" nel modello Visual Basic progetto.](../ide/media/vb-console-helloworld-template.png)

Se si seleziona il **pulsante HelloWorld** nell'IDE, è possibile eseguire il programma in modalità debug.

![Screenshot che mostra il pulsante "Hello World" evidenziato nella barra Visual Studio barra degli strumenti.](../ide/media/vb-console-hello-world-button.png)

Quando l'applicazione viene eseguita nel Microsoft Visual Studio Console di debug, la finestra della console rimane aperta fino a quando non si preme un tasto. 

Tuttavia, se si passa a *HelloWorld.exe* in Esplora file ed eseguirla, la routine termina dopo l'esecuzione della singola istruzione e la finestra della `Main` console si chiude rapidamente.

### <a name="add-some-code&quot;></a>Aggiungere codice

Ora si aggiungerà del codice per sospendere l'applicazione e richiedere l'input dell'utente.

1. Aggiungere il codice seguente subito dopo la chiamata al metodo <xref:System.Console.WriteLine%2A>:

   ```vb
   Console.Write(&quot;Press any key to continue...")
   Console.ReadKey(true)
   ```

   Questo codice sospende l'esecuzione del programma fino a quando non si preme un tasto.

1. Sulla barra dei menu selezionare **Compila** > **soluzione**.

   Il programma viene compilato in un linguaggio intermedio (IL) che viene successivamente convertito in codice binario da un compilatore JIT (Just-In-Time).

## <a name="run-the-application"></a>Eseguire l'applicazione

1. In **Esplora soluzioni** fare clic con il pulsante destro **del mouse su HelloWorld** per aprire il menu di scelta rapida per il progetto. Selezionare quindi **Apri cartella in Esplora file**.

1. Passare al file *HelloWorld.exe* nella cartella **bin > Debug > net6.0** ed eseguirlo.

L'applicazione viene ora eseguita nella console e rimane aperta fino a quando non si preme un tasto qualsiasi per chiudere la finestra della console.

   ![Screenshot che mostra l'applicazione console Hello World in esecuzione. L'app visualizza i messaggi "Hello World!". e "Premere un tasto qualsiasi per continuare".](../ide/media/vb-console-hello-world-press-any-key.png)

::: moniker-end

::: moniker range=">=vs-2022&quot;

Dopo aver selezionato il modello Visual Basic progetto e aver creato un nome per il progetto, Visual Studio crea un semplice &quot;Hello World!&quot; applicazione per l'utente. Il file **Program.vb** contiene il codice predefinito che chiama il metodo per visualizzare la stringa <xref:System.Console.WriteLine%2A> letterale &quot;Hello World!&quot; nella finestra della console.

:::image type="content" source="media/vs-2022/vb-console-hello-world-template.png" alt-text="Screenshot che mostra il codice &quot;Hello World&quot; predefinito nel file Program.vb.":::

Selezionare il **pulsante HelloWorld** o premere **CTRL** + **F5** per eseguire il codice &quot;HelloWorld&quot; predefinito in modalità debug.

:::image type="content" source="media/vs-2022/vb-console-hello-world-button.png" alt-text="Screenshot che mostra il pulsante &quot;HelloWorld&quot; evidenziato nella barra Visual Studio barra degli strumenti.":::

Quando l'applicazione viene eseguita nel Microsoft Visual Studio Console di debug, la finestra della console rimane aperta fino a quando non si preme un tasto. 

Tuttavia, se si passa *HelloWorld.exe* in Esplora file ed eseguirla, la procedura termina dopo l'esecuzione della singola istruzione e la finestra della console si `Main` chiude rapidamente.

### <a name=&quot;add-some-code&quot;></a>Aggiungere codice

Ora si aggiungerà del codice per sospendere l'applicazione e richiedere l'input dell'utente.

1. Aggiungere il codice seguente subito dopo la chiamata al metodo <xref:System.Console.WriteLine%2A>:

   ```vb
   Console.Write(&quot;Press any key to continue...")
   Console.ReadKey(true)
   ```

   Questo codice sospende il programma fino a quando non si preme un tasto.

1. Nella barra dei menu selezionare **Compila** > **compila soluzione.**

   Compilando la soluzione, il programma viene compilato in un linguaggio intermedio (IL) convertito in codice binario da un compilatore JIT (Just-In-Time).

## <a name="run-the-application"></a>Eseguire l'applicazione

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse **su HelloWorld** per aprire il menu di scelta rapida per il progetto. Selezionare quindi **Apri cartella in Esplora file**.

1. Passare al file *HelloWorld.exe* nella cartella **bin > Debug > net6.0** ed eseguirlo.

A questo punto l'applicazione viene eseguita nella console e rimane aperta fino a quando non si preme un tasto qualsiasi per chiudere la finestra della console.

   :::image type="content" source="media/vs-2022/vb-console-hello-world-press-any-key.png" alt-text="Screenshot che mostra l'applicazione console HelloWorld in esecuzione. L'app visualizza i messaggi &quot;Hello World!&quot; e &quot;Premere un tasto qualsiasi per continuare&quot;.":::

::: moniker-end

## <a name="next-steps"></a>Passaggi successivi

La guida introduttiva è stata completata. Ci auguriamo che l'utente abbia appreso Visual Basic e l'IDE Visual Studio. Per altre informazioni, continuare con l'esercitazione seguente.

> [!div class="nextstepaction"]
> [Introduzione a Visual Basic in Visual Studio](../get-started/visual-basic/tutorial-console.md)
