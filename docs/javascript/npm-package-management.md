---
title: Gestire pacchetti npm
description: Visual Studio consente di gestire i pacchetti usando il sistema di gestione pacchetti Node.js (npm)
ms.custom: seodec18
ms.date: 04/16/2020
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 6b53fb34b3cff444e57491f878f8385bdb523c6e
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85285049"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Gestire i pacchetti npm in Visual Studio

npm consente di installare e gestire i pacchetti per l'uso nelle applicazioni Node.js. Visual Studio semplifica l'interazione con npm e genera comandi npm direttamente o attraverso l'interfaccia utente. Se non si ha familiarità con npm e sono necessarie altre informazioni, consultare la [documentazione di npm](https://docs.npmjs.com/).

L'integrazione di Visual Studio con NPM è diversa a seconda del tipo di progetto.
* [Node.js](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [Apri cartella (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)

> [!Important]
> NPM prevede che la cartella *node_modules* e *package.js* nella radice del progetto. Se la struttura di cartelle dell'app è diversa, è necessario modificare la struttura di cartelle se si vuole gestire i pacchetti NPM con Visual Studio.

## <a name="nodejs-projects"></a>Progetti Node.js

Per Node.js progetti, è possibile eseguire le attività seguenti:
* [Installare i pacchetti da Esplora soluzioni](#npmInstallWindow)
* [Gestire i pacchetti installati da Esplora soluzioni](#solutionExplorer)
* [Usare il comando `.npm` nella finestra interattiva di Node.js](#interactive)

Queste funzionalità interagiscono e si sincronizzano con il sistema di progetto e il file *package.json* nel progetto.

### <a name="prerequisites"></a>Prerequisiti

Per aggiungere il supporto NPM al progetto sono necessari il carico di lavoro di **sviluppoNode.js** e il runtime di Node.js installato. Per i passaggi dettagliati, vedere [creare un Node.js progetto](/visualstudio/ide/quickstart-nodejs?toc=/visualstudio/javascript/toc.json).

> [!NOTE]
> Per i progetti di Node.js esistenti, usare il modello **di soluzione da codice Node.js esistente** o il tipo di progetto [cartella aperta (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md) per abilitare NPM nel progetto.

### <a name="install-packages-from-solution-explorer-nodejs"></a><a name="npmInstallWindow"></a>Installare i pacchetti da Esplora soluzioni (Node.js)

Per i progetti Node.js, il modo più semplice per installare i pacchetti NPM è tramite la finestra di installazione dei pacchetti NPM. Per accedere a questa finestra, fare clic con il pulsante destro del mouse sul nodo **npm** nel progetto e selezionare **Installa nuovi pacchetti npm**.

:::image type="content" source="../javascript/media/solution-explorer-install-package.png" alt-text="Installare nuovi pacchetti npm da esplora soluzioni" border="true":::

In questa finestra è possibile eseguire la ricerca di un pacchetto, specificare le opzioni ed eseguire l'installazione.

![Ricerca del pacchetto npm](../javascript/media/search-package.png)

* **Tipo di dipendenza**: scegliere tra i pacchetti **Standard**, **Sviluppo** e **Facoltativo**. Standard specifica che il pacchetto è una dipendenza di runtime, mentre Sviluppo specifica che il pacchetto è necessario solo durante lo sviluppo.
* **Aggiungi a package.json** -recommended. Questa opzione configurabile è deprecata.
* **Versione selezionata**: selezionare la versione del pacchetto da installare.
* **Altri argomenti di npm**: specificare altri argomenti di npm standard. Ad esempio, è possibile immettere un valore di versione come `@~0.8` per installare una versione specifica che non è disponibile nell'elenco delle versioni.

È possibile visualizzare lo stato di avanzamento dell'installazione nell'output **NPM** nella finestra **output** . Questa operazione potrebbe richiedere tempo.

![output NPM](../javascript/media/npm-output.png)

> [!TIP]
> È possibile cercare i pacchetti con ambito anteponendo la query di ricerca con l'ambito che interessa, ad esempio, digitare `@types/mocha` per cercare i file di definizione TypeScript per mocha. Inoltre, quando si installano le definizioni dei tipi per TypeScript, è possibile specificare la versione di TypeScript di destinazione aggiungendo `@ts2.6` nel campo argomento NPM.

### <a name="manage-installed-packages-in-solution-explorer-nodejs"></a><a name="solutionExplorer"></a>Gestione dei pacchetti installati in Esplora soluzioni (Node.js)

I pacchetti npm sono visualizzati in Esplora soluzioni. Le voci sotto il nodo **npm** simulano le dipendenze nel file *package.json*.

![Ricerca del pacchetto npm](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>Stato del pacchetto

* ![Pacchetto installato](../javascript/media/installed-npm.png) - Installato e indicato nel file package.json
* ![Pacchetto estraneo](../javascript/media/extraneous-npm.png): installato, ma non esplicitamente indicato nel file package.json
* ![Pacchetto mancante](../javascript/media/missing-npm.png) - Non installato ma indicato nel file package.json

::: moniker range=">=vs-2019"
Fare clic con il pulsante destro del mouse sul nodo **NPM** per eseguire una delle azioni seguenti:

* **Installare nuovi pacchetti NPM** Apre l'interfaccia utente per installare i nuovi pacchetti.
* **Installare i pacchetti NPM** Esegue il comando NPM install per installare tutti i pacchetti elencati in *package.json*. (Esegue `npm install` ).
* **Aggiornare i pacchetti NPM** Aggiorna i pacchetti alle versioni più recenti, in base all'intervallo di semver specificato in *package.json*. (Esegue `npm update --save` .). Gli intervalli di Semver vengono in genere specificati usando "~" o "^". Per ulteriori informazioni, [package.jssulla configurazione](../javascript/configure-packages-with-package-json.md).

Fare clic con il pulsante destro del mouse su un nodo del pacchetto per eseguire una delle azioni seguenti:

* **Installa pacchetto/i NPM** Esegue il comando NPM install per installare la versione del pacchetto elencata in *package.json*. (Esegue `npm install` ).
* **Aggiornare i pacchetti NPM** Aggiorna il pacchetto alla versione più recente, in base all'intervallo di semver specificato in *package.json*. (Eseguire `npm update --save` ). Gli intervalli di Semver vengono in genere specificati usando "~" o "^".
* **Disinstalla pacchetto/i NPM** Disinstalla il pacchetto e lo rimuove dalla *package.js* (esecuzioni `npm uninstall --save` ).
::: moniker-end
::: moniker range="vs-2017"
Fare clic con il pulsante destro del mouse su un nodo del pacchetto o sul nodo **npm** per effettuare una delle azioni seguenti:
* **Installare i pacchetti mancanti** indicati in *package.json*
* **Aggiornare i pacchetti NPM** alla versione più recente
* **Disinstallare un pacchetto** e rimuoverlo da *package.json*
::: moniker-end

>[!NOTE]
> Per informazioni sulla risoluzione dei problemi relativi ai pacchetti NPM, vedere [risoluzione dei](#troubleshooting-npm-packages)problemi.

### <a name="use-the-npm-command-in-the-nodejs-interactive-window-nodejs"></a><a name="interactive"></a>Usare il comando. NPM nella finestra Node.js interattiva (Node.js)

È anche possibile usare il comando `.npm` nella finestra interattiva di Node.js per eseguire i comandi npm. Per aprire la finestra, fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni e scegliere **Apri finestra interattiva di Node.js**.

Nella finestra è possibile usare comandi simili al seguente per installare un pacchetto:

`.npm install azure@4.2.3`

 > [!Tip]
 > Per impostazione predefinita, npm viene eseguito nella home directory del progetto. Se sono presenti più progetti nella soluzione, specificare il nome o il percorso del progetto tra parentesi quadre.
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > Se il progetto non contiene un file package.json, usare `.npm init -y` per creare un nuovo file package.json con le voci predefinite.

 ## <a name="aspnet-core-projects"></a>Progetti ASP.NET Core

Per progetti come ASP.NET Core progetti, è possibile integrare il supporto NPM nel progetto e usare NPM per installare i pacchetti.
* [Aggiungere il supporto NPM a un progetto](#npmAdd)
* [Installare i pacchetti usando package.json](#npmInstallPackage)

>[!NOTE]
> Per ASP.NET Core progetti, è anche possibile usare [Gestione librerie](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1) o Yarn anziché NPM per installare i file CSS e JavaScript sul lato client.

### <a name="add-npm-support-to-a-project-aspnet-core"></a><a name="npmAdd"></a>Aggiungere il supporto NPM a un progetto (ASP.NET Core)

Se il progetto non include già un *package.jssu* file, è possibile aggiungerne uno per abilitare il supporto di NPM aggiungendo un *package.jssul* file al progetto.

1. Se Node.js non è installato, si consiglia di installare la versione LTS dal sito Web di [Node.js](https://nodejs.org/en/download/) per ottenere la massima compatibilità con i Framework e le librerie esterni.

   NPM richiede Node.js.

1. Per aggiungere il *package.js* nel file, fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni e scegliere **Aggiungi**  >  **nuovo elemento**. Scegliere il **file di configurazione NPM**, usare il nome predefinito e fare clic su **Aggiungi**.

   ![Aggiungere package.jsal progetto](../javascript/media/npm-add-package-json.png)

   Se il file di configurazione NPM non è elencato, non sono installati Node.js strumenti di sviluppo. È possibile utilizzare il Programma di installazione di Visual Studio per aggiungere il carico di lavoro di **sviluppoNode.js** . Ripetere quindi il passaggio precedente.

1. Includere uno o più pacchetti NPM nella `dependencies` sezione o `devDependencies` di *package.json*. Ad esempio, è possibile aggiungere il codice seguente al file:

   ```json
   "devDependencies": {
      "gulp": "4.0.2",
      "@types/jquery": "3.3.33"
   }
   ```

Quando si salva il file, Visual Studio aggiunge il pacchetto nel nodo **dipendenze/NPM** in Esplora soluzioni. Se il nodo non è visibile, fare clic con il pulsante destro **del mouse supackage.js** e scegliere **Ripristina pacchetti**.

>[!NOTE]
> In alcuni scenari Esplora soluzioni possibile che non venga visualizzato lo stato corretto per i pacchetti NPM installati. Per altre informazioni, vedere [Risoluzione dei problemi](#troubleshooting-npm-packages).

### <a name="install-packages-using-packagejson-aspnet-core"></a><a name="npmInstallPackage"></a>Installare i pacchetti usando package.json (ASP.NET Core)

Per i progetti con NPM incluso, è possibile configurare i pacchetti NPM usando `package.json` . Fare clic con il pulsante destro del mouse sul nodo NPM in Esplora soluzioni e scegliere **apri package.jssu**.

![Ricerca del pacchetto npm](../javascript/media/npm-add-package.png)

IntelliSense in *package.json* consente di selezionare una particolare versione di un pacchetto NPM.

:::image type="content" source="../javascript/media/npm-add-package-intellisense.png" alt-text="Selezionare la versione del pacchetto NPM" border="true":::

Quando si salva il file, Visual Studio aggiunge il pacchetto nel nodo **dipendenze/NPM** in Esplora soluzioni. Se il nodo non è visibile, fare clic con il pulsante destro **del mouse supackage.js** e scegliere **Ripristina pacchetti**.

L'installazione di un pacchetto potrebbe richiedere alcuni minuti. Controllare l'avanzamento dell'installazione del pacchetto passando all'output di **NPM** nella finestra **output** .

![output NPM](../javascript/media/npm-output.png)

## <a name="troubleshooting-npm-packages"></a>Risoluzione dei problemi relativi ai pacchetti NPM

* NPM richiede Node.js se non è stato installato Node.js, è consigliabile installare la versione LTS dal sito Web di [Node.js](https://nodejs.org/en/download/) per la migliore compatibilità con le librerie e i framework esterni.

* Per Node.js progetti, è necessario avere installato il carico di lavoro di **sviluppoNode.js** per il supporto di NPM.

* In alcuni scenari Esplora soluzioni possibile che non venga visualizzato lo stato corretto per i pacchetti NPM installati a causa di un problema noto descritto [qui](https://github.com/aspnet/Tooling/issues/479). È ad esempio possibile che il pacchetto venga visualizzato come non installato al momento dell'installazione. Nella maggior parte dei casi, è possibile aggiornare Esplora soluzioni eliminando *package.js*, riavviando Visual Studio e aggiungendo nuovamente il *package.jssul* file come descritto in precedenza in questo articolo. In alternativa, quando si installano i pacchetti, è possibile usare la finestra di output NPM per verificare lo stato dell'installazione.

* Se si verificano errori durante la compilazione dell'app o il transimpilamento del codice TypeScript, verificare la presenza di incompatibilità del pacchetto NPM come origine potenziale di errori. Per semplificare l'identificazione degli errori, controllare la finestra di output di NPM durante l'installazione dei pacchetti, come descritto in precedenza in questo articolo. Se ad esempio una o più versioni del pacchetto NPM sono state deprecate e generano un errore, potrebbe essere necessario installare una versione più recente per correggere gli errori. Per informazioni sull'uso di *package.json* per controllare le versioni del pacchetto npm, vedere [Configurazione di package.json](../javascript/configure-packages-with-package-json.md).

