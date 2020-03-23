---
title: "Guida introduttiva: Creare per la prima volta un'app Node.js con Visual Studio"
description: In questa guida introduttiva verrà creata un'app Node.js in Visual Studio
ms.date: 06/27/2018
ms.technology: vs-javascript
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: f716421da3b9f888dbb7656c55db6814de88332b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "78235054"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>Guida introduttiva: Creare per la prima volta un'app Node.js con Visual Studio

In questa introduzione di 5-10 minuti all'ambiente di sviluppo integrato (IDE) di Visual Studio si creerà una semplice applicazione Web Node.js.

## <a name="prerequisites"></a>Prerequisites

* È necessario che siano installati Visual Studio e il carico di lavoro di sviluppo Node.js.

    ::: moniker range=">=vs-2019"
    Se non hai ancora installato Visual Studio 2019, vai alla pagina dei [download](https://visualstudio.microsoft.com/downloads) di Visual Studio per installarlo gratuitamente.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Se non hai ancora installato Visual Studio 2017, vai alla pagina dei [download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) di Visual Studio per installarlo gratuitamente.
    ::: moniker-end

    Se è necessario installare il carico di lavoro ma si dispone già di Visual Studio, passare a **Strumenti** > **Get Tools and Features...**, che apre il programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo Node.js**, quindi scegliere **Modifica**.

    ![Carico di lavoro Node.js nel programma di installazione di Visual Studio](../ide/media/quickstart-nodejs-workload.png)

* Il runtime di Node.js deve essere installato.

    Se non è installato, si consiglia di installare la versione LTS dal sito [Web Node.js](https://nodejs.org/en/download/) per la migliore compatibilità con framework e librerie esterni. Node.js è progettato per architetture a 32 e 64 bit. Gli strumenti Node.js in Visual Studio, inclusi nel carico di lavoro Node.js, supportano entrambe le versioni. Ne è richiesto solo uno e il programma di installazione Node.js supporta solo uno in fase di installazione alla volta.
    
    In generale, Visual Studio rileva automaticamente il runtime di Node.js installato. Se non rileva un runtime installato, è possibile configurare il progetto in modo che faccia riferimento al runtime installato nella pagina delle proprietà (dopo aver creato un progetto, aver fatto clic con il pulsante destro del mouse sul nodo del progetto, scegliere **Proprietà**e impostare il **percorso di Node.exe**). È possibile utilizzare un'installazione globale di Node.js oppure è possibile specificare il percorso di un interprete locale in ognuno dei progetti Node.js. 

## <a name="create-a-project"></a>Creare un progetto

Per prima cosa si crea un progetto di applicazione Web Node.js.

1. Se il runtime di Node.js non è già installato, installare la versione LTS dal sito Web [Node.js](https://nodejs.org/en/download/).

    Per altre informazioni, vedere i prerequisiti.

1. Aprire Visual Studio.

1. Creare un nuovo progetto.

    ::: moniker range=">=vs-2019"
    Premere **ESC** per chiudere la finestra iniziale. Premere **CTRL+Q** per aprire la casella di ricerca, digitare **Node.js**, quindi scegliere **Create new Blank Node.js Web application project** (Crea nuovo progetto applicazione Web Node.js vuoto) (JavaScript). Nella finestra di dialogo visualizzata scegliere **Crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dalla barra dei menu superiore, scegliere **File** > **Nuovo** > **progetto**. Nel riquadro di sinistra della finestra di dialogo **Nuovo progetto** espandere **JavaScript**, quindi selezionare **Node.js**. Nel riquadro centrale scegliere **Applicazione Web Node.js vuota**, quindi scegliere **OK**.
    ::: moniker-end
    Se il modello di progetto **Applicazione Web Node.js vuota** non compare, è necessario installare prima il carico di lavoro **Sviluppo Node.js**. Per istruzioni dettagliate, vedere i [Prerequisiti](#prerequisites).

    Visual Studio crea la nuova soluzione e apre il progetto. Nell'editor nel riquadro sinistro si apre *server.js*.

## <a name="explore-the-ide"></a>Esplorare l'IDE

1. Osservare **Esplora soluzioni** nel riquadro a destra.

   ![Esplora soluzioni](../ide/media/quickstart-nodejs-solution-explorer.png)

   - Il progetto viene visualizzato in grassetto, con il nome assegnato in precedenza nella finestra di dialogo **Nuovo progetto**. Su disco, questo progetto è rappresentato da un file *con estensione njsproj* nella cartella del progetto.

   - Al primo livello è presente una soluzione che, per impostazione predefinita, ha lo stesso nome del progetto. Una soluzione, rappresentata da un file *sln* su disco, è un contenitore per uno o più progetti correlati.

   - Il nodo npm visualizza tutti i pacchetti npm eventualmente installati. È possibile fare clic con il pulsante destro del mouse sul nodo npm per cercare e installare pacchetti npm tramite una finestra di dialogo.

1. Se si desidera installare i pacchetti npm o i comandi Node.js da un prompt dei comandi, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Apri prompt dei comandi qui**.

   ![Prompt dei comandi node.js](../ide/media/quickstart-nodejs-command-prompt.png)

1. Nel file *server.js* dell'editor (riquadro sinistro), scegliere `http.createServer` e premere **F12** oppure scegliere **Vai a definizione** dal menu di scelta rapida (attivato con il clic destro del mouse). Questo comando consente di passare `createServer` alla definizione della funzione in *index.d.ts*.

   ![Menu di scelta rapida Vai a definizione](../ide/media/quickstart-nodejs-gotodefinition.png)

1. Ritornare a *server.js*, posizionare il cursore alla fine della stringa di questa riga di codice, `res.end('Hello World\n');`, e modificarla come visualizzato di seguito:

    `res.end('Hello World\n' + res.connection.`

    Quando si digita `connection.` IntelliSense offre opzioni per il completamento automatico dell'immissione di codice.

   ![Completamento automatico di IntelliSense](../ide/media/quickstart-nodejs-intellisense.png)

1. Scegliere **localPort**, quindi digitare `);` per completare l'istruzione in modo che risulti simile alla seguente:

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-application"></a>Eseguire l'applicazione

1. Premere **CTRL**+**F5** (o **Esegui debug > Avvia senza eseguire debug**) per eseguire l'applicazione. L'app viene aperta in un browser.

1. Nella finestra del browser viene visualizzato "Hello World" e il numero della porta locale.

1. Chiudere il Web browser.

È stata completata la Guida introduttiva che ha fornito una panoramica dell'IDE di Visual Studio e di Node.js. Se si vuole approfondire la conoscenza relativa alle funzionalità, scegliere un'esercitazione nella sezione del sommario relativa alle **esercitazioni**.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Distribuire l'app nel servizio app di Linux](../javascript/publish-nodejs-app-azure.md)

- [Tutorial for Node.js and Express](../javascript/tutorial-nodejs.md) (Esercitazione per Node.js ed Express)
- [Tutorial for Node.js and React](../javascript/tutorial-nodejs-with-react-and-jsx.md) (Esercitazione per Node.js e React)