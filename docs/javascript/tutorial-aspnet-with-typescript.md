---
title: Creare un'app ASP.NET Core con TypeScript
description: In questa esercitazione si creerà un'app usando ASP.NET Core e TypeScript
ms.date: 03/25/2021
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: ce27b8fdd73c1fcc001861a9b1fb7c2e9e4f4058
ms.sourcegitcommit: 00e16b9afe6b22ba0591e4d0d92690544e6d4357
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/26/2021
ms.locfileid: "105616987"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>Esercitazione: creare un'app ASP.NET Core con TypeScript in Visual Studio

In questa esercitazione per lo sviluppo di Visual Studio ASP.NET Core e TypeScript si crea una semplice applicazione Web, si aggiunge un codice TypeScript e quindi si esegue l'app.

::: moniker range="vs-2017"

Se Visual Studio non è ancora installato, passare alla pagina dei [download di Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se Visual Studio non è ancora installato, passare alla pagina dei [download di Visual Studio](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

In questa esercitazione verranno illustrate le procedure per:
> [!div class="checklist"]
> * Creare un progetto ASP.NET Core
> * Aggiungere il pacchetto NuGet per il supporto di TypeScript
> * Aggiungere codice TypeScript
> * Eseguire l'app
> * Aggiungere una libreria di terze parti con NPM

## <a name="prerequisites"></a>Prerequisiti

* È necessario che Visual Studio sia installato e che il carico di lavoro sviluppo Web ASP.NET.

    ::: moniker range=">=vs-2019"
    Se Visual Studio 2019 non è ancora installato, passare alla pagina dei [download di Visual Studio](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Se Visual Studio 2017 non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente.
    ::: moniker-end

    Se è necessario installare il carico di lavoro ma si dispone già di Visual Studio, passare a **strumenti**  >  **Ottieni strumenti e funzionalità...**, che consente di aprire la programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo ASP.NET e Web**, quindi scegliere **Cambia**.

## <a name="create-a-new-aspnet-core-mvc-project"></a>Creare un nuovo progetto MVC ASP.NET Core

Visual Studio gestisce i file per una sola applicazione in un *progetto*. Il progetto include i file di configurazione, le risorse e il codice sorgente.

>[!NOTE]
> Per iniziare con un progetto di ASP.NET Core vuoto e aggiungere un front-end TypeScript, vedere invece [ASP.NET Core con typescript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html) .

In questa esercitazione si inizia con un semplice progetto che contiene il codice per un'app MVC ASP.NET Core.

1. Aprire Visual Studio.

1. Creare un nuovo progetto.

    ::: moniker range=">=vs-2019"
    In Visual Studio 2019, scegliere **Crea un nuovo progetto** nella finestra Start. Se la finestra di avvio non è aperta, scegliere  >  **finestra di avvio** file. Digitare **app Web**, scegliere **C#** come lingua, quindi scegliere **ASP.NET Core applicazione Web (Model-View-Controller)**, quindi scegliere **Avanti**. Nella schermata successiva assegnare un nome al progetto, quindi scegliere **Avanti**.

    Scegliere il Framework di destinazione consigliato (.NET Core 3,1) o .NET 5, quindi scegliere **Crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dalla barra dei menu in alto scegliere **file**  >  **nuovo**  >  **progetto**. Nel riquadro sinistro della finestra di dialogo **nuovo progetto** espandere **Visual C#**, quindi scegliere **.NET Core**. Nel riquadro centrale scegliere **ASP.NET Core applicazione Web-C#**, quindi scegliere **OK**.

    Nella finestra di dialogo visualizzata selezionare **applicazione Web (Model-View-Controller)** nella finestra di dialogo, quindi scegliere **Crea** (o **OK**).

    ![Scegliere il modello MVC](../javascript/media/aspnet-core-ts-mvc-template.png)
    ::: moniker-end
    Se non viene visualizzato il modello di progetto **applicazione Web di ASP.NET Core** , è necessario aggiungere il carico di lavoro **sviluppo di ASP.NET e Web** . Per istruzioni dettagliate, vedere i [Prerequisiti](#prerequisites).

    Visual Studio crea la nuova soluzione e apre il progetto nel riquadro destro.

## <a name="add-some-code"></a>Aggiungere codice

1. In Esplora soluzioni (riquadro a destra). fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Gestisci pacchetti NuGet**. Nella scheda **Sfoglia** cercare **Microsoft. typescript. MSBuild**, quindi fare clic su **Installa** a destra per installare il pacchetto.

   ![Aggiungi pacchetto NuGet](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio aggiunge il pacchetto NuGet nel nodo **dipendenze** in Esplora soluzioni.

1. Fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **aggiungi > nuovo elemento**. Scegliere il **file di configurazione TYPESCRIPT JSON** e quindi fare clic su **Aggiungi**.

   Visual Studio aggiunge il *tsconfig.jsnel* file alla radice del progetto. È possibile usare questo file per [configurare le opzioni](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) per il compilatore typescript.

1. Aprire *tsconfig.js* e sostituire il codice predefinito con il codice seguente:

   ```json
   {
     "compileOnSave": true,
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "wwwroot/js"
     },
     "include": [
       "scripts/**/*"
     ]
   }
   ```

   L'opzione *outDir* specifica la cartella di output per i file JavaScript semplici che vengono traspilati dal compilatore typescript.

   Questa configurazione offre un'introduzione di base all'uso di TypeScript. In altri scenari, ad esempio quando si usa [Gulp o Webpack](https://www.typescriptlang.org/docs/handbook/asp-net-core.html), potrebbe essere necessario un percorso intermedio diverso per i file JavaScript transpiled, a seconda degli strumenti e delle preferenze di configurazione, invece di *wwwroot/JS*.

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **aggiungi > nuova cartella**. Usare gli *script* di nome per la nuova cartella.

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

    Per eseguire il test, rimuovere `.lastName` dalla `greeter` funzione, quindi ridigitare "." e visualizzare IntelliSense.

    ![Visualizza IntelliSense](../javascript/media/aspnet-core-ts-intellisense.png)

    Selezionare questa finestra `lastName` per aggiungere di nuovo il cognome al codice.

1. Aprire la cartella *views/Home* e quindi aprire *index. cshtml*.

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

1. Aggiungere il seguente riferimento allo script prima della chiamata a `@RenderSection("Scripts", required: false)` :

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>Compilare l'applicazione

1. Scegliere **compila > Compila soluzione**.

   Sebbene l'app venga compilata automaticamente quando viene eseguita, è opportuno esaminare qualcosa che si verifica durante il processo di compilazione.

1. Aprire la cartella *wwwroot/JS* e trovare due nuovi file, *app.js* e il file di mapping di origine, *app.js. map*. Questi file vengono generati dal compilatore TypeScript.

   Per il debug sono necessari i file di mapping di origine.

## <a name="run-the-application"></a>Eseguire l'applicazione

1. Premere **F5** (**Debug** > **Avvia debug**) per eseguire l'applicazione.

    L'app viene aperta in un browser.

    Nella finestra del browser viene visualizzata l'intestazione **Welcome** e il pulsante **Click me** .

    ![ASP.NET Core con TypeScript](../javascript/media/aspnet-core-ts-running-app.png)

1. Fare clic sul pulsante per visualizzare il messaggio specificato nel file TypeScript.

## <a name="debug-the-application"></a>Eseguire il debug dell'applicazione

1. Impostare un punto di interruzione nella `greeter` funzione in `app.ts` facendo clic sul margine sinistro nell'editor di codice.

    ![Imposta punto di interruzione](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. Premere **F5** per eseguire l'applicazione.

   Potrebbe essere necessario rispondere a un messaggio per abilitare il debug degli script.

   L'applicazione viene sospesa in corrispondenza del punto di interruzione. A questo punto, è possibile esaminare le variabili e usare le funzionalità del debugger.

## <a name="add-typescript-support-for-a-third-party-library"></a>Aggiungere il supporto TypeScript per una libreria di terze parti

1. Seguire le istruzioni in [Gestione pacchetti NPM](../javascript/npm-package-management.md#aspnet-core-projects) per aggiungere un `package.json` file al progetto. Viene aggiunto il supporto NPM al progetto.

   >[!NOTE]
   > Per ASP.NET Core progetti, è anche possibile usare [Gestione librerie](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1&preserve-view=true) o Yarn anziché NPM per installare i file CSS e JavaScript sul lato client.

1. In questo esempio, aggiungere un file di definizione TypeScript per jQuery al progetto. Includere quanto segue nel file di *package.js* .

   ```json
   "devDependencies": {
      "@types/jquery": "3.3.33"
   }
   ```

   Viene aggiunto il supporto TypeScript per jQuery. La libreria jQuery è già inclusa nel modello di progetto MVC (cercare in wwwroot/lib in Esplora soluzioni). Se si usa un modello diverso, potrebbe essere necessario includere anche il pacchetto NPM NPM.

1. Se il pacchetto in Esplora soluzioni non è installato, fare clic con il pulsante destro del mouse sul nodo NPM e scegliere **Ripristina pacchetti**.

   >[!NOTE]
   > In alcuni scenari Esplora soluzioni possibile indicare che un pacchetto NPM non è sincronizzato con *package.js* a causa di un problema noto descritto [qui](https://github.com/aspnet/Tooling/issues/479). È ad esempio possibile che il pacchetto venga visualizzato come non installato al momento dell'installazione. Nella maggior parte dei casi, è possibile aggiornare Esplora soluzioni eliminando *package.js*, riavviando Visual Studio e aggiungendo nuovamente il *package.jssul* file come descritto in precedenza in questo articolo.

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sulla cartella script e scegliere **Aggiungi**  >  **nuovo elemento**.

1. Scegliere **file typescript**, digitare *Library. TS*, quindi scegliere **Aggiungi**.

1. In *Library. TS* aggiungere il codice seguente.

   ```ts
   var jqtest = {
      showMsg: function (): void {
         let v: any = jQuery.fn.jquery.toString();
         let content: any = $("#ts-example-2")[0].innerHTML;
         alert(content.toString() + " " + v + "!!");
         $("#ts-example-2")[0].innerHTML = content + " " + v + "!!";
      }
   };

   jqtest.showMsg();
   ```

   Per semplicità, questo codice visualizza un messaggio usando jQuery e un avviso.

   Con le definizioni di tipo TypeScript per jQuery aggiunto, si ottiene il supporto IntelliSense sugli oggetti jQuery quando si digita "." dopo un oggetto jQuery, come illustrato di seguito.

   ![IntelliSense per jQuery](../javascript/media/aspnet-core-ts-jquery-intellisense.png)

1. In _Layout. cshtml aggiornare i riferimenti agli script da includere `library.js` .

   ```html
   <script src="~/js/app.js"></script>
   <script src="~/js/library.js"></script>
   ```

1. In index. cshtml aggiungere il codice HTML seguente alla fine del file.

   ```html
   <div>
      <p id="ts-example-2">jQuery version is:</p>
   </div>
   ```

1. Premere **F5** (**Debug** > **Avvia debug**) per eseguire l'applicazione.

    L'app viene aperta nel browser.

    Fare clic su **OK** nell'avviso per visualizzare la pagina aggiornata alla **versione jQuery: 3.3.1!!**.

    ![esempio di jQuery](../javascript/media/aspnet-core-ts-jquery-example.png)

## <a name="next-steps"></a>Passaggi successivi

È possibile ottenere altre informazioni sull'uso di TypeScript con ASP.NET Core. Se si è interessati alla programmazione AngularJS in Visual Studio, è possibile usare l' [estensione del servizio di linguaggio AngularJS](https://devblogs.microsoft.com/visualstudio/angular-language-service-for-visual-studio) per Visual Studio.

> [!div class="nextstepaction"]
> [ASP.NET Core e TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)

> [!div class="nextstepaction"]
> [Estensione del servizio di linguaggio AngularJS](https://devblogs.microsoft.com/visualstudio/angular-language-service-for-visual-studio)
