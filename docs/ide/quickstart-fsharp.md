---
title: 'Guida introduttiva: Creare un servizio Web ASP.NET Core in F#'
description: Informazioni dettagliate su come creare un servizio Web ASP.NET Core in Visual Studio con F#.
ms.date: 09/14/2021
ms.topic: quickstart
ms.custom: vs-acquisition
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- FSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 17d443c9dac7a37670c65c7fb9c8da8362aa4ab4
ms.sourcegitcommit: 59613afd06a8f184efab8e108410066824a2b712
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/18/2021
ms.locfileid: "127920030"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-service-in-f"></a>Avvio rapido: Usare Visual Studio per creare il primo ASP.NET Core web in F\#

In questa introduzione di 5-10 minuti a F# in Visual Studio verrà creata un'applicazione Web ASP.NET Core F#.

::: moniker range="vs-2017"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range=">=vs-2019"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

## <a name="create-a-project"></a>Creare un progetto

Per prima cosa, verrà creato un progetto API Web ASP:NET Core. Il tipo di progetto viene specificato con i file di modello che costituiscono un servizio Web funzionale, prima ancora di aggiungere alcun elemento.

::: moniker range="vs-2017"

1. Aprire Visual Studio.

1. Nella barra dei menu superiore scegliere **File** > **Nuovo** > **Project**.

1. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **Visual F#** e quindi scegliere **Web**. Nel riquadro centrale, scegliere **Applicazione Web ASP.NET Core**, quindi scegliere **OK**.

   Se non viene visualizzata la categoria dei modelli di progetto **.NET Core** scegliere il collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo ASP.NET e Web**, quindi scegliere **Cambia**.

   ![Carico di lavoro ASP.NET nel programma di installazione di Visual Studio](../ide/media/quickstart-aspnet-workload.png)

1. Nella finestra di dialogo **Nuova applicazione Web ASP.NET Core** selezionare **ASP.NET Core 2.1** nel menu a discesa in alto. Se non viene visualizzato **ASP.NET Core 2.1** nell'elenco, installarlo seguendo il collegamento **Download** visualizzato in una barra gialla nella parte superiore della finestra di dialogo. Scegliere **OK.**

::: moniker-end

::: moniker range="vs-2019"

1. Aprire Visual Studio.

1. Nella finestra iniziale scegliere **Crea un nuovo progetto.**

1. Nella pagina **Crea un nuovo progetto** digitare **f# web** nella casella di ricerca e quindi scegliere il modello di progetto **Applicazione Web ASP.NET Core**. Scegliere **Avanti**.

1. Nella pagina **Configura il nuovo progetto** immettere un nome e quindi scegliere **Crea**.

1. Nella pagina **Crea una nuova applicazione Web ASP.NET Core** selezionare **ASP.NET Core 2.1** nel menu a discesa in alto e quindi scegliere **Crea**.

## <a name="explore-the-ide"></a>Esplorare l'IDE

1. Nella barra degli strumenti **Esplora soluzioni** espandere la cartella **Controller** e quindi scegliere **ValuesController.fs** per aprirlo nell'editor.

   ![Screenshot dell'Esplora soluzioni con la cartella Controllers espansa in un progetto API Web F#.](../ide/media/hello-world-fs-sln-explorer.png)

1. A questo punto, modificare il membro `Get()` come segue:

   ```fsharp
   [<HttpGet>]
   member this.Get() =
       let values = [|"Hello"; "World"; "First F#/ASP.NET Core web API!"|]
       ActionResult<string[]>(values)
   ```

Il codice è semplice. Una matrice di valori F# viene associata al nome `values` e quindi passata al framework MVC ASP.NET Core come `ActionResult`. ASP.NET Core si occupa di tutto il resto.

Il codice dovrebbe essere simile al seguente nell'editor:

![Screenshot che mostra il codice modificato per il membro Get in ValuesController.fs.](../ide/media/hello-world-fs-get-member.png)

## <a name="run-the-application"></a>Eseguire l'applicazione

1. Premere **CTRL** + **F5** per eseguire l'applicazione e aprirla in un Web browser.

1. La pagina dovrebbe passare alla route `/api/values`, ma in caso contrario, immettere `https://localhost:44396/api/values` nel browser.

Il Web browser visualizzerà ora codice JSON corrispondente a quanto digitato in precedenza.

::: moniker-end

::: moniker range=">=vs-2022"

1. Aprire Visual Studio.

1. Nella finestra iniziale scegliere **Crea un nuovo progetto.**

1. Nella finestra **Crea un nuovo progetto** digitare **f# web** nella casella di ricerca oppure usare i filtri del linguaggio, della piattaforma e del tipo di progetto per perfezionare l'elenco. Selezionare il **ASP.NET Core di progetto API Web** e quindi scegliere **Avanti.**

1. Nella finestra **Configura il nuovo progetto** immettere un nome Project **e** quindi selezionare **Avanti.**

1. Nella finestra **Informazioni aggiuntive** verificare che nel campo **Framework** sia visualizzato **.NET 6.0** e quindi scegliere **Crea.**

## <a name="explore-the-ide"></a>Esplorare l'IDE

1. Nella barra **Esplora soluzioni** espandere la **cartella Controller** e quindi **scegliere WeatherForecast.fs** per aprirlo nell'editor.

   :::image type="content" source="media/vs-2022/hello-world-fs-sln-explorer.png" alt-text="Screenshot che mostra la Esplora soluzioni con la cartella Controllers espansa in un progetto API Web F#.":::

1. Modificare quindi l'esempio `Get()` di membro esistente in modo che corrisponda al codice seguente:

   ```fsharp
   [<HttpGet>]
   member this.Get() =
       let values = [|"Hello"; "World"; "First F#/ASP.NET Core web API!"|]
       ActionResult<string[]>(values)
   ```

Il codice è semplice. Una matrice di valori F# viene associata al nome `values` e quindi passata al framework MVC ASP.NET Core come `ActionResult`. ASP.NET Core si occupa di tutto il resto.

Il codice dovrebbe essere simile al seguente nell'editor:

:::image type="content" source="media/vs-2022//hello-world-fs-get-member.png" alt-text="Screenshot che mostra il codice modificato per il membro Get in WeatherForecast.fs.":::

## <a name="run-the-application"></a>Eseguire l'applicazione

Premere **CTRL** + **F5** per eseguire l'applicazione e aprirla in un Web browser. 

> [!NOTE]
> Se viene visualizzato un messaggio che chiede se si vuole  accettare un certificato SSL Express iis,  scegliere Sì per visualizzare il codice in un Web browser e quindi scegliere Sì se viene visualizzato un messaggio di avviso di sicurezza di follow-up.

Visual Studio viene avviata una finestra del browser che visualizza json corrispondente al messaggio "Hello World" aggiunto in precedenza.

::: moniker-end

## <a name="next-steps"></a>Passaggi successivi

La guida introduttiva è stata completata. Ci auguriamo che l'utente abbia appreso informazioni su F#, ASP.NET Core e sull'IDE Visual Studio. Per visualizzare l'app in esecuzione in un server pubblico, selezionare il pulsante seguente.

> [!div class="nextstepaction"]
> [Distribuire l'app nel servizio app di Azure](../deployment/quickstart-deploy-to-azure.md)

Per altre informazioni su F#, vedere la [Guida a F#](/dotnet/fsharp/index) ufficiale.
