---
title: Gestire pacchetti npm
description: Visual Studio consente di gestire i pacchetti usando il sistema di gestione pacchetti Node.js (npm)
ms.custom: seodec18
ms.date: 04/16/2020
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: ef831b5ffee172b642572535162713a53d8ae578
ms.sourcegitcommit: eef26de3d7a5c971baedbecf3b4941fb683ddb2d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2020
ms.locfileid: "81544328"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Gestire i pacchetti npm in Visual Studio

npm consente di installare e gestire i pacchetti per l'uso nelle applicazioni Node.js. Visual Studio semplifica l'interazione con npm e genera comandi npm direttamente o attraverso l'interfaccia utente. Se non si ha familiarità con npm e sono necessarie altre informazioni, consultare la [documentazione di npm](https://docs.npmjs.com/).

L'integrazione di Visual Studio con npm è diversa a seconda del tipo di progetto.
* [Node.js](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [Cartella aperta (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)

*package.json* è un file utilizzato da npm per gestire le dipendenze dei pacchetti e le versioni dei pacchetti per i pacchetti installati localmente. Per ulteriori informazioni su questo file, vedere [configurazione package.json](../javascript/configure-packages-with-package-json.md).

> [!Important]
> npm prevede la cartella *node_modules* e *package.json* nella radice del progetto. If your app's folder structure is different, you should modify your folder structure if you want to manage npm packages using Visual Studio.

## <a name="nodejs-projects"></a>Progetti Node.js

Per i progetti Node.js, è possibile eseguire le attività seguenti:For Node.js projects, you can perform the following tasks:
* [Installare i pacchetti da Esplora soluzioni](#npmInstallWindow)
* [Gestire i pacchetti installati da Esplora soluzioni](#solutionExplorer)
* [Usare il comando `.npm` nella finestra interattiva di Node.js](#interactive)

Queste funzionalità interagiscono e si sincronizzano con il sistema di progetto e il file *package.json* nel progetto.

### <a name="prerequisites"></a>Prerequisiti

Per aggiungere il supporto npm al progetto sono necessari il carico di lavoro di **sviluppo Node.js** e il runtime Node.js. Per la procedura dettagliata, vedere [Creare un progetto Node.js](/visualstudio/ide/quickstart-nodejs?toc=/visualstudio/javascript/toc.json).

> [!NOTE]
> Per i progetti Node.js esistenti, usare il modello di soluzione **Di codice Node.js esistente** o il tipo di progetto Apri cartella [(Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md) per abilitare npm nel progetto.

### <a name="install-packages-from-solution-explorer-nodejs"></a><a name="npmInstallWindow"></a>Installare pacchetti da Esplora soluzioni (Node.js)Install packages from Solution Explorer (Node.js)

Per i progetti Node.js, il modo più semplice per installare i pacchetti npm è tramite la finestra di installazione del pacchetto npm. Per accedere a questa finestra, fare clic con il pulsante destro del mouse sul nodo **npm** nel progetto e selezionare **Installa nuovi pacchetti npm**.

:::image type="content" source="../javascript/media/solution-explorer-install-package.png" alt-text="Installare nuovi pacchetti npm da esplora soluzioni" border="true":::

In questa finestra è possibile eseguire la ricerca di un pacchetto, specificare le opzioni ed eseguire l'installazione.

![Ricerca del pacchetto npm](../javascript/media/search-package.png)

* **Tipo di dipendenza**: scegliere tra i pacchetti **Standard**, **Sviluppo** e **Facoltativo**. Standard specifica che il pacchetto è una dipendenza di runtime, mentre Sviluppo specifica che il pacchetto è necessario solo durante lo sviluppo.
* **Aggiungi a package.json**: questa opzione è deprecata
* **Versione selezionata**: selezionare la versione del pacchetto da installare.
* **Altri argomenti di npm**: specificare altri argomenti di npm standard. Ad esempio, è possibile immettere un valore di versione come `@~0.8` per installare una versione specifica che non è disponibile nell'elenco delle versioni.

È possibile visualizzare lo stato di avanzamento dell'installazione nell'output **npm** nella finestra **Output.** Questa operazione potrebbe richiedere tempo.

![Uscita npm](../javascript/media/npm-output.png)

> [!TIP]
> È possibile cercare i pacchetti con ambito anteponendo la query di ricerca con l'ambito che interessa, ad esempio, digitare `@types/mocha` per cercare i file di definizione TypeScript per mocha. Inoltre, quando si installano definizioni di tipo per TypeScript, è `@ts2.6` possibile specificare la versione di TypeScript di destinazione aggiungendo nel campo dell'argomento npm.

### <a name="manage-installed-packages-in-solution-explorer-nodejs"></a><a name="solutionExplorer"></a>Gestire i pacchetti installati in Esplora soluzioni (Node.js)Manage installed packages in Solution Explorer (Node.js)

I pacchetti npm sono visualizzati in Esplora soluzioni. Le voci sotto il nodo **npm** simulano le dipendenze nel file *package.json*.

![Ricerca del pacchetto npm](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>Stato del pacchetto

* ![Pacchetto installato](../javascript/media/installed-npm.png) - Installato e indicato nel file package.json
* ![Pacchetto estraneo](../javascript/media/extraneous-npm.png): installato, ma non esplicitamente indicato nel file package.json
* ![Pacchetto mancante](../javascript/media/missing-npm.png) - Non installato ma indicato nel file package.json

Fare clic con il pulsante destro del mouse su un nodo del pacchetto o sul nodo **npm** per effettuare una delle azioni seguenti:
* **Installare i pacchetti mancanti** indicati in *package.json*
* **Aggiornare i pacchetti** alla versione più recente
* **Disinstallare un pacchetto** e rimuoverlo da *package.json*

### <a name="use-the-npm-command-in-the-nodejs-interactive-window-nodejs"></a><a name="interactive"></a>Utilizzare il comando .npm nella finestra interattiva Node.js (Node.js)

È anche possibile usare il comando `.npm` nella finestra interattiva di Node.js per eseguire i comandi npm. Per aprire la finestra, fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni e scegliere **Apri finestra interattiva di Node.js**.

Nella finestra è possibile usare comandi simili al seguente per installare un pacchetto:

`.npm install azure@4.2.3`

 > [!Tip]
 > Per impostazione predefinita, npm viene eseguito nella home directory del progetto. Se sono presenti più progetti nella soluzione, specificare il nome o il percorso del progetto tra parentesi quadre.
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > Se il progetto non contiene un file package.json, usare `.npm init -y` per creare un nuovo file package.json con le voci predefinite.

 ## <a name="aspnet-core-projects"></a>progetti ASP.NET Core

Per progetti come ASP.NET progetti Core, è possibile integrare il supporto npm nel progetto e utilizzare npm per installare i pacchetti.
* [Aggiungere il supporto npm a un progettoAdd npm support to a project](#npmAdd)
* [Installare i pacchetti usando package.jsonInstall packages using package.json](#npmInstallPackage)

>[!NOTE]
> Per i progetti ASP.NET Core, è anche possibile utilizzare [Gestione librerie](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1) o filato anziché npm per installare file JavaScript e CSS lato client.

### <a name="add-npm-support-to-a-project-aspnet-core"></a><a name="npmAdd"></a>Aggiungere il supporto npm a un progetto (ASP.NET Core)Add npm support to a project (ASP.NET Core)

Se il progetto non include già un file *package.json,* è possibile aggiungerne uno per abilitare il supporto npm aggiungendo un file *package.json* al progetto.

1. Se Node.js non è installato, è consigliabile installare la versione LTS dal sito [Web Node.js](https://nodejs.org/en/download/) per garantire la migliore compatibilità con framework e librerie esterni.

   npm richiede Node.js.

1. Per aggiungere il file *package.json,* fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni e scegliere **Aggiungi** > **nuovo elemento**. Scegliere il file di **configurazione npm**, utilizzare il nome predefinito e fare clic su **Aggiungi**.

   ![Aggiungere package.json al progettoAdd package.json to your project](../javascript/media/npm-add-package-json.png)

   Se il file di configurazione npm non è elencato, gli strumenti di sviluppo Node.js non sono installati. È possibile utilizzare il programma di installazione di Visual Studio per aggiungere il carico di lavoro di **sviluppo Node.js.You** can use the Visual Studio Installer to add the Node.js development workload. Ripetere quindi il passaggio precedente.

1. Includere uno o più pacchetti `dependencies` `devDependencies` npm nella sezione o di *package.json*. Ad esempio, è possibile aggiungere quanto segue al file:

   ```json
   "devDependencies": {
      "gulp": "4.0.2",
      "@types/jquery": "3.3.33"
   }
   ```

Quando si salva il file, Visual Studio aggiunge il pacchetto nel nodo **Dipendenze / npm** in Esplora soluzioni. Se il nodo non è visualizzato, fare clic con il pulsante destro del mouse su **package.json** e scegliere **Ripristina pacchetti**.

>[!NOTE]
> In alcuni scenari, In Esplora soluzioni potrebbe non mostrare lo stato corretto per i pacchetti npm installati a causa di un problema noto descritto [di seguito](https://github.com/aspnet/Tooling/issues/479). Ad esempio, il pacchetto potrebbe apparire come non installato al momento dell'installazione. Nella maggior parte dei casi, è possibile aggiornare Esplora soluzioni eliminando *package.json*, riavviando Visual Studio e aggiungendo nuovamente il file *package.json* come descritto in precedenza in questo articolo.

### <a name="install-packages-using-packagejson-aspnet-core"></a><a name="npmInstallPackage"></a>Installare pacchetti utilizzando package.json (ASP.NET Core)Install packages using package.json (ASP.NET Core)

Per i progetti con npm incluso, `package.json`è possibile configurare i pacchetti npm utilizzando . Fare clic con il pulsante destro del mouse sul nodo npm in Esplora soluzioni e scegliere **Apri package.json**.

![Ricerca del pacchetto npm](../javascript/media/npm-add-package.png)

IntelliSense in *package.json* consente di selezionare una particolare versione di un pacchetto npm.

:::image type="content" source="../javascript/media/npm-add-package-intellisense.png" alt-text="Selezionare la versione del pacchetto npm" border="true":::

Quando si salva il file, Visual Studio aggiunge il pacchetto nel nodo **Dipendenze / npm** in Esplora soluzioni. Se il nodo non è visualizzato, fare clic con il pulsante destro del mouse su **package.json** e scegliere **Ripristina pacchetti**.

L'installazione di un pacchetto potrebbe richiedere alcuni minuti. Controllare lo stato di avanzamento dell'installazione del pacchetto passando all'output **di npm** nella finestra **Output.**

![Uscita npm](../javascript/media/npm-output.png)

