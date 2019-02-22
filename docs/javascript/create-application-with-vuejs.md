---
title: Creare un'app Vue.js tramite Node.js
description: È possibile creare applicazioni Node.js in Visual Studio usando il framework Vue.js
ms.custom: seodec18
ms.date: 07/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: a1c9de1c65c5f3f780e6ea4374fa7d96f436f514
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227761"
---
# <a name="create-a-vuejs-application-using-nodejs-tools-for-visual-studio"></a>Creare un'applicazione Vue.js tramite Node.js Tools for Visual Studio

Visual Studio 2017 include miglioramenti al supporto del framework [Vue.js](https://vuejs.org/), che offre una migliore esperienza di sviluppo durante la creazione di un'applicazione con Vue.js, JavaScript e TypeScript.

Lo sviluppo di applicazioni Vue.js in Visual Studio è supportato dalle nuove funzionalità seguenti:

* Supporto dei blocchi di script, stili e modelli nei file con estensione *vue*
* Riconoscimento dell'attributo `lang` nei file con estensione *vue*
* Modelli di progetto e di file di Vue.js

## <a name="prerequisites"></a>Prerequisiti

* È necessario che siano installati Visual Studio 2017 versione 15.8 Preview 3 e il carico di lavoro di sviluppo **Node.js**.

    > [!IMPORTANT]
    > Questo articolo richiede funzionalità disponibili solo a partire da Visual Studio 2017 versione 15.8 Preview 3.

    Se Visual Studio non è ancora installato, accedere alla pagina  [Download di Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)  per installarlo gratuitamente.

    Se il carico di lavoro è già installato ed è necessario installare Visual Studio, fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro della finestra di dialogo **Nuovo progetto** (selezionare **File** > **Nuovo** > **Progetto**). Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo Node.js**, quindi scegliere **Modifica**.

* Per creare il progetto ASP.NET Core, è necessario che siano installati i carichi di lavoro Sviluppo ASP.NET e Web e il carico di lavoro di sviluppo multipiattaforma di .NET Core.

* Il runtime di Node.js deve essere installato.

    Se il runtime non è installato, installare la versione LTS dal sito Web [Node.js](https://nodejs.org/en/download/). In generale, Visual Studio rileva automaticamente il runtime di Node.js installato. Se non viene rilevato un runtime installato è possibile configurare il progetto in modo che faccia riferimento al runtime installato nella pagina delle proprietà. Dopo aver creato un progetto, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Proprietà**.

## <a name="create-a-vuejs-project-using-a-template"></a>Creare un progetto Vue.js tramite un modello

Per creare un nuovo progetto, è possibile usare i nuovi modelli Vue.js. L'uso di un modello è il modo più semplice per iniziare. Per la procedura dettagliata, vedere [Use Visual Studio to create your first Vue.js app](../javascript/quickstart-vuejs-with-nodejs.md) (Creare la prima app Vue.js con Visual Studio).

## <a name="create-a-vuejs-project-with-aspnet-core-and-the-vue-cli"></a>Creare un progetto Vue.js con ASP.NET Core e la Common Language Infrastructure di Vue

Vue.js rende disponibile una Common Language Infrastructure ufficiale per lo scaffolding rapido dei progetti. Se si vuole usare la Common Language Infrastructure per creare l'applicazione, seguire la procedura descritta in questo articolo per configurare l'ambiente di sviluppo.

> [!IMPORTANT]
> Questa procedura presuppone già una certa familiarità con il framework Vue.js. In caso contrario, visitare il sito Web [Vue.js](https://vuejs.org/) per altre informazioni sul framework.

### <a name="create-a-new-aspnet-core-project"></a>Creare un nuovo progetto ASP.NET Core

In questo esempio si usa un'applicazione ASP.NET Core vuota (C#). È tuttavia possibile scegliere da un'ampia gamma di progetti e linguaggi di programmazione.

#### <a name="create-an-empty-project"></a>Creare un progetto vuoto

1. Aprire Visual Studio e scegliere **File** > **Nuovo** > **Progetto** dal menu principale.

1. In **Visual C#** > **Web** scegliere **Applicazione Web ASP.NET Core** e quindi fare clic su **OK**.

    Se il modello di progetto **Applicazione Web ASP.NET Core** non è visualizzato, è prima necessario installare il carico di lavoro **Sviluppo ASP.NET e Web** e il carico di lavoro di sviluppo di .**NET Core**. Per installare uno o entrambi i carichi di lavoro, fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro della finestra di dialogo **Nuovo progetto** (selezionare **File** > **Nuovo** > **Progetto**). Verrà avviato il Programma di installazione di Visual Studio. Selezionare i carichi di lavoro necessari.

1. Selezionare **Vuoto** e quindi fare clic su **OK**.

    Visual Studio crea il progetto, che viene aperto in Esplora soluzioni (riquadro destro).

#### <a name="configure-the-project-startup-file"></a>Configurare il file di avvio del progetto

* Aprire il file *./Startup.cs*e aggiungere le righe seguenti al metodo Configure:

    ```csharp
    app.UseDefaultFiles(); // Enables default file mapping on the web root.
    app.UseStaticFiles(); // Marks files on the web root as servable.
    ```

### <a name="install-the-vue-cli"></a>Installare la Common Language Infrastructure di vue

Per installare il modulo vue-cli npm, aprire un prompt dei comandi e digitare `npm install --g vue-cli` o `npm install -g @vue/cli` per la versione 3.0 (attualmente in versione beta).

### <a name="scaffold-a-new-client-application-using-the-vue-cli"></a>Eseguire lo scaffolding di una nuova applicazione client tramite la Common Language Infrastructure di vue

1. Passare al prompt dei comandi e passare dalla directory corrente alla cartella radice del progetto.

1. Digitare `vue init webpack ClientApp` e seguire questa procedura quando viene richiesto di rispondere a domande aggiuntive.

#### <a name="modify-the-webpack-configuration-to-output-the-built-files-to-wwwroot"></a>Modificare la configurazione di webpack per inviare i file compilati a wwwroot

* Aprire il file *./ClientApp/config/index.js* e modificare `build.index` e `build.assetsRoot` nel percorso wwwroot:

    ```js
    // Template for index.html
    index: path.resolve(__dirname, '../../wwwroot/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../../wwwroot'),
    ```

#### <a name="indicate-the-project-to-build-the-clientapp-each-time-that-a-build-is-triggered"></a>Indicare il progetto per la compilazione di ClientApp ogni volta che viene attivata una compilazione

1. In Visual Studio passare a **Progetto** > **Proprietà** > **Eventi di compilazione**.

1. In **Riga di comando eventi pre-compilazione** digitare `npm --prefix ./ClientApp run build`.

#### <a name="configure-webpacks-output-module-names"></a>Configurare i nomi dei moduli di output di webpack

* Aprire il file *./ClientApp/build/webpack.base.conf.js* e aggiungere le proprietà seguenti alla proprietà di output:

    ```js
    devtoolModuleFilenameTemplate: '[absolute-resource-path]',
    devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
    ```

### <a name="add-typescript-support-with-the-vue-cli"></a>Aggiungere il supporto di TypeScript con la Common Language Infrastructure di Vue

Questa procedura richiede vue-cli 3.0, che attualmente è in versione beta.

1. Passare al prompt dei comandi e passare dalla directory corrente alla cartella radice del progetto.

1. Digitare `vue create ClientApp` e quindi scegliere **Manually select features** (Seleziona manualmente le funzionalità).

1. Scegliere **TypeScript**e quindi selezionare le altre opzioni desiderate.

1. Eseguire i passaggi rimanenti e rispondere alle domande.

#### <a name="configure-a-vuejs-project-for-typescript"></a>Configurare un progetto Vue.js per TypeScript

1. Aprire il file *./ClientApp/tsconfig.json* e aggiungere `noEmit:true` alle opzioni del compilatore.

    Impostando questa opzione si evita di sovraccaricare il progetto ogni volta che si esegue la compilazione in Visual Studio.

1. Creare quindi un file *vue.config.js* in *./ClientApp/* e aggiungere il codice seguente.

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

Un problema sconosciuto di vue-cli 3.0 impedisce l'automatizzazione del processo di compilazione. Ogni volta che si tenta di aggiornare la cartella wwwroot, è necessario eseguire il comando `npm run build` nella cartella ClientApp.

## <a name="limitations"></a>Limitazioni

* L'attributo `lang` supporta solo i linguaggi JavaScript e TypeScript. I valori consentiti sono js, jsx, ts e tsx.
* L'attributo `lang` non funziona con i tag di stile o di modello.
* Il debug di blocchi di script nei file con estensione *vue* non è supportato a causa della sua natura pre-elaborata.
* TypeScript non riconosce i file con estensione *vue* come moduli. È necessario un file che contenga codice come il seguente che informi TypeScript dell'aspetto dei file con estensione *vue*. Il modello vue-cli 3.0 include già questo file.

    ```js
    // ./ClientApp/vue-shims.d.ts
    declare module "*.vue" {
        import Vue from "vue";
        export default Vue;
    }
    ```

* L'esecuzione del comando `npm run build` come evento di pre-compilazione per le proprietà del progetto non funziona se si usa vue-cli 3.0.

## <a name="see-also"></a>Vedere anche

- [Guida introduttiva di Vue](https://vuejs.org/v2/guide).
- [Progetto Vue CLI](https://github.com/vuejs/vue-cli).
- [Documentazione sulla configurazione di webpack](https://webpack.js.org/configuration/).
