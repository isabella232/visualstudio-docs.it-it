---
title: Creare un'app ASP.NET Core con TypeScript
description: In questa esercitazione si crea un'app usando ASP.NET Core e TypeScript
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
ms.openlocfilehash: 9a2d362bc9fd22f7bb1db2fa005534f2f67e3155
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760965"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>Esercitazione: Creare un'app ASP.NET Core con TypeScript in Visual Studio

In questa esercitazione per Visual Studio sviluppo ASP.NET Core e TypeScript, si crea una semplice applicazione Web, si aggiunge codice TypeScript e quindi si esegue l'app.

::: moniker range="vs-2017"

Se non è già stato installato Visual Studio, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range=">=vs-2019"

Se non è già stato installato Visual Studio, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

In questa esercitazione verranno illustrate le procedure per:
> [!div class="checklist"]
> * Creare un progetto ASP.NET Core
> * Aggiungere il pacchetto NuGet per il supporto TypeScript
> * Aggiungere codice TypeScript
> * Eseguire l'app
> * Aggiungere una libreria di terze parti usando npm

## <a name="prerequisites"></a>Prerequisiti

* È necessario aver installato Visual Studio e il carico ASP.NET di sviluppo Web.

    ::: moniker range=">=vs-2019"
    Se non è già stato installato Visual Studio 2019, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Se Visual Studio 2017 non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente.
    ::: moniker-end

    Se è necessario installare il carico di lavoro ma Visual Studio, passare a Strumenti Ottieni strumenti e  >  **funzionalità...**, che apre la Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo ASP.NET e Web**, quindi scegliere **Cambia**.

## <a name="create-a-new-aspnet-core-mvc-project"></a>Creare un nuovo progetto ASP.NET Core MVC

Visual Studio gestisce i file per una sola applicazione in un *progetto*. Il progetto include i file di configurazione, le risorse e il codice sorgente.

>[!NOTE]
> Per iniziare con un progetto ASP.NET Core vuoto e aggiungere un front-end TypeScript, vedere [ASP.NET Core con TypeScript.](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)

In questa esercitazione si inizia con un semplice progetto contenente il codice per un'app ASP.NET Core MVC.

1. Aprire Visual Studio.

