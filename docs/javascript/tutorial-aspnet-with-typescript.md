---
title: Creare un'app ASP.NET Core con TypeScript
description: In questa esercitazione si creerà un'app usando ASP.NET Core e TypeScript
ms.date: 01/03/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 8d733c41e2833eeca2a8bf8c68f5e329f0af723c
ms.sourcegitcommit: 0d8488329263cc0743a89d43f6de863028e982ff
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/06/2020
ms.locfileid: "75685307"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>Esercitazione: creare un'app ASP.NET Core con TypeScript in Visual Studio

In questa esercitazione per lo sviluppo di Visual Studio ASP.NET Core e TypeScript si crea una semplice applicazione Web, si aggiunge un codice TypeScript e quindi si esegue l'app. 

::: moniker range="vs-2017"

Se non è ancora stato installato Visual Studio, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se non è ancora stato installato Visual Studio, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

In questa esercitazione si imparerà a:
> [!div class="checklist"]
> * Creare un progetto di ASP.NET Core
> * Aggiungere il pacchetto NuGet per il supporto di TypeScript
> * Aggiungere codice TypeScript
> * Eseguire l'app

## <a name="prerequisites"></a>Prerequisiti

* È necessario che Visual Studio sia installato e che il carico di lavoro sviluppo Web ASP.NET.

    ::: moniker range=">=vs-2019"
    Se Visual Studio 2019 non è ancora installato, accedere alla pagina  [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/)  per installarlo gratuitamente.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Se Visual Studio 2017 non è ancora installato, accedere alla pagina  [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/)  per installarlo gratuitamente.
    ::: moniker-end

    Se occorre installare il carico di lavoro, ma si ha già Visual Studio, passare a **Strumenti** > **Ottieni strumenti e funzionalità**, che apre il programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo ASP.NET e Web**, quindi scegliere **Cambia**.

## <a name="create-a-new-aspnet-core-mvc-project"></a>Creare un nuovo progetto MVC ASP.NET Core

Visual Studio gestisce i file per una sola applicazione in un *progetto*. Il progetto include i file di configurazione, le risorse e il codice sorgente.

In questa esercitazione si inizia con un semplice progetto che contiene il codice per un'app MVC ASP.NET Core.

1. Apri Visual Studio.

