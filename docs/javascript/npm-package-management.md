---
title: Gestire pacchetti npm
description: Visual Studio consente di gestire i pacchetti usando il sistema di gestione pacchetti Node.js (npm)
ms.custom: seodec18
ms.date: 06/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: de92c3f1f0d0e29d1ba2dfaf5d536a42e636be2c
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409457"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Gestire i pacchetti npm in Visual Studio

npm consente di installare e gestire i pacchetti per l'uso nelle applicazioni Node.js. Se non si ha familiarità con npm e sono necessarie altre informazioni, consultare la [documentazione di npm](https://docs.npmjs.com/).

Visual Studio semplifica l'interazione con npm e genera comandi npm direttamente o attraverso l'interfaccia utente. È possibile usare i seguenti metodi:
* [Installare i pacchetti da Esplora soluzioni](#npmInstallWindow)
* [Gestire i pacchetti installati da Esplora soluzioni](#solutionExplorer)
* [Usare il comando `.npm` nella finestra interattiva di Node.js](#interactive)

Queste funzionalità interagiscono e si sincronizzano con il sistema di progetto e il file *package.json* nel progetto.

> [!Important]
> npm si aspetta che la cartella *node_modules* e *package.json* si trovino nella radice del progetto. Se la struttura di cartelle dell'app è diversa, è necessario aggiornare la struttura di cartelle se si vuole gestire i pacchetti NPM con Visual Studio.

> [!NOTE]
> Per i progetti NPM esistenti, usare il modello **di soluzione di codice node. js esistente** .

## <a name="npmInstallWindow"></a> Installare i pacchetti da Esplora soluzioni

Il modo più semplice di installare i pacchetti npm è usare la finestra di installazione dei pacchetti npm. Per accedere a questa finestra, fare clic con il pulsante destro del mouse sul nodo **npm** nel progetto e selezionare **Installa nuovi pacchetti npm**.

![Installare nuovi pacchetti npm da esplora soluzioni](../javascript/media/solution-explorer-install-package.png)

In questa finestra è possibile eseguire la ricerca di un pacchetto, specificare le opzioni ed eseguire l'installazione.

![Ricerca del pacchetto npm](../javascript/media/search-package.png)

* **Tipo di dipendenza**: scegliere tra i pacchetti **Standard**, **Sviluppo** e **Facoltativo**. Standard specifica che il pacchetto è una dipendenza di runtime, mentre Sviluppo specifica che il pacchetto è necessario solo durante lo sviluppo.
* **Aggiungi a package.json**: questa opzione è deprecata
* **Versione selezionata**: selezionare la versione del pacchetto da installare.
* **Altri argomenti di npm**: specificare altri argomenti di npm standard. Ad esempio, è possibile immettere un valore di versione come `@~0.8` per installare una versione specifica che non è disponibile nell'elenco delle versioni.

È possibile visualizzare lo stato di avanzamento dell'installazione nella scheda npm nella finestra Output. Questa operazione potrebbe richiedere tempo.

> [!TIP]
> È possibile cercare i pacchetti con ambito anteponendo la query di ricerca con l'ambito che interessa, ad esempio, digitare `@types/mocha` per cercare i file di definizione TypeScript per mocha. Inoltre, quando si installano le definizioni di tipo per TypeScript, è possibile specificare la versione di TypeScript di destinazione aggiungendo `@ts2.6` nel campo dell'argomento npm.

## <a name="solutionExplorer"></a>Gestire i pacchetti installati in Esplora soluzioni

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

## <a name="interactive"></a>Usare il comando .npm nella finestra interattiva di Node.js

È anche possibile usare il comando `.npm` nella finestra interattiva di Node.js per eseguire i comandi npm. Per aprire la finestra, fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni e scegliere **Apri finestra interattiva di Node.js**.

Nella finestra è possibile usare comandi simili al seguente per installare un pacchetto:

`.npm install azure@4.2.3`

 > [!Tip]
 > Per impostazione predefinita, npm viene eseguito nella home directory del progetto. Se sono presenti più progetti nella soluzione, specificare il nome o il percorso del progetto tra parentesi quadre.
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > Se il progetto non contiene un file package.json, usare `.npm init -y` per creare un nuovo file package.json con le voci predefinite.
