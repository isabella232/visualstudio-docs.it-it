---
title: Creare la prima Node.js app
ms.custom:
- acquisition
- SEO-VS-2020
description: In questa guida introduttiva verrà creata un'app Node.js in Visual Studio
ms.date: 03/25/2021
ms.technology: vs-javascript
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: d9397cb121ab3aa68d368a0cc7e1ab709411f6b6
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2021
ms.locfileid: "112113158"
---
# <a name="quickstart-create-your-first-nodejs-app-with-visual-studio"></a>Avvio rapido: Creare la prima app Node.js con Visual Studio

In questa introduzione da 5 a 10 minuti all'ambiente di sviluppo integrato (IDE) di Visual Studio verrà creata una semplice app Node.js Web.

## <a name="prerequisites"></a>Prerequisiti

Prima di iniziare, installare Visual Studio e configurare l'ambiente Node.js locale.

### <a name="install-visual-studio"></a>Installare Visual Studio

::: moniker range=">=vs-2019"
Se non è già stato installato Visual Studio 2019, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.
::: moniker-end
::: moniker range="vs-2017"
Se Visual Studio 2017 non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.
::: moniker-end

### <a name="set-up-your-nodejs-environment"></a>Configurare l'ambiente Node.js locale

Visual Studio consente di configurare l'ambiente, inclusa l'installazione di strumenti comuni con Node.js sviluppo.

1. In Visual Studio passare a **Strumenti**  >  **Ottieni strumenti e funzionalità**.

1. Nella finestra Programma di installazione di Visual Studio scegliere il caricoNode.js **di** sviluppo e selezionare **Modifica** per scaricare e installare il carico di lavoro.

    ![Node.js carico di lavoro in Programma di installazione di Visual Studio](../ide/media/quickstart-nodejs-workload.png)

1. Installare la versione LTS del [runtimeNode.js.](https://nodejs.org/en/download/) È consigliabile usare la versione LTS per garantire la migliore compatibilità con framework e librerie esterni.

    Anche Node.js è compilato per architetture a 32 bit e a 64 bit, il programma di installazione Node.js supporta solo una versione installata alla volta.

1. Se Visual Studio non rileva il runtime installato (in genere), configurare il progetto per fare riferimento al runtime installato:

   1. Dopo aver [creato il progetto,](#create-your-app-project)fare clic con il pulsante destro del mouse sul nodo del progetto.

   1. Selezionare **Proprietà** e impostare il **percorsoNode.exe.** È possibile usare un'installazione globale di Node.js o specificare il percorso di un interprete locale in ogni progetto Node.js progetto.

## <a name="create-your-app-project"></a>Creare il progetto di app

1. Se non è ancora stato fatto, installare la versione LTS [ dell'Node.js runtime](https://nodejs.org/en/download/). Per altre informazioni, vedere i [prerequisiti](#prerequisites).

1. Aprire Visual Studio.

1. Creare un nuovo progetto.

    ::: moniker range=">=vs-2019"

    1. Premere **ESC** per chiudere la finestra iniziale.

    1. Premere **CTRL+Q per** aprire la casella di ricerca, quindi **digitareNode.js**.

    1. Scegliere **Blank Node.js Web Application (JavaScript)**. Nella finestra di dialogo selezionare **Crea**.

    ::: moniker-end

    ::: moniker range="vs-2017"
    1. Nella barra dei menu superiore scegliere **File** > **nuovo** > **progetto**.

    1. Nel riquadro sinistro della finestra di dialogo **Nuovo** progetto espandere **JavaScript** e **scegliereNode.js**.

    1. Nel riquadro centrale scegliere Blank **Node.js Web application (Applicazione Web vuota)** e selezionare **OK**.

    ::: moniker-end
    
    Se il modello di progetto **Applicazione Web Node.js vuota** non compare, è necessario installare prima il carico di lavoro **Sviluppo Node.js**. Per istruzioni dettagliate, vedere i [prerequisiti](#prerequisites).

    Visual Studio crea e apre il progetto. Il file *server.js* del progetto viene aperto nell'editor a sinistra.

## <a name="explore-the-ide"></a>Esplorare l'IDE

1. Nel riquadro destro esaminare Esplora soluzioni **.**

   ![Esplora soluzioni](../ide/media/quickstart-nodejs-solution-explorer.png)

   - Evidenziato in grassetto è il progetto, usando il nome specificato al momento della configurazione del progetto. Su disco, questo progetto è rappresentato da un file con estensione *njsproj* nella cartella del progetto.

   - Al primo livello è presente una soluzione che, per impostazione predefinita, ha lo stesso nome del progetto. Una soluzione, rappresentata da un file *sln* su disco, è un contenitore per uno o più progetti correlati.

   - Il **nodo npm** mostra i pacchetti npm installati. È possibile fare clic con il pulsante destro del mouse sul nodo npm per cercare e installare pacchetti npm usando una finestra di dialogo.

1. Se si desidera installare pacchetti npm o Node.js comandi da un prompt dei comandi, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Apri prompt dei comandi qui**.

   ![Prompt dei comandi di Node dot j s](../ide/media/quickstart-nodejs-command-prompt.png)

1. Se si vuole testare la navigazione nel codice sorgente, dal file *openserver.js* selezionare **http.createServer** e premere **F12** o scegliere **Vai** a definizione dal menu di scelta rapida (fare clic con il pulsante destro del mouse). Questo comando consente di accedere alla definizione della `createServer` funzione in *http.d.ts*.

   ![Menu di scelta rapida Vai a definizione](../ide/media/quickstart-nodejs-gotodefinition.png)

1. Tornare a *server.js* e individuare questa riga di codice: `res.end('Hello World\n');` . Modificare il codice come segue:

    `res.end('Hello World\n' + res.connection.`

    Quando si digita **connection.**, IntelliSense offre opzioni per completare automaticamente la voce di codice.

   ![Completamento automatico di IntelliSense](../ide/media/quickstart-nodejs-intellisense.png)

1. Scegliere **localPort** e digitare **);** per completare l'istruzione:

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-app"></a>Eseguire l'app

1. Premere **CTRL+F5** (o **Avvia debug** senza eseguire  >  **debug**) per eseguire l'app. 
 
   L'app viene aperta in un browser.

1. Nel browser verificare che sia visualizzato un messaggio "Hello World" e il numero di porta locale.

Congratulazioni. È stata creata un'app Node.js semplice con Visual Studio. Per approfondire il contenuto, continuare nella **sezione Esercitazioni** del sommario.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Distribuire l'app nel servizio app di Linux](../javascript/publish-nodejs-app-azure.md)

> [!div class="nextstepaction"]
> [Tutorial for Node.js and Express](../javascript/tutorial-nodejs.md) (Esercitazione per Node.js ed Express)

> [!div class="nextstepaction"]
> [Tutorial for Node.js and React](../javascript/tutorial-nodejs-with-react-and-jsx.md) (Esercitazione per Node.js e React)
