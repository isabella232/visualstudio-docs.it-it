---
title: 'Guida introduttiva: Creare un servizio Web ASP.NET Core in F#'
description: Informazioni dettagliate su come creare un servizio Web ASP.NET Core in Visual Studio con F#.
ms.date: 08/24/2018
ms.topic: quickstart
ms.custom: vs-acquisition
author: cartermp
ms.author: phcart
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- FSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: ad45a9cefa183919f164e8e9f48667fdacfd3e2fe5721863dbfd0b444d3dc467
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121372908"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-service-in-f"></a>Avvio rapido: Usare Visual Studio per creare il primo ASP.NET Core web in F\#

In questa introduzione di 5-10 minuti a F# in Visual Studio verrà creata un'applicazione Web ASP.NET Core F#.

::: moniker range="vs-2017"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2022"

Se non è già stato installato Visual Studio 2022 Preview, passare alla pagina dei download di [Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) per installarlo gratuitamente.

::: moniker-end

## <a name="create-a-project"></a>Creare un progetto

Per prima cosa, verrà creato un progetto API Web ASP:NET Core. Il tipo di progetto viene specificato con i file di modello che costituiscono un servizio Web funzionale, prima ancora di aggiungere alcun elemento.

::: moniker range="vs-2017"

1. Aprire Visual Studio.

2. Nella barra dei menu superiore scegliere **File** > **Nuovo** > **Project**.

3. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **Visual F#** e quindi scegliere **Web**. Nel riquadro centrale, scegliere **Applicazione Web ASP.NET Core**, quindi scegliere **OK**.

     Se non viene visualizzata la categoria dei modelli di progetto **.NET Core** scegliere il collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo ASP.NET e Web**, quindi scegliere **Cambia**.

     ![Carico di lavoro ASP.NET nel programma di installazione di Visual Studio](../ide/media/quickstart-aspnet-workload.png)

4.Nella finestra di dialogo **Nuova applicazione Web ASP.NET Core** selezionare **ASP.NET Core 2.1** nel menu a discesa in alto. Se non viene visualizzato **ASP.NET Core 2.1** nell'elenco, installarlo seguendo il **collegamento Download** visualizzato in una barra gialla nella parte superiore della finestra di dialogo. Scegliere **OK.**

::: moniker-end

::: moniker range=">=vs-2019"

1. Aprire Visual Studio.

2. Nella finestra iniziale scegliere **Crea un nuovo progetto.**

3. Nella pagina **Crea un nuovo progetto** digitare **f# web** nella casella di ricerca e quindi scegliere il modello di progetto **Applicazione Web ASP.NET Core**. Scegliere **Avanti**.

4. Nella pagina **Configura il nuovo progetto** immettere un nome e quindi scegliere **Crea**.

5. Nella pagina **Crea una nuova applicazione Web ASP.NET Core** selezionare **ASP.NET Core 2.1** nel menu a discesa in alto e quindi scegliere **Crea**.

::: moniker-end

## <a name="explore-the-ide"></a>Esplorare l'IDE

1. Nella barra degli strumenti **Esplora soluzioni** espandere la cartella **Controller** e quindi scegliere **ValuesController.fs** per aprirlo nell'editor.

   ![Esplora soluzioni con la cartella Controller espansa nel progetto API Web F#](../ide/media/hello-world-fs-sln-explorer.png)

2. A questo punto, modificare il membro `Get()` come segue:

   ```fsharp
   [<HttpGet>]
   member this.Get() =
       let values = [|"Hello"; "World"; "First F#/ASP.NET Core web API!"|]
       ActionResult<string[]>(values)
   ```

Il codice è semplice. Una matrice di valori F# viene associata al nome `values` e quindi passata al framework MVC ASP.NET Core come `ActionResult`. ASP.NET Core si occupa di tutto il resto.

Il codice dovrebbe essere simile al seguente nell'editor:

![Membro Get modificato](../ide/media/hello-world-fs-get-member.png)

## <a name="run-the-application"></a>Eseguire l'applicazione

1. Premere **CTRL** + **F5** per eseguire l'applicazione e aprirla in un Web browser.

2. La pagina dovrebbe passare alla route `/api/values`, ma in caso contrario, immettere `https://localhost:44396/api/values` nel browser.

Il Web browser visualizzerà ora codice JSON corrispondente a quanto digitato in precedenza.

## <a name="next-steps"></a>Passaggi successivi

La guida introduttiva è stata completata. Ci auguriamo che sia stata utile per l'apprendimento dell'uso di F#, ASP.NET Core e dell'IDE di Visual Studio. Per visualizzare l'app in esecuzione in un server pubblico, selezionare il pulsante seguente.

> [!div class="nextstepaction"]
> [Distribuire l'app nel servizio app di Azure](../deployment/quickstart-deploy-to-azure.md)

Per altre informazioni su F#, vedere la [Guida a F#](/dotnet/fsharp/index) ufficiale.
