---
title: Usare Visual Studio per creare la prima app console C#
titleSuffix: ''
description: Informazioni dettagliate su come creare un'app console Hello World semplice in Visual Studio con C#.
ms.date: 09/21/2018
ms.prod: visual-studio-dev15
ms.custom: seodec18
ms.topic: quickstart
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 2b36051f3a316f2b00ebdd08110f22346a910512
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853918"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-c-console-app"></a>Guida introduttiva: Usare Visual Studio per creare la prima app console C#

In questa introduzione di 5-10 minuti all'ambiente di sviluppo integrato (IDE) di Visual Studio si creerà una semplice app C# eseguita nella console.

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) per installarlo gratuitamente.

## <a name="create-a-project"></a>Creare un progetto

Per prima cosa si crea un progetto di applicazione C#. Il tipo di progetto include fin dall'inizio tutti i file modello necessari.

1. Aprire Visual Studio 2017.

2. Sulla barra dei menu in alto scegliere **File** > **Nuovo** > **Progetto**.

3. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **C#** e quindi scegliere **.NET Core**. Nel riquadro centrale scegliere **Console App (.NET Core)** (App console (.NET Core)). Quindi assegnare al progetto il nome *HelloWorld*.

   ![Modello di progetto Console App (.NET Core) nella finestra di dialogo Nuovo progetto dell'IDE di Visual Studio](../ide/media/new-project-csharp-dotnetcore-helloworld-console-app.png)

     Se non viene visualizzato il modello di progetto **Applicazione console (.NET Core)**, fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro a sinistra della finestra di dialogo **Nuovo progetto**.

   ![Fare clic sul collegamento Apri il programma di installazione di Visual Studio dalla finestra di dialogo Nuovo progetto](../ide/media/csharp-open-visual-studio-installer-hello-world.png)

     Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo multipiattaforma .NET Core**, quindi scegliere **Modifica**.

     ![Carico di lavoro Sviluppo multipiattaforma .NET Core nel programma di installazione di Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

## <a name="create-the-application"></a>Creare l'applicazione

Dopo la selezione del modello di progetto C# e l'assegnazione di un nome al progetto, in Visual Studio viene creata una semplice applicazione "Hello World". 

A tale scopo viene chiamato il metodo <xref:System.Console.WriteLine%2A> per visualizzare la stringa letterale "Hello World!" nella finestra della console.

   ![Visualizzare il codice Hello World predefinito dal modello](../ide/media/csharp-console-helloworld-template.png)

Se si preme **F5** è possibile eseguire il programma in modalità di debug. La finestra della console resta comunque visibile per un istante, quindi viene chiusa.

Ciò accade perché il metodo `Main` termina dopo l'esecuzione dell'unica istruzione, quindi l'applicazione termina.

### <a name="add-some-code"></a>Aggiungere codice

È possibile aggiungere codice per sospendere l'applicazione in modo che la finestra della console non venga chiusa fino a quando non si preme **INVIO**.

1. Aggiungere il codice seguente subito dopo la chiamata al metodo <xref:System.Console.WriteLine%2A>:

   ```csharp
   Console.ReadLine();
   ```

1. Verificare che il codice sia simile al seguente nell'editor del codice:

   ![Aggiungere codice per sospendere l'app Hello World](../ide/media/csharp-console-helloworld-add-code.png)

## <a name="run-the-application"></a>Esecuzione dell'applicazione

1. Fare clic sul pulsante **HelloWorld** sulla barra degli strumenti per eseguire l'applicazione in modalità di debug. In alternativa, è possibile premere **F5**.

   ![Fare clic sul pulsante HelloWorld per eseguire l'app dalla barra degli strumenti](../ide/media/csharp-console-hello-world-button.png)

1. Visualizzare l'app nella finestra della console.

   ![Finestra della console che mostra Hello World!](../ide/media/csharp-console-hello-world.png)

### <a name="close-the-application"></a>Chiudere l'applicazione

1. Premere **INVIO** per chiudere la finestra della console.

1. Chiudere il riquadro **Output** in Visual Studio.

   ![Chiudere il riquadro Output in Visual Studio](../ide/media/csharp-hello-world-close-output-pane.png)

1. Chiudere Visual Studio.

## <a name="next-steps"></a>Passaggi successivi

La guida introduttiva è stata completata. Ci auguriamo che sia stata utile per l'apprendimento dell'uso di C# e dell'IDE di Visual Studio. Per altre informazioni, continuare con le esercitazioni seguenti.

> [!div class="nextstepaction"]
> [Introduzione a un'app console C# in Visual Studio](../get-started/csharp/tutorial-console.md)
