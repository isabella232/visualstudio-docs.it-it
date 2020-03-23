---
title: Creare un'app ASP.NET Core con TypeScript
description: In questa esercitazione si crea un'app usando ASP.NET Core e TypeScript
ms.date: 03/16/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: e212aec6d2d3aa7e20cb0ca08c9ea604f32bb08c
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2020
ms.locfileid: "79988552"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>Esercitazione: Creare un'app ASP.NET Core con TypeScript in Visual StudioTutorial: Create an ASP.NET Core app with TypeScript in Visual Studio

In questa esercitazione per lo sviluppo di Visual Studio ASP.NET Core e TypeScript, si crea una semplice applicazione Web, si aggiunge codice TypeScript e quindi si esegue l'app. 

::: moniker range="vs-2017"

Se Visual Studio non è già stato installato, passare alla pagina dei download di [Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se Visual Studio non è già stato installato, passare alla pagina dei download di [Visual Studio](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

In questa esercitazione verranno illustrate le procedure per:
> [!div class="checklist"]
> * Creare un progetto ASP.NET CoreCreate an ASP.NET Core project
> * Aggiungere il pacchetto NuGet per il supporto TypeScriptAdd the NuGet package for TypeScript support
> * Aggiungere del codice TypeScript
> * Eseguire l'app
> * Aggiungere una libreria di terze parti utilizzando npm

## <a name="prerequisites"></a>Prerequisites

* È necessario disporre di Visual Studio installato e del carico di lavoro di sviluppo Web ASP.NET.

    ::: moniker range=">=vs-2019"
    Se non hai ancora installato Visual Studio 2019, vai alla pagina dei [download](https://visualstudio.microsoft.com/downloads/) di Visual Studio per installarlo gratuitamente.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Se non hai ancora installato Visual Studio 2017, vai alla pagina dei [download](https://visualstudio.microsoft.com/downloads/) di Visual Studio per installarlo gratuitamente.
    ::: moniker-end

    Se è necessario installare il carico di lavoro ma si dispone già di Visual Studio, passare a **Strumenti** > **Get Tools and Features...**, che apre il programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo ASP.NET e Web**, quindi scegliere **Cambia**.

## <a name="create-a-new-aspnet-core-mvc-project"></a>Creare un nuovo progetto MVC ASP.NET CoreCreate a new ASP.NET Core MVC project

Visual Studio gestisce i file per una sola applicazione in un *progetto*. Il progetto include i file di configurazione, le risorse e il codice sorgente.

>[!NOTE]
> Per iniziare con un progetto ASP.NET Core vuoto e aggiungere un frontend TypeScript, vedere invece [ASP.NET Core con TypeScript.](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)

In questa esercitazione si inizia con un progetto semplice contenente il codice per un'app MVC di ASP.NET Core.

1. Aprire Visual Studio.

1. Creare un nuovo progetto.

    ::: moniker range=">=vs-2019"
    Se la finestra di avvio non è aperta, scegliere**Finestra di avvio** **file** > . Nella finestra di avvio scegliere **Crea un nuovo progetto.** Nell'elenco a discesa del linguaggio, scegliere **C .** Nella casella di ricerca digitare **ASP.NET**, quindi scegliere **ASP.NETapplicazione Web di base**. Scegliere **Avanti**.

    Digitare un nome per il progetto e scegliere **Crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dalla barra dei menu superiore, scegliere **File** > **Nuovo** > **progetto**. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto,** espandere **Visual C,** quindi scegliere **.NET Core**. Nel riquadro centrale scegliere **ASP.NET Applicazione Web di base - C,** quindi scegliere **OK**.
    ::: moniker-end
    Se il modello di progetto **applicazione Web di ASP.NET** non viene visualizzato, è necessario aggiungere il carico di lavoro ASP.NET e di sviluppo **Web.** Per istruzioni dettagliate, vedere i [Prerequisiti](#prerequisites).

1. Nella finestra di dialogo visualizzata selezionare **Applicazione Web (Model-View-Controller)** nella finestra di dialogo, quindi scegliere **Crea** (o **OK).**

   ![Scegliere il modello MVC](../javascript/media/aspnet-core-ts-mvc-template.png)

    Visual Studio crea la nuova soluzione e apre il progetto nel riquadro destro.

## <a name="add-some-code"></a>Aggiungere codice

1. In Esplora soluzioni (riquadro destro). Fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Gestisci pacchetti NuGet**. Nella scheda **Sfoglia** cercare **Microsoft.TypeScript.MSBuild**, quindi fare clic su **Installa** a destra per installare il pacchetto.

   ![Aggiungi pacchetto NuGet](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio aggiunge il pacchetto NuGet nel nodo **Dipendenze** in Esplora soluzioni.

   > [!NOTE]
   > Questa esercitazione richiede il pacchetto NuGet.This tutorial requires the NuGet package. In alternativa, nelle tue app, puoi usare il [pacchetto TypeScript npm](https://www.npmjs.com/package/typescript).

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi > nuova cartella**. Utilizzare gli script dei *nomi* per la nuova cartella.

1. Fare clic con il pulsante destro del mouse sulla cartella *degli script* e scegliere Aggiungi > **nuovo elemento**. Scegliere il file di **configurazione JSON TypeScript**e quindi fare clic su **Aggiungi**.

   Visual Studio aggiunge il file *tsconfig.json* alla cartella *scripts.* È possibile utilizzare questo file per [configurare](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) le opzioni per il compilatore TypeScript.

1. Aprire *tsconfig.json* e sostituire il codice predefinito con il codice seguente:

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

   L'opzione *outDir* specifica la cartella di output per i file JavaScript del piano che vengono transletti dal compilatore TypeScript.

   Questa configurazione fornisce un'introduzione di base all'utilizzo di TypeScript.This configuration provides a basic introduction to using TypeScript. In altri scenari, ad esempio quando si utilizza [gulp o webpack](https://www.typescriptlang.org/docs/handbook/asp-net-core.html), è possibile che si desideri una posizione intermedia diversa per i file JavaScript transletti, a seconda degli strumenti e delle preferenze di configurazione, anziché *.. /wwwroot/js*.

1. Fare clic con il pulsante destro del mouse sulla cartella *degli script* e scegliere Aggiungi > **nuovo elemento**. Scegliere il **File TypeScript**, digitare il nome *app.ts* per il nome del file e quindi fare clic su **Aggiungi**.

   Visual Studio aggiunge *app.ts* alla cartella degli *script.*

1. Apri *app.ts* e aggiungi il seguente codice TypeScript.

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

    Visual Studio fornisce il supporto IntelliSense per il codice TypeScript.Visual Studio provides IntelliSense support for your TypeScript code.

    Per verificarlo, `.lastName` rimuovere `greeter` dalla funzione, quindi digitare nuovamente il "."e viene visualizzato IntelliSense.To test this, remove from the function, then retype the ".", and you see IntelliSense.

    ![Visualizza IntelliSense](../javascript/media/aspnet-core-ts-intellisense.png)

    Selezionare questa opzione `lastName` per aggiungere di nuovo il cognome al codice.

1. Aprire la cartella *Viste/Home,* quindi *index.html*.

1. Aggiungere il seguente codice HTML alla fine del file.

    ```html
    <div id="ts-example">
        <br />
        <button type="button" class="btn btn-primary btn-md" onclick="TSButton()">
            Click Me
        </button>
    </div>
    ```

1. Aprire la cartella *Viste/Condivisa,* quindi *aprire _Layout.cshtml*.

1. Aggiungere il seguente riferimento allo `@RenderSection("Scripts", required: false)`script prima della chiamata a :

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>Compilare l'applicazione

1. Scegliere **Compila > compila soluzione**.

   Anche se l'app viene compilata automaticamente quando viene eseguita, si vuole dare un'occhiata a qualcosa che accade durante il processo di compilazione.

1. Aprire la cartella *wwwroot / js* e trovare due nuovi file, *app.js* e il file di mappa di origine, *app.js.map*. Questi file vengono generati dal compilatore TypeScript.

   I file di mappa di origine sono necessari per il debug.

## <a name="run-the-application"></a>Eseguire l'applicazione

1. Premere **F5** (**Debug** > **Avvia debug**) per eseguire l'applicazione.

    L'app viene aperta in un browser.

    Nella finestra del browser, vedrai l'intestazione **Benvenuto** e il pulsante **Click Me.**

    ![ASP.NET Core con TypeScript](../javascript/media/aspnet-core-ts-running-app.png)

1. Fare clic sul pulsante per visualizzare il messaggio specificato nel file TypeScript.

## <a name="debug-the-application"></a>Eseguire il debug dell'applicazione

1. Impostare un `greeter` punto `app.ts` di interruzione nella funzione in facendo clic sul margine sinistro nell'editor di codice.

    ![Imposta punto di interruzione](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. Premere **F5** per eseguire l'applicazione.

   Potrebbe essere necessario rispondere a un messaggio per abilitare il debug degli script.

   L'applicazione viene sospesa in corrispondenza del punto di interruzione. A questo punto, è possibile esaminare le variabili e utilizzare le funzionalità del debugger.

## <a name="add-typescript-support-for-a-third-party-library"></a>Aggiungere il supporto TypeScript per una libreria di terze partiAdd TypeScript support for a third-party library

1. Seguire le istruzioni nella gestione `package.json` dei pacchetti [npm](../javascript/npm-package-management.md#aspnet-core-projects) per aggiungere un file al progetto. In questo modo viene aggiunto il supporto npm al progetto.

   >[!NOTE]
   > Per i progetti ASP.NET Core, è anche possibile utilizzare [Gestione librerie](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1) o filato anziché npm per installare file JavaScript e CSS lato client.

1. In questo esempio, aggiungere un file di definizione TypeScript per jQuery al progetto. Includere quanto segue nel file *package.json.*

   ```json
   "devDependencies": {
      "@types/jquery": "3.3.33"
   }
   ```

   In questo modo viene aggiunto il supporto TypeScript per jQuery. La libreria jQuery stessa è già inclusa nel modello di progetto MVC (cercare in wwwroot/lib in Esplora soluzioni). Se si utilizza un modello diverso, potrebbe essere necessario includere anche il pacchetto jquery npm.

1. Se il pacchetto in Esplora soluzioni non è installato, fare clic con il pulsante destro del mouse sul nodo npm e scegliere **Ripristina pacchetti**.

   >[!NOTE]
   > In alcuni scenari, Esplora soluzioni potrebbe indicare che un pacchetto npm non è sincronizzato con *package.json* a causa di un problema noto descritto [di seguito.](https://github.com/aspnet/Tooling/issues/479) Ad esempio, il pacchetto potrebbe apparire come non installato al momento dell'installazione. Nella maggior parte dei casi, è possibile aggiornare Esplora soluzioni eliminando *package.json*, riavviando Visual Studio e aggiungendo nuovamente il file *package.json* come descritto in precedenza in questo articolo.

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sulla cartella degli script e **scegliere Aggiungi** > **nuovo elemento**.

1. Scegliete **File TypeScript**, *libreria dei tipi.ts*e scegliete **Aggiungi**.

1. In *library.ts*aggiungere il codice seguente.

   ```ts
   var jqtest = {
      showMsg: function (): void {
         let v: any = jQuery.fn.jquery.toString();
         let content: any = $("#ts-example-2")[0].innerHTML;
         alert(content.toString());
         $("#ts-example-2")[0].innerHTML = content + " " + v + "!!";
      }
   };

   jqtest.showMsg();
   ```

   Per semplicità, questo codice visualizza un messaggio usando jQuery e un avviso.

   Con TypeScript definizioni di tipo per jQuery aggiunto, si ottiene il supporto IntelliSense su oggetti jQuery quando si digita un "." dopo un oggetto jQuery, come illustrato di seguito.

   ![IntelliSense jquery](../javascript/media/aspnet-core-ts-jquery-intellisense.png)

1. In _Layout.cshtml aggiornare i `library.js`riferimenti agli script in modo da includere .

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

    L'app si apre nel browser.

    Fare clic **su OK** nell'avviso per visualizzare la pagina aggiornata alla **versione jQuery è: 3.3.1!!**.

    ![Esempio jquery](../javascript/media/aspnet-core-ts-jquery-example.png)

## <a name="next-steps"></a>Passaggi successivi

È possibile ottenere ulteriori dettagli sull'utilizzo di TypeScript con ASP.NET Core.

> [!div class="nextstepaction"]
> [ASP.NET e TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)
