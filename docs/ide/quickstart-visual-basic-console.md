---
title: Creare per la prima volta un'app console con Visual Basic
description: Informazioni dettagliate su come creare un'app console Hello World semplice in Visual Studio con Visual Basic.
ms.custom: acquisition, seodec18
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
ms.devlang: vb
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 5d963762772060296f38a9c9c1ebfce85fbf5f8e
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2021
ms.locfileid: "112113146"
---
# <a name="quickstart-create-your-first-console-app-in-visual-studio-with-visual-basic"></a>Guida introduttiva: Creare per la prima volta un'app console in Visual Studio con Visual Basic

In questa introduzione di 5-10 minuti all'ambiente di sviluppo integrato (IDE) di Visual Studio si creerà una semplice applicazione di Visual Basic che viene eseguita nella console.

::: moniker range="vs-2017"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

## <a name="create-a-project"></a>Creare un progetto

In primo luogo si creerà un progetto di applicazione Visual Basic. Il tipo di progetto include fin dall'inizio tutti i file modello necessari.

::: moniker range="vs-2017"

1. Aprire Visual Studio 2017.

2. Nella barra dei menu superiore scegliere **File** > **Nuovo** > **progetto.**

3. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **Visual Basic**, quindi selezionare **.NET Core**. Nel riquadro centrale scegliere **Console App (.NET Core)** (App console (.NET Core)). Quindi assegnare al progetto il nome *HelloWorld*.

   ![Modello di progetto Console App (.NET Core) nella finestra di dialogo Nuovo progetto dell'IDE di Visual Studio](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

     Se non viene visualizzato il modello di progetto **Console App (.NET Core)** (App console (.NET Core)), fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro della finestra di dialogo **Nuovo progetto**.

   ![Fare clic sul collegamento Apri il programma di installazione di Visual Studio nella finestra di dialogo Nuovo progetto](../ide/media/vb-open-visual-studio-installer-hello-world.png)

     Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo multipiattaforma .NET Core**, quindi scegliere **Modifica**.

     ![Carico di lavoro Sviluppo multipiattaforma .NET Core nel programma di installazione di Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Alcuni degli screenshot contenuti in questo Avvio rapido usano il tema scuro. Per passare al tema scuro, qualora questo non fosse già in uso, vedere le informazioni disponibili nella pagina [Personalizzare l'IDE e l'editor di Visual Studio](quickstart-personalize-the-ide.md).

1. Aprire Visual Studio 2019.

1. Nella finestra iniziale scegliere **Crea un nuovo progetto.**

   ![Visualizzare la finestra Crea un nuovo progetto](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Nella finestra **Crea un nuovo progetto** scegliere Visual Basic dall'elenco Linguaggio.  Scegliere quindi **Windows dall'elenco** Piattaforma e **Console dall'elenco** dei tipi di progetto.

   Dopo aver applicato i filtri del linguaggio, della piattaforma e del tipo di progetto, scegliere il modello **Applicazione** console e quindi **scegliere Avanti.**

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-create-new-project-console-net-core.png" alt-text="Scegliere il modello Visual Basic per l'applicazione console":::

   > [!NOTE]
   > Se il modello Applicazione **console** non viene visualizzato, è possibile installarlo dalla **finestra Crea un nuovo** progetto. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**.
   >
   > ![Collegamento "Installa altri strumenti e funzionalità" nel messaggio "L'elemento cercato non è stato trovato?" nella finestra "Crea un nuovo progetto"](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Scegliere quindi il carico di lavoro **Sviluppo multipiattaforma .NET Core** nel programma di installazione di Visual Studio.
   >
   > ![Carico di lavoro Sviluppo multipiattaforma .NET Core nel programma di installazione di Visual Studio](../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Successivamente, scegliere il pulsante **Modifica** nel programma di installazione di Visual Studio. Quando viene richiesto, salvare il lavoro. Scegliere quindi **Continua** per installare il carico di lavoro. Quindi tornare al passaggio 2 della procedura [Creare un progetto](#create-a-project)".

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *WhatIsYourName* nella casella **Nome del progetto**. Scegliere quindi **Avanti.**

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-name-your-project-whatname.png" alt-text="Nella finestra Configura il nuovo progetto assegnare al progetto il nome &quot;WhatIsYourName&quot;":::

1. Nella finestra **Informazioni aggiuntive** dovrebbe essere già **selezionato .NET Core 3.1** per il framework di destinazione. In caso contrario, **selezionare .NET Core 3.1.** Scegliere quindi **Crea.**

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-target-framework.png" alt-text="Nella finestra &quot;Informazioni aggiuntive&quot; assicurarsi che sia selezionato .NET Core 3.1":::

   Visual Studio aprirà il nuovo progetto.

::: moniker-end

## <a name="create-the-application"></a>Creazione dell'applicazione

Dopo la selezione del modello di progetto Visual Basic e l'assegnazione di un nome al progetto, in Visual Studio viene creata una semplice applicazione "Hello World". Chiama il metodo <xref:System.Console.WriteLine%2A> per visualizzare la stringa letterale "Hello World!" nella finestra della console.

![Visualizzare il codice Hello World predefinito dal modello](../ide/media/vb-console-helloworld-template.png)

Se si fa clic sul pulsante **HelloWorld** nell'IDE è possibile eseguire il programma in modalità debug.

  ![Fare clic sul pulsante HelloWorld per eseguire il programma in modalità debug](../ide/media/vb-console-hello-world-button.png)

Se si esegue questa operazione, la finestra della console resta visibile per un istante, quindi viene chiusa. Ciò accade perché il metodo `Main` termina dopo l'esecuzione dell'unica istruzione, quindi l'applicazione termina.

### <a name="add-some-code&quot;></a>Aggiungere codice

Ora si aggiungerà del codice per sospendere l'applicazione e richiedere l'input dell'utente.

1. Aggiungere il codice seguente subito dopo la chiamata al metodo <xref:System.Console.WriteLine%2A>:

   ```vb
   Console.Write(&quot;Press any key to continue...")
   Console.ReadKey(true)
   ```

    Questo codice sospende l'esecuzione del programma fino a quando non si preme un tasto.

2. Nella barra dei menu selezionare **Compila**  >  **compila soluzione.**

   Il programma viene compilato in un linguaggio intermedio (IL) che viene successivamente convertito in codice binario da un compilatore JIT (Just-In-Time).

## <a name="run-the-application"></a>Eseguire l'applicazione

1. Fare clic sul pulsante **HelloWorld** nella barra degli strumenti.

   ![Fare clic sul pulsante HelloWorld per eseguire il programma dalla barra degli strumenti](../ide/media/vb-console-hello-world-button.png)

2. Premere un tasto per chiudere la finestra della console.

   ![Finestra della console che visualizza Hello World e Premere un tasto qualsiasi per continuare](../ide/media/vb-console-hello-world-press-any-key.png)

## <a name="next-steps"></a>Passaggi successivi

La guida introduttiva è stata completata. Ci auguriamo che sia stata utile per l'apprendimento dell'uso di Visual Basic e dell'IDE di Visual Studio. Per altre informazioni, continuare con l'esercitazione seguente.

> [!div class="nextstepaction"]
> [Introduzione a Visual Basic in Visual Studio](../get-started/visual-basic/tutorial-console.md)