1. Creare un nuovo progetto.

    ::: moniker range=">=vs-2019"
    Premere **ESC** per chiudere la finestra iniziale. Digitare **CTRL + Q** per aprire la casella di ricerca, digitare **ASP.NET**, quindi scegliere **ASP.NET Core applicazione Web C#-** . Nella finestra di dialogo visualizzata scegliere **Crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Sulla barra dei menu in alto scegliere **File** > **Nuovo** > **Progetto**. Nel riquadro di sinistra della finestra di dialogo **Nuovo progetto** espandere **JavaScript**, quindi selezionare **Node.js**. Nel riquadro centrale scegliere **ASP.NET Core applicazione C#Web** , quindi scegliere **OK**.
    ::: moniker-end
    Se non viene visualizzato il modello di progetto **applicazione Web di ASP.NET Core** , è necessario aggiungere il carico di lavoro **sviluppo di ASP.NET e Web** . Per istruzioni dettagliate, vedere i [Prerequisiti](#prerequisites).

1. Dopo aver scelto **Crea**, selezionare **applicazione Web (Model-View-Controller)** nella finestra di dialogo, quindi scegliere **Crea**.

   ![Scegliere il modello MVC](../javascript/media/aspnet-core-ts-mvc-template.png)

    Visual Studio crea la nuova soluzione e apre il progetto nel riquadro destro.

## <a name="add-some-code"></a>Aggiungere codice

1. In Esplora soluzioni (riquadro a destra). fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Gestisci pacchetti NuGet**. Nella scheda **Sfoglia** cercare **Microsoft. typescript. MSBuild**, quindi fare clic su **Installa** a destra per installare il pacchetto.

   ![Aggiungi pacchetto NuGet](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio aggiunge il pacchetto NuGet nel nodo **dipendenze** in Esplora soluzioni.

   > [!NOTE]
   > Questa esercitazione richiede il pacchetto NuGet. In alternativa, è possibile usare il [pacchetto NPM typescript](https://www.npmjs.com/package/typescript)nelle proprie app.

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **aggiungi > nuova cartella**. Usare gli *script* di nome per la nuova cartella.

1. Fare clic con il pulsante destro del mouse sulla cartella *script* e scegliere **Aggiungi > nuovo elemento**. Scegliere il **file di configurazione TYPESCRIPT JSON**e quindi fare clic su **Aggiungi**.

   Visual Studio aggiunge il file *tsconfig. JSON* alla cartella *Scripts* . È possibile usare questo file per [configurare le opzioni](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) per il compilatore typescript.

1. Aprire *tsconfig. JSON* e sostituire il codice predefinito con il codice seguente:

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "../wwwroot/js"
     },
     "exclude": [
       "node_modules",
       "wwwroot"
     ]
   }
   ```

   L'opzione *outDir* specifica la cartella di output per i file JavaScript del piano che vengono traspilati dal compilatore typescript.

   Questa configurazione offre un'introduzione di base all'uso di TypeScript. In altri scenari, ad esempio quando si usa [Gulp o Webpack](https://www.typescriptlang.org/docs/handbook/asp-net-core.html), potrebbe essere necessario un percorso intermedio diverso per i file JavaScript transpiled, a seconda degli strumenti e delle preferenze di configurazione, anziché *. /Wwwroot/JS*.

1. Fare clic con il pulsante destro del mouse sulla cartella *script* e scegliere **Aggiungi > nuovo elemento**. Scegliere il **file typescript**, digitare il nome *app. TS* per il nome file, quindi fare clic su **Aggiungi**.

   Visual Studio aggiunge *app. TS* alla cartella *Scripts* .

1. Aprire *app. TS* e aggiungere il codice typescript seguente.

    ```ts
    function TSButton() {
       let name: string = "Fred";
       document.getElementById("ts-example").innerHTML = greeter(user);
    }

    class Student {
       fullName: string;
       constructor(public firstName: string, public middleInitial: string, public lastName: string) {
           this.fullName = firstName + " " + middleInitial + " " + lastName;
       }
    }

    interface Person {
       firstName: string;
       lastName: string;
    }

    function greeter(person: Person) {
       return "Hello, " + person.firstName + " " + person.lastName;
    }

    let user = new Student("Fred", "M.", "Smith");
    ```

    Visual Studio fornisce il supporto IntelliSense per il codice TypeScript.

    Per eseguire il test, rimuovere `.lastName` dalla funzione `greeter`, quindi ridigitare "." e visualizzare IntelliSense.

    ![Visualizza IntelliSense](../javascript/media/aspnet-core-ts-intellisense.png)

    Selezionare `lastName` per aggiungere di nuovo il cognome al codice.

1. Aprire la cartella *views/Home* e quindi aprire *index. html*.

1. Aggiungere il codice HTML seguente alla fine del file.

    ```html
    <div id="ts-example">
        <br />
        <button type="button" class="btn btn-primary btn-md" onclick="TSButton()">
            Click Me
        </button>
    </div>
    ```

1. Aprire la cartella *Views/Shared* , quindi aprire *_Layout. cshtml*.

1. Aggiungere il riferimento allo script seguente prima della chiamata a `@RenderSection("Scripts", required: false)`:

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>Compilare l'applicazione

1. Scegliere **compila > Compila soluzione**.

   Sebbene l'app venga compilata automaticamente quando viene eseguita, è opportuno esaminare qualcosa che si verifica durante il processo di compilazione.

1. Aprire la cartella *wwwroot/JS* e trovare due nuovi file, *app. js* e il file di mappa di origine, *app. js. map*. Questi file vengono generati dal compilatore TypeScript.

   Per il debug sono necessari i file di mapping di origine.

## <a name="run-the-application"></a>Esecuzione dell'applicazione

1. Premere **F5** (**Debug** > **Avvia debug**) per eseguire l'applicazione.

    L'app viene aperta in un browser.

    Nella finestra del browser viene visualizzata l'intestazione **Welcome** e il pulsante **Click me** .

    ![ASP.NET Core con TypeScript](../javascript/media/aspnet-core-ts-running-app.png)

1. Fare clic sul pulsante per visualizzare il messaggio specificato nel file TypeScript.

## <a name="debug-the-application"></a>Eseguire il debug dell'applicazione

1. Impostare un punto di interruzione nella funzione `greeter` in `app.ts` facendo clic sul margine sinistro nell'editor di codice.

    ![Imposta punto di interruzione](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. Premere **F5** per eseguire l'applicazione.

   Potrebbe essere necessario rispondere a un messaggio per abilitare il debug degli script.

   L'applicazione viene sospesa in corrispondenza del punto di interruzione. A questo punto, è possibile esaminare le variabili e usare le funzionalità del debugger.

## <a name="next-steps"></a>Passaggi successivi

È possibile ottenere altre informazioni sull'uso di TypeScript con ASP.NET Core.

> [!div class="nextstepaction"]
> [ASP.NET Core e TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)