1. Creare un nuovo progetto.

    ::: moniker range=">=vs-2019"
    In Visual Studio 2019 scegliere **Crea un nuovo progetto** nella finestra iniziale. Se la finestra iniziale non è aperta, scegliere **Finestra**  >  **iniziale file**. Digitare **app** Web, scegliere **C#** come linguaggio, quindi **scegliere ASP.NET Core Web Application (Model-View-Controller)** e quindi **scegliere Avanti.** Nella schermata successiva assegnare un nome al progetto e quindi scegliere **Avanti.**

    Scegliere il framework di destinazione consigliato (.NET Core 3.1) o .NET 5 e quindi **scegliere Crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Nella barra dei menu superiore scegliere **File**  >  **nuovo**  >  **progetto**. Nel riquadro sinistro della finestra di dialogo **Nuovo** progetto espandere **Visual C#** e quindi **scegliere .NET Core.** Nel riquadro centrale scegliere ASP.NET **Core Web Application - C#** e quindi scegliere **OK.**

    Nella finestra di dialogo visualizzata selezionare **Applicazione Web (Model-View-Controller)** nella finestra di dialogo e quindi scegliere **Crea** (o **OK).**

    ![Scegliere il modello MVC](../javascript/media/aspnet-core-ts-mvc-template.png)
    ::: moniker-end
    Se il modello di progetto applicazione **Web ASP.NET Core** non è visualizzato, è necessario aggiungere il carico di lavoro ASP.NET sviluppo **Web.** Per istruzioni dettagliate, vedere i [Prerequisiti](#prerequisites).

    Visual Studio crea la nuova soluzione e apre il progetto nel riquadro destro.

## <a name="add-some-code"></a>Aggiungere codice

1. In Esplora soluzioni (riquadro destro). Fare clic con il pulsante destro del mouse sul nodo del progetto **e scegliere Gestisci pacchetti NuGet**. Nella scheda **Sfoglia** cercare **Microsoft.TypeScript.MSBuild** e quindi fare clic **su** Installa a destra per installare il pacchetto.

   ![Aggiungere un pacchetto NuGet](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio aggiunge il pacchetto NuGet nel nodo **Dipendenze** in Esplora soluzioni.

1. Fare clic con il pulsante destro del mouse sul nodo del **progetto e scegliere Aggiungi > nuovo elemento**. Scegliere il **file di configurazione JSON TypeScript** e quindi fare clic su **Aggiungi**.

   Visual Studio aggiunge il *tsconfig.jsfile* alla radice del progetto. È possibile usare questo file per [configurare le opzioni per](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) il compilatore TypeScript.

1. Aprire *tsconfig.jse* sostituire il codice predefinito con il codice seguente:

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

   *L'opzione outDir* specifica la cartella di output per i file JavaScript semplici trascritti dal compilatore TypeScript.

   Questa configurazione fornisce un'introduzione di base all'uso di TypeScript. In altri scenari, ad esempio quando si usa gulp o [webpack,](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)potrebbe essere necessario un percorso intermedio diverso per i file JavaScript traslati, a seconda degli strumenti e delle preferenze di configurazione, anziché *wwwroot/js*.

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi > nuova cartella**. Usare gli *script dei nomi* per la nuova cartella.

1. Fare clic con il pulsante destro *del mouse* sulla cartella scripts e scegliere Aggiungi > **nuovo elemento**. Scegliere il **file TypeScript,** digitare il nome *app.ts per* il nome del file e quindi fare clic su **Aggiungi**.

   Visual Studio aggiunge *app.ts* alla *cartella scripts.*

1. Aprire *app.ts e* aggiungere il codice TypeScript seguente.

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

    Visual Studio supporto IntelliSense per il codice TypeScript.

    Per testare questa operazione, rimuovere dalla funzione, digitare nuovamente "." e viene `.lastName` visualizzato `greeter` IntelliSense.

    ![Visualizzare IntelliSense](../javascript/media/aspnet-core-ts-intellisense.png)

    Selezionare `lastName` questa opzione per aggiungere di nuovo il cognome al codice.

1. Aprire la *cartella Views/Home* e quindi *index.cshtml*.

1. Aggiungere il codice HTML seguente alla fine del file.

    ```html
    <div id="ts-example">
        <br />
        <button type="button" class="btn btn-primary btn-md" onclick="TSButton()">
            Click Me
        </button>
    </div>
    ```

1. Aprire la *cartella Views/Shared* e quindi *_Layout.cshtml*.

1. Aggiungere il riferimento allo script seguente prima della chiamata a `@RenderSection("Scripts", required: false)` :

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>Compilare l'applicazione

1. Scegliere **Compila > Compila soluzione**.

   Anche se l'app viene compilata automaticamente quando viene eseguita, è necessario esaminare qualcosa che si verifica durante il processo di compilazione.

1. Aprire la *cartella wwwroot/js* e trovare due nuovi file, *app.js* e il file source map, *app.js.map*. Questi file vengono generati dal compilatore TypeScript.

   I file della mappa di origine sono necessari per il debug.

## <a name="run-the-application"></a>Eseguire l'applicazione

1. Premere **F5** (**Debug** > **Avvia debug**) per eseguire l'applicazione.

    L'app viene aperta in un browser.

    Nella finestra del browser verranno visualizzati **l'intestazione Benvenuto** e il pulsante Fare clic su **Di me.**

    ![ASP.NET Core con TypeScript](../javascript/media/aspnet-core-ts-running-app.png)

1. Fare clic sul pulsante per visualizzare il messaggio specificato nel file TypeScript.

## <a name="debug-the-application"></a>Eseguire il debug dell'applicazione

1. Impostare un punto di `greeter` interruzione nella funzione in `app.ts` facendo clic sul margine sinistro nell'editor di codice.

    ![Imposta punto di interruzione](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. Premere **F5 per** eseguire l'applicazione.

   Potrebbe essere necessario rispondere a un messaggio per abilitare il debug degli script.

   L'applicazione viene sospesa in corrispondenza del punto di interruzione. È ora possibile esaminare le variabili e usare le funzionalità del debugger.

## <a name="add-typescript-support-for-a-third-party-library"></a>Aggiungere il supporto TypeScript per una libreria di terze parti

1. Seguire le istruzioni in [Gestione pacchetti npm](../javascript/npm-package-management.md#aspnet-core-projects) per aggiungere un `package.json` file al progetto. Verrà aggiunto il supporto npm al progetto.

   >[!NOTE]
   > Per ASP.NET Core, è anche possibile usare [Library Manager](/aspnet/core/client-side/libman/) o yarn anziché npm per installare i file JavaScript e CSS sul lato client.

1. In questo esempio aggiungere un file di definizione TypeScript per jQuery al progetto. Includere quanto segue nel *package.jsfile.*

   ```json
   "devDependencies": {
      "@types/jquery": "3.3.33"
   }
   ```

   In questo modo viene aggiunto il supporto TypeScript per jQuery. La libreria jQuery stessa è già inclusa nel modello di progetto MVC (vedere wwwroot/lib in Esplora soluzioni). Se si usa un modello diverso, potrebbe essere necessario includere anche il pacchetto npm jquery.

1. Se il pacchetto in Esplora soluzioni non è installato, fare clic con il pulsante destro del mouse sul nodo npm e scegliere **Ripristina pacchetti**.

   >[!NOTE]
   > In alcuni scenari, Esplora soluzioni che un pacchetto npm non  è sincronizzato conpackage.jsa causa di un problema noto descritto [qui.](https://github.com/aspnet/Tooling/issues/479) Ad esempio, il pacchetto potrebbe essere visualizzato come non installato al momento dell'installazione. Nella maggior parte dei casi, è possibile aggiornare Esplora soluzioni eliminando *package.js* in , riavviando Visual Studio e aggiungendo nuovamente il *package.js* nel file come descritto in precedenza in questo articolo.

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sulla cartella scripts e scegliere **Aggiungi**  >  **nuovo elemento**.

1. Scegliere **File TypeScript**, libreria *dei tipi.ts* e scegliere **Aggiungi**.

1. In *library.ts* aggiungere il codice seguente.

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

   Dopo aver aggiunto le definizioni dei tipi TypeScript per jQuery, è possibile ottenere il supporto IntelliSense per gli oggetti jQuery quando si digita "." dopo un oggetto jQuery, come illustrato di seguito.

   ![IntelliSense per jquery](../javascript/media/aspnet-core-ts-jquery-intellisense.png)

1. In _Layout.cshtml aggiornare i riferimenti allo script in modo da includere `library.js` .

   ```html
   <script src="~/js/app.js"></script>
   <script src="~/js/library.js"></script>
   ```

1. In Index.cshtml aggiungere il codice HTML seguente alla fine del file.

   ```html
   <div>
      <p id="ts-example-2">jQuery version is:</p>
   </div>
   ```

1. Premere **F5** (**Debug** > **Avvia debug**) per eseguire l'applicazione.

    L'app viene aperta nel browser.

    Fare **clic su OK** nell'avviso per visualizzare che la pagina aggiornata alla versione di **jQuery è: 3.3.1").**

    ![Esempio di jquery](../javascript/media/aspnet-core-ts-jquery-example.png)

## <a name="next-steps"></a>Passaggi successivi

È possibile ottenere altre informazioni sull'uso di TypeScript con ASP.NET Core. Se si è interessati alla programmazione AngularJS in Visual Studio, è possibile usare l'estensione del servizio di linguaggio [AngularJS](https://devblogs.microsoft.com/visualstudio/angular-language-service-for-visual-studio) per Visual Studio.

> [!div class="nextstepaction"]
> [ASP.NET Core e TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)

> [!div class="nextstepaction"]
> [Estensione del servizio di linguaggio AngularJS](https://devblogs.microsoft.com/visualstudio/angular-language-service-for-visual-studio)
