---
title: Gestire pacchetti npm
description: Visual Studio consente di gestire i pacchetti usando il sistema di gestione pacchetti Node.js (npm)
ms.custom: seodec18
ms.date: 10/1/2021
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
ms.openlocfilehash: 46b5284f91fdce4b073f8ac7b8e78569b353452c
ms.sourcegitcommit: d63ba1eff845d41ca095efb14b499ea96c4b6eba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/06/2021
ms.locfileid: "129560907"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Gestire i pacchetti npm in Visual Studio

npm consente di installare e gestire i pacchetti per l'uso in Node.js e ASP.NET Core applicazioni. Visual Studio semplifica l'interazione con npm e genera comandi npm direttamente o attraverso l'interfaccia utente. Se non si ha familiarità con npm e sono necessarie altre informazioni, consultare la [documentazione di npm](https://docs.npmjs.com/).

Visual Studio'integrazione con npm è diversa a seconda del tipo di progetto.
::: moniker range=">=vs-2022"
* [Progetti basati sull'interfaccia della riga di comando (con estensione esproj)](#cli-based-project-esproj)
* [Node.js](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [Apri cartella (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)
::: moniker-end

::: moniker range="<=vs-2019"
* [Node.js](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [Apri cartella (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)
::: moniker-end

> [!Important]
> npm prevede la cartella *node_modules* *e package.json* nella radice del progetto. Se la struttura di cartelle dell'app è diversa, è consigliabile modificare la struttura di cartelle se si vogliono gestire i pacchetti npm usando Visual Studio.

::: moniker range=">=vs-2022"
## <a name="cli-based-project-esproj"></a>Progetto basato sull'interfaccia della riga di comando (con estensione esproj)

A partire da Visual Studio 2022 Preview 4, gestione pacchetti npm è disponibile per i progetti basati sull'interfaccia della riga di comando, quindi è ora possibile scaricare i moduli npm in modo analogo al modo in cui si scaricano i pacchetti NuGet per i progetti ASP.NET Core. È quindi possibile usare *package.json* per modificare ed eliminare i pacchetti.

Per aprire Gestione pacchetti, da Esplora soluzioni fare clic con il pulsante destro del mouse sul **nodo npm** nel progetto.

:::image type="content" source="../javascript/media/vs-2022/npm-packages-open-manager-esproj.png" alt-text="Aprire Gestione pacchetti da Esplora soluzioni" border="true":::

Successivamente, è possibile cercare i pacchetti npm, selezionarne uno e installarlo selezionando **Installa pacchetto**. 

:::image type="content" source="../javascript/media/vs-2022/npm-packages-install-esproj.png" alt-text="Installare il nuovo pacchetto npm per esproj" border="true":::
::: moniker-end

## <a name="nodejs-projects"></a>Node.js progetti

Per Node.js progetti, è possibile eseguire le attività seguenti:
* [Installare i pacchetti da Esplora soluzioni](#npmInstallWindow)
* [Gestire i pacchetti installati da Esplora soluzioni](#solutionExplorer)
* [Usare il comando `.npm` nella finestra interattiva di Node.js](#interactive)

Queste funzionalità interagiscono e si sincronizzano con il sistema di progetto e il file *package.json* nel progetto.

### <a name="prerequisites"></a>Prerequisiti

Per aggiungere **il supporto npm al progetto,** sono necessari il carico di lavoro di sviluppoNode.js e il runtime di Node.js. Per la procedura dettagliata, vedere [Creare un Node.js progetto](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json).

> [!NOTE]
> Per i Node.js esistenti, usare il tipo di progetto Da soluzione codice **Node.js** esistente o Apri cartella [(Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md) per abilitare npm nel progetto.

### <a name="install-packages-from-solution-explorer-nodejs"></a><a name="npmInstallWindow"></a> Installare pacchetti da Esplora soluzioni (Node.js)

Per Node.js, il modo più semplice per installare i pacchetti npm è tramite la finestra di installazione del pacchetto npm. Per accedere a questa finestra, fare clic con il pulsante destro del mouse sul nodo **npm** nel progetto e selezionare **Installa nuovi pacchetti npm**.

:::image type="content" source="../javascript/media/solution-explorer-install-package.png" alt-text="Installare il nuovo pacchetto npm per Node.js" border="true":::

In questa finestra è possibile eseguire la ricerca di un pacchetto, specificare le opzioni ed eseguire l'installazione.

![Screenshot della finestra di dialogo Installa nuovi pacchetti npm. Il pacchetto azure 2.2.1-preview è selezionato e vengono visualizzati i dettagli e le opzioni per il pacchetto.](../javascript/media/search-package.png)

* **Tipo di dipendenza**: scegliere tra i pacchetti **Standard**, **Sviluppo** e **Facoltativo**. Standard specifica che il pacchetto è una dipendenza di runtime, mentre Sviluppo specifica che il pacchetto è necessario solo durante lo sviluppo.
* **Aggiungi a package.json** - Consigliato. Questa opzione configurabile è deprecata.
* **Versione selezionata**: selezionare la versione del pacchetto da installare.
* **Altri argomenti di npm**: specificare altri argomenti di npm standard. Ad esempio, è possibile immettere un valore di versione come `@~0.8` per installare una versione specifica che non è disponibile nell'elenco delle versioni.

È possibile visualizzare lo stato di avanzamento dell'installazione nell'output **npm** nella finestra **Output** (per aprire la finestra scegliere Visualizza output o premere  >   **CTRL**  +    +  **ALT+O).** Questa operazione potrebbe richiedere tempo.

![Output npm](../javascript/media/npm-output.png)

> [!TIP]
> È possibile cercare i pacchetti con ambito anteponendo la query di ricerca con l'ambito che interessa, ad esempio, digitare `@types/mocha` per cercare i file di definizione TypeScript per mocha. Inoltre, quando si installano le definizioni dei tipi per TypeScript, è possibile specificare la versione di TypeScript di destinazione aggiungendo nel `@ts2.6` campo dell'argomento npm.

### <a name="manage-installed-packages-in-solution-explorer-nodejs"></a><a name="solutionExplorer"></a>Gestire i pacchetti installati in Esplora soluzioni (Node.js)

I pacchetti npm sono visualizzati in Esplora soluzioni. Le voci sotto il nodo **npm** simulano le dipendenze nel file *package.json*.

![Screenshot del nodo npm in Esplora soluzioni lo stato di installazione dei pacchetti npm.](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>Stato del pacchetto

* ![Pacchetto installato](../javascript/media/installed-npm.png) - Installato e indicato nel file package.json
* ![Pacchetto estraneo](../javascript/media/extraneous-npm.png): installato, ma non esplicitamente indicato nel file package.json
* ![Pacchetto mancante](../javascript/media/missing-npm.png) - Non installato ma indicato nel file package.json

::: moniker range=">=vs-2019"
Fare clic con il pulsante destro del mouse sul nodo **npm** per eseguire una delle azioni seguenti:

* **Installare nuovi pacchetti npm** Apre l'interfaccia utente per installare nuovi pacchetti.
* **Installare pacchetti npm** Esegue il comando npm install per installare tutti i pacchetti elencati in *package.json.* (Esegue `npm install` . )
* **Aggiornare i pacchetti npm** Aggiorna i pacchetti alle versioni più recenti, in base all'intervallo di controllo delle versioni semantico (SemVer) specificato in *package.json.* (Esegue `npm update --save` . ). Gli intervalli di SemVer vengono in genere specificati usando "~" o "^". Per altre informazioni, [vedere configurazione di package.json.](../javascript/configure-packages-with-package-json.md)

Fare clic con il pulsante destro del mouse su un nodo del pacchetto per eseguire una delle azioni seguenti:

* **Installare i pacchetti npm** Esegue il comando npm install per installare la versione del pacchetto elencata in *package.json*. (Esegue `npm install` . )
* **Aggiornare i pacchetti npm** Aggiorna il pacchetto alla versione più recente, in base all'intervallo SemVer specificato in *package.json.* (Eseguire `npm update --save` . ) Gli intervalli di SemVer vengono in genere specificati usando "~" o "^".
* **Disinstallare i pacchetti npm** Disinstalla il pacchetto e lo rimuove da *package.json* (esegue `npm uninstall --save` . )
::: moniker-end
::: moniker range="vs-2017"
Fare clic con il pulsante destro del mouse su un nodo del pacchetto o sul nodo **npm** per effettuare una delle azioni seguenti:
* **Installare i pacchetti mancanti** indicati in *package.json*
* **Aggiornare i pacchetti npm** alla versione più recente
* **Disinstallare un pacchetto** e rimuoverlo da *package.json*
::: moniker-end

>[!NOTE]
> Per informazioni sulla risoluzione dei problemi relativi ai pacchetti npm, vedere [Risoluzione dei problemi](#troubleshooting-npm-packages).

### <a name="use-the-npm-command-in-the-nodejs-interactive-window-nodejs"></a><a name="interactive"></a>Usare il comando .npm nella finestra interattiva Node.js (Node.js)

È anche possibile usare il comando `.npm` nella finestra interattiva di Node.js per eseguire i comandi npm. Per aprire la finestra, fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni e scegliere Apri Node.js **finestra** interattiva (o premere **CTRL**  +  **K**, **N**).

Nella finestra è possibile usare comandi simili al seguente per installare un pacchetto:

`.npm install azure@4.2.3`

 > [!Tip]
 > Per impostazione predefinita, npm viene eseguito nella home directory del progetto. Se sono presenti più progetti nella soluzione, specificare il nome o il percorso del progetto tra parentesi quadre.
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > Se il progetto non contiene un file package.json, usare `.npm init -y` per creare un nuovo file package.json con le voci predefinite.

 ## <a name="aspnet-core-projects"></a>ASP.NET Core progetti

Per progetti come ASP.NET Core, è possibile integrare il supporto npm nel progetto e usare npm per installare i pacchetti.
* [Aggiungere il supporto npm a un progetto](#npmAdd)
* [Installare pacchetti usando package.json](#npmInstallPackage)

>[!NOTE]
> Per ASP.NET Core, è anche possibile usare [Library Manager](/aspnet/core/client-side/libman/?view=aspnetcore-3.1&preserve-view=true) o yarn anziché npm per installare i file JavaScript e CSS sul lato client.

### <a name="add-npm-support-to-a-project-aspnet-core"></a><a name="npmAdd"></a>Aggiungere il supporto npm a un progetto (ASP.NET Core)

Se il progetto non include già un file *package.json,* è possibile aggiungerne uno per abilitare il supporto npm aggiungendo un file *package.json* al progetto.

1. Se non è installato Node.js, è consigliabile installare la versione di [ LTS ](https://nodejs.org/en/download/) dal sito WebNode.jsper una migliore compatibilità con framework e librerie esterni.

   npm richiede Node.js.

1. Per aggiungere il file *package.json,* fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni e scegliere Aggiungi nuovo elemento  >   (o premere **CTRL**  +  **MAIUSC**  +  **A).** Scegliere il **file di configurazione npm**, usare il nome predefinito e fare clic su **Aggiungi**.

   ![Aggiungere package.json al progetto](../javascript/media/npm-add-package-json.png)

   Se il file di configurazione npm non è elencato, gli Node.js di sviluppo non sono installati. È possibile usare il Programma di installazione di Visual Studio per aggiungere il carico di **Node.js di** sviluppo. Ripetere quindi il passaggio precedente.

1. Includere uno o più pacchetti npm nella `dependencies` sezione o `devDependencies` di *package.json*. Ad esempio, è possibile aggiungere quanto segue al file:

   ```json
   "devDependencies": {
      "gulp": "4.0.2",
      "@types/jquery": "3.3.33"
   }
   ```

Quando si salva il file, Visual Studio il pacchetto nel nodo **Dipendenze/npm** in Esplora soluzioni. Se il nodo non viene visualizzato, fare clic con il pulsante destro del mouse **su package.json** e scegliere **Ripristina pacchetti**.

>[!NOTE]
> In alcuni scenari, Esplora soluzioni potrebbe non visualizzare lo stato corretto per i pacchetti npm installati. Per altre informazioni, vedere [Risoluzione dei problemi](#troubleshooting-npm-packages).

### <a name="install-packages-using-packagejson-aspnet-core"></a><a name="npmInstallPackage"></a>Installare pacchetti usando package.json (ASP.NET Core)

Per i progetti con npm incluso, è possibile configurare i pacchetti npm usando `package.json` . Fare clic con il pulsante destro del mouse sul nodo npm Esplora soluzioni e **scegliere Apri package.json**.

![Screenshot del Esplora soluzioni con il nodo npm selezionato. Viene aperto un menu di scelta rapida con il pulsante destro del mouse e viene selezionato Apri package.json.](../javascript/media/npm-add-package.png)

IntelliSense in *package.json* consente di selezionare una versione specifica di un pacchetto npm.

:::image type="content" source="../javascript/media/npm-add-package-intellisense.png" alt-text="Selezionare la versione del pacchetto npm" border="true":::

Quando si salva il file, Visual Studio il pacchetto nel nodo **Dipendenze/npm** in Esplora soluzioni. Se il nodo non viene visualizzato, fare clic con il pulsante destro del mouse **su package.json** e scegliere **Ripristina pacchetti**.

L'installazione di un pacchetto può richiedere alcuni minuti. Controllare lo stato di avanzamento dell'installazione del pacchetto passando all'output **npm** nella **finestra Output.**

![Output npm](../javascript/media/npm-output.png)

## <a name="troubleshooting-npm-packages"></a>Risoluzione dei problemi relativi ai pacchetti npm

* npm richiede Node.js Se non è installato Node.js, è consigliabile installare la versione LTS dal sito Web [Node.js](https://nodejs.org/en/download/) per garantire la migliore compatibilità con framework e librerie esterni.

* Per Node.js, è necessario che sia installato il carico **diNode.js di sviluppo** per il supporto npm.

* In alcuni scenari, Esplora soluzioni potrebbe non visualizzare lo stato corretto per i pacchetti npm installati a causa di un problema noto descritto [qui.](https://github.com/aspnet/Tooling/issues/479) Ad esempio, il pacchetto potrebbe essere visualizzato come non installato al momento dell'installazione. Nella maggior parte dei casi, è possibile aggiornare Esplora soluzioni eliminando *package.json,* riavviando Visual Studio e aggiungendo di nuovo il file *package.json* come descritto in precedenza in questo articolo. In caso contrario, quando si installano i pacchetti, è possibile usare la finestra di output npm per verificare lo stato dell'installazione.

* In alcuni ASP.NET Core, il nodo npm in Esplora soluzioni potrebbe non essere visibile dopo la compilazione del progetto. Per rendere nuovamente visibile il nodo, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Scarica Project.** Fare quindi clic con il pulsante destro del mouse sul nodo del **progetto e scegliere Ricarica Project**.

* Se vengono visualizzati errori durante la compilazione dell'app o la traslazione del codice TypeScript, verificare la presenza di incompatibilità del pacchetto npm come potenziale origine di errori. Per identificare gli errori, controllare la finestra di output npm durante l'installazione dei pacchetti, come descritto in precedenza in questo articolo. Ad esempio, se una o più versioni del pacchetto npm sono state deprecate e si verifica un errore, potrebbe essere necessario installare una versione più recente per correggere gli errori. Per informazioni sull'uso di *package.json* per controllare le versioni del pacchetto npm, vedere [Configurazione di package.json](../javascript/configure-packages-with-package-json.md).
