---
title: Creare un'app Vue.js tramite Node.js
description: È possibile creare applicazioni Node.js in Visual Studio usando il framework Vue.js
ms.custom: seodec18
ms.date: 07/06/2018
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-javascript
dev_langs:
- JavaScript
ms.workload:
- nodejs
monikerRange: <= vs-2019
ms.openlocfilehash: e9f67334dfc6f0fb586638a8f9a93148fed4bb33b134066c92a6606f9e506e3c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121371152"
---
# <a name="create-a-vuejs-application-using-nodejs-tools-for-visual-studio"></a>Creare un'applicazione Vue.js tramite Node.js Tools for Visual Studio

Visual Studio supporta lo sviluppo di app con il framework [Vue.js](https://vuejs.org/) in JavaScript o TypeScript.

Lo sviluppo di applicazioni Vue.js in Visual Studio è supportato dalle nuove funzionalità seguenti:

* Supporto dei blocchi di script, stili e modelli nei file con estensione *vue*
* Riconoscimento dell'attributo `lang` nei file con estensione *vue*
* Modelli di progetto e di file di Vue.js

## <a name="prerequisites"></a>Prerequisiti

* È necessario che siano installati Visual Studio 2017 versione 15.8 o una versione successiva e il carico di lavoro di **sviluppo Node.js**.

    > [!IMPORTANT]
    > Questo articolo richiede funzionalità disponibili solo a partire da Visual Studio 2017 versione 15.8.

    ::: moniker range=">=vs-2019"
    Se non è già installata una versione richiesta, installare [Visual Studio 2019](https://visualstudio.microsoft.com/downloads).
    ::: moniker-end
    ::: moniker range="vs-2017"
    Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.
    ::: moniker-end

    Se è necessario installare il carico di lavoro ma è già Visual Studio, passare a Strumenti Ottieni strumenti e  >  **funzionalità...**, che apre il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo Node.js**, quindi scegliere **Modifica**.

* Per creare il progetto ASP.NET Core, è necessario che siano installati i carichi di lavoro Sviluppo ASP.NET e Web e il carico di lavoro di sviluppo multipiattaforma di .NET Core.

* Il runtime di Node.js deve essere installato.

    Se il runtime non è installato, installare la versione LTS dal sito Web [Node.js](https://nodejs.org/en/download/). In generale, Visual Studio rileva automaticamente il runtime di Node.js installato. Se non viene rilevato un runtime installato è possibile configurare il progetto in modo che faccia riferimento al runtime installato nella pagina delle proprietà. Dopo aver creato un progetto, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Proprietà**.

## <a name="create-a-vuejs-project-using-nodejs"></a>Creare un progetto Vue.js usando Node.js

Per creare un nuovo progetto, è possibile usare i nuovi modelli Vue.js. L'uso di un modello è il modo più semplice per iniziare. Per la procedura dettagliata, vedere [Use Visual Studio to create your first Vue.js app](../javascript/quickstart-vuejs-with-nodejs.md) (Creare la prima app Vue.js con Visual Studio).

## <a name="create-a-vuejs-project-with-aspnet-core-and-the-vue-cli"></a>Creare un progetto Vue.js con ASP.NET Core e la Common Language Infrastructure di Vue

Vue.js rende disponibile una Common Language Infrastructure ufficiale per lo scaffolding rapido dei progetti. Se si vuole usare la Common Language Infrastructure per creare l'applicazione, seguire la procedura descritta in questo articolo per configurare l'ambiente di sviluppo.

> [!IMPORTANT]
> Questa procedura presuppone già una certa familiarità con il framework Vue.js. In caso contrario, visitare il sito Web [Vue.js](https://vuejs.org/) per altre informazioni sul framework.

### <a name="create-a-new-aspnet-core-project"></a>Creare un nuovo progetto ASP.NET Core

In questo esempio si usa un'applicazione ASP.NET Core vuota (C#). È tuttavia possibile scegliere da un'ampia gamma di progetti e linguaggi di programmazione.

#### <a name="create-an-empty-project"></a>Creare un progetto vuoto

* Aprire Visual Studio e creare un nuovo progetto.

    ::: moniker range=">=vs-2019"
    In Visual Studio 2019 scegliere **Crea un nuovo progetto** nella finestra iniziale. Se la finestra iniziale non è aperta, scegliere **Finestra**  >  **iniziale file**. Digitare **app Web,** scegliere **C#** come linguaggio, quindi ASP.NET Core **vuoto** e infine **scegliere Avanti.** Nella schermata successiva assegnare al progetto il nome **client-app** e quindi scegliere **Avanti.**

    Scegliere il framework di destinazione consigliato (.NET Core 3.1) o .NET 5 e quindi scegliere **Crea.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Nella barra dei menu superiore scegliere **File**  >  **Nuovo**  >  **Project**. Nel riquadro a sinistra della finestra di dialogo **Nuovo progetto** espandere **Visual C#** e quindi scegliere **Web**. Nel riquadro centrale scegliere **Applicazione Web ASP.NET Core**, digitare il nome **client-app** e quindi scegliere **OK**.

    Selezionare **Vuoto** e quindi fare clic su **OK**.

    Visual Studio crea il progetto, che viene aperto in Esplora soluzioni (riquadro destro).
    ::: moniker-end

    Se il modello di progetto **Applicazione Web ASP.NET Core** non è visualizzato, è prima necessario installare il carico di lavoro **Sviluppo ASP.NET e Web** e il carico di lavoro di sviluppo di .**NET Core**. Per installare uno o entrambi i carichi di lavoro, fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro della finestra di dialogo **Nuovo progetto** (selezionare **File** > **Nuovo** > **Progetto**). Verrà avviato il Programma di installazione di Visual Studio. Selezionare i carichi di lavoro necessari.

#### <a name="configure-the-project-startup-file"></a>Configurare il file di avvio del progetto

* Aprire il file *./Startup.cs* e aggiungere le righe seguenti al metodo Configure:

    ```csharp
    app.UseDefaultFiles(); // Enables default file mapping on the web root.
    app.UseStaticFiles(); // Marks files on the web root as servable.
    ```

### <a name="install-the-vue-cli"></a>Installare la Common Language Infrastructure di vue

Per installare il modulo vue-cli npm, aprire un prompt dei comandi e digitare `npm install --g vue-cli` o `npm install -g @vue/cli` per la versione 3.0 (attualmente in versione beta).

### <a name="scaffold-a-new-client-application-using-the-vue-cli"></a>Eseguire lo scaffolding di una nuova applicazione client tramite la Common Language Infrastructure di vue

1. Passare al prompt dei comandi e passare dalla directory corrente alla cartella radice del progetto.

1. Digitare `vue init webpack client-app` e seguire questa procedura quando viene richiesto di rispondere a domande aggiuntive.

    > [!NOTE]
    > Per i file con estensione *vue*, è necessario usare WebPack o un framework simile con un caricatore per eseguire la conversione. TypeScript e Visual Studio non supportano la compilazione di file *vue*. Lo stesso vale per la creazione di bundle. TypeScript non supporta la conversione di moduli ES2015 (ovvero, le istruzioni `import` e `export`) in un singolo file *js* finale da caricare nel browser. Anche in questo caso WebPack è la scelta migliore. Per gestire questo processo da Visual Studio con MSBuild, è necessario iniziare da un modello di Visual Studio. Al momento, non è disponibile alcun modello ASP.NET predefinito per lo sviluppo di Vue.js.

#### <a name="modify-the-webpack-configuration-to-output-the-built-files-to-wwwroot"></a>Modificare la configurazione di webpack per inviare i file compilati a wwwroot

* Aprire il file *./client-app/config/index.js* e modificare `build.index` e `build.assetsRoot` nel percorso wwwroot:

    ```js
    // Template for index.html
    index: path.resolve(__dirname, '../../wwwroot/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../../wwwroot'),
    ```

#### <a name="indicate-the-project-to-build-the-client-app-each-time-that-a-build-is-triggered"></a>Indicare il progetto per la compilazione dell'app client ogni volta che viene attivata una compilazione

1. In Visual Studio passare a **Proprietà** Project  >    >  **eventi di compilazione.**

1. In **Riga di comando eventi pre-compilazione** digitare `npm --prefix ./client-app run build`.

#### <a name="configure-webpacks-output-module-names"></a>Configurare i nomi dei moduli di output di webpack

* Aprire il file *./client-app/build/webpack.base.conf.js* e aggiungere le proprietà seguenti alla proprietà di output:

    ```js
    devtoolModuleFilenameTemplate: '[absolute-resource-path]',
    devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
    ```

### <a name="add-typescript-support-with-the-vue-cli"></a>Aggiungere il supporto di TypeScript con la Common Language Infrastructure di Vue

Questa procedura richiede vue-cli 3.0, che attualmente è in versione beta.

1. Passare al prompt dei comandi e passare dalla directory corrente alla cartella radice del progetto.

1. Digitare `vue create client-app` e quindi scegliere **Manually select features** (Seleziona manualmente le funzionalità).

1. Scegliere **TypeScript** e quindi selezionare le altre opzioni desiderate.

1. Eseguire i passaggi rimanenti e rispondere alle domande.

#### <a name="configure-a-vuejs-project-for-typescript"></a>Configurare un progetto Vue.js per TypeScript

1. Aprire il file *./client-app/tsconfig.json* e aggiungere `noEmit:true` alle opzioni del compilatore.

    Impostando questa opzione si evita di sovraccaricare il progetto ogni volta che si esegue la compilazione in Visual Studio.

1. Creare quindi un file *vue.config.js* in *./client-app/* e aggiungere il codice seguente.

    ```js
    module.exports = {
        outputDir: '../wwwroot',

        configureWebpack: {
            output: {
                devtoolModuleFilenameTemplate: '[absolute-resource-path]',
                devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
            }
        }
    };
    ```

    Il codice precedente configura webpack e imposta la cartella wwwroot.

#### <a name="build-with-vue-cli-30"></a>Compilare con vue-cli 3.0

Un problema sconosciuto di vue-cli 3.0 può impedire l'automatizzazione del processo di compilazione. Ogni volta che si tenta di aggiornare la cartella wwwroot, è necessario eseguire il comando `npm run build` nella cartella client-app.

In alternativa, è possibile compilare il progetto vue-cli 3.0 come un evento di pre-compilazione usando le proprietà del progetto ASP.NET. Fare clic con il pulsante destro del mouse sul progetto, scegliere **Proprietà** e includere i comandi seguenti nella casella di testo **Riga di comando eventi pre-compilazione** della scheda **Compilazione**.

``` cmd
cd ./client-app
npm run build
cd ../
```

## <a name="limitations"></a>Limitazioni

* L'attributo `lang` supporta solo i linguaggi JavaScript e TypeScript. I valori consentiti sono js, jsx, ts e tsx.
* L'attributo `lang` non funziona con i tag di stile o di modello.
* Il debug di blocchi di script nei file con estensione *vue* non è supportato a causa della sua natura pre-elaborata.
* TypeScript non riconosce i file con estensione *vue* come moduli. È necessario un file che contenga codice come il seguente che informi TypeScript dell'aspetto dei file con estensione *vue*. Il modello vue-cli 3.0 include già questo file.

    ```js
    // ./client-app/vue-shims.d.ts
    declare module "*.vue" {
        import Vue from "vue";
        export default Vue;
    }
    ```

* L'esecuzione del comando `npm run build` come evento di pre-compilazione per le proprietà del progetto non funziona se si usa vue-cli 3.0.

## <a name="see-also"></a>Vedi anche

- [Guida introduttiva di Vue](https://vuejs.org/v2/guide).
- [Progetto dell'interfaccia della riga di comando di Vue](https://github.com/vuejs/vue-cli).
- [Documentazione sulla configurazione di webpack](https://webpack.js.org/configuration/).
