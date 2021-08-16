---
title: Visualizzare e diagnosticare contenitori e immagini Docker
description: Descrive come migliorare la capacità di eseguire il debug e diagnosticare le app basate su contenitori in Visual Studio usando una finestra degli strumenti per vedere cosa succede all'interno dei contenitori che ospitano l'app.
author: ghogen
ms.author: ghogen
ms.topic: how-to
ms.date: 01/20/2020
ms.technology: vs-container-tools
monikerRange: vs-2019
ms.openlocfilehash: 1895f67ae9ecb6bbad992ebbd891f326ec92aa52ae74a7d933f2d7a3127f9b9b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121363509"
---
# <a name="how-to-view-and-diagnose-containers-and-images-in-visual-studio"></a>Come visualizzare e diagnosticare contenitori e immagini in Visual Studio

È possibile visualizzare cosa succede all'interno dei contenitori che ospitano l'app usando la **finestra** Contenitori. Se si usa il prompt dei comandi per eseguire comandi Docker per visualizzare e diagnosticare cosa succede con i contenitori, questa finestra offre un modo più pratico per monitorare i contenitori senza uscire dall'IDE Visual Studio.

## <a name="prerequisites"></a>Prerequisiti

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- [Visual Studio 2019 versione 16.4 Preview 2](https://visualstudio.microsoft.com/downloads) o successiva oppure, se si usa una versione precedente di Visual Studio 2019, installare l'estensione della finestra Contenitori [.](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-containers-tools-extensions)

## <a name="view-information-about-your-containers"></a>Visualizzare informazioni sui contenitori

La **finestra Contenitori** si apre automaticamente all'avvio di un progetto .NET in contenitori. Per visualizzare i contenitori Visual Studio in qualsiasi momento, usare **CTRL** Q per attivare la casella di ricerca Visual Studio e digitare e +  scegliere il `Containers` primo elemento. È anche possibile aprire la **finestra** Contenitori dal menu principale. Usare il percorso del menu **Visualizza**  >  **altri Windows**  >  **contenitori**.  

![Screenshot della finestra Contenitori in Visual Studio con un contenitore selezionato nel riquadro sinistro e la scheda Ambiente selezionata nel riquadro destro.](media/view-and-diagnose-containers/container-window.png)

Sul lato sinistro viene visualizzato l'elenco dei contenitori nel computer locale. I contenitori associati alla soluzione sono visualizzati in **Contenitori della soluzione**. A destra viene visualizzato un riquadro con le schede **Ambiente**, **Porte**, **Log** e **File**.

> [!TIP]
> È possibile personalizzare facilmente la posizione **in cui la finestra** degli strumenti Contenitori è ancorata Visual Studio. Vedere [Personalizzazione dei layout delle finestre in Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md). Per impostazione predefinita, **la finestra** Contenitori è ancorata alla finestra **Espressioni** di controllo quando il debugger è in esecuzione.

## <a name="view-environment-variables"></a>Visualizzare le variabili di ambiente

La **scheda Ambiente** mostra le variabili di ambiente nel contenitore. Per il contenitore dell'app, è possibile impostare queste variabili in molti modi, ad esempio nel Dockerfile, in un file con estensione env o usando l'opzione -e quando si avvia un contenitore usando un comando Docker.

![Screenshot della finestra Contenitori in Visual Studio variabili di ambiente per il contenitore WebApplication11.](media/view-and-diagnose-containers/containers-environment-vars.png)

> [!NOTE]
> Eventuali modifiche alle variabili di ambiente non vengono riflesse in tempo reale. Inoltre, le variabili di ambiente in questa scheda sono le variabili di ambiente di sistema nel contenitore e non riflettono le variabili di ambiente utente locali per l'app.

## <a name="view-port-mappings"></a>Visualizzare i mapping delle porte

Nella scheda **Porte** è possibile controllare i mapping delle porte in vigore per il contenitore.

![Screenshot della scheda Porte nella finestra Contenitori](media/view-and-diagnose-containers/containers-ports.png)

Le porte note sono collegate, quindi se è disponibile contenuto su una porta, è possibile fare clic sul collegamento per aprire il browser.

## <a name="view-logs"></a>Visualizzare i log

La **scheda** Log mostra i risultati del `docker logs` comando. Per impostazione predefinita, la scheda mostra i flussi stdout e stderr in un contenitore, ma è possibile configurare l'output. Per informazioni dettagliate, vedere [Registrazione di Docker.](https://docs.docker.com/config/containers/logging/)  Per impostazione predefinita, **la scheda** Log consente di trasmettere i log, ma è possibile disabilitarla scegliendo il **pulsante** Arresta nella scheda.

![Screenshot della scheda Log nella finestra Contenitori](media/view-and-diagnose-containers/containers-logs.png)

Per cancellare i log, usare il **pulsante** Cancella nella **scheda** Log.  Per ottenere tutti i log, usare il **pulsante** Aggiorna.

> [!NOTE]
> Visual Studio reindirizza automaticamente stdout e stderr alla finestra **Output** quando si esegue senza eseguire il debug con contenitori Windows, quindi i contenitori Windows avviati da Visual Studio usando **CTRL** + **F5** non visualizzano i log in questa scheda. Usare invece la finestra **Output.**

## <a name="view-the-filesystem"></a>Visualizzare il file system

Nella scheda **File** è possibile visualizzare il file system del contenitore, inclusa la cartella dell'app che contiene il progetto.

![Screenshot della scheda File nella finestra Contenitori](media/view-and-diagnose-containers/container-filesystem.png)

Per aprire i file in Visual Studio, passare al file e fare doppio clic su di esso oppure fare clic con il pulsante destro del mouse e scegliere **Apri**. Visual Studio apre i file in modalità di sola lettura.

![Screenshot del file aperto per la visualizzazione in Visual Studio](media/view-and-diagnose-containers/container-file-open.png)

La scheda **File** consente di visualizzare i log dell'applicazione, ad esempio i log di IIS, i file di configurazione e altri file di contenuto nel file system del contenitore.

## <a name="start-stop-and-remove-containers"></a>Avviare, arrestare e rimuovere contenitori

Per impostazione predefinita, **la finestra** Contenitori mostra tutti i contenitori nel computer gestiti da Docker. È possibile usare i pulsanti della barra degli strumenti per avviare, arrestare o rimuovere (eliminare) un contenitore non più desiderato.  Questo elenco viene aggiornato dinamicamente quando i contenitori vengono creati o rimossi.

## <a name="open-a-terminal-window-in-a-running-container"></a>Aprire una finestra del terminale in un contenitore in esecuzione

È possibile aprire una finestra del terminale (prompt dei comandi o shell interattiva) nel contenitore usando il pulsante Apri finestra **terminale** nella **finestra Contenitore.**

![Screenshot della finestra Apri terminale nella finestra Contenitori](media/view-and-diagnose-containers/containers-open-terminal-window.png)

Per Windows contenitori, viene aperto Windows prompt dei comandi. Per i contenitori Linux, apre una finestra usando la shell bash.

![Screenshot della finestra bash](media/view-and-diagnose-containers/container-bash-window.png)

In genere, la finestra del terminale si apre Visual Studio come finestra separata. Se si vuole un ambiente da riga di comando integrato nell'IDE Visual Studio come finestra degli strumenti ancorabile, è possibile installare [Wnette Wnette Terminal](https://marketplace.visualstudio.com/items?itemName=DanielGriffen.WhackWhackTerminal).

## <a name="attach-the-debugger-to-a-process"></a>Connettere il debugger a un processo

È possibile connettere il debugger a un processo in  esecuzione nel contenitore usando il pulsante Collega a processo sulla barra degli strumenti della finestra Contenitori. Quando si usa questo pulsante, viene **visualizzata la** finestra di dialogo Collega a processo che mostra i processi disponibili in esecuzione nel contenitore.  

![Screenshot della finestra di dialogo Collega a processo](media/view-and-diagnose-containers/containers-attach-to-process.jpg)

È possibile connettersi ai processi gestiti nel contenitore. Per cercare un processo in un altro contenitore, usare il **pulsante** Trova e selezionare un altro contenitore nella **finestra di dialogo Seleziona contenitore Docker.**

## <a name="viewing-images"></a>Visualizzazione di immagini

È anche possibile visualizzare le immagini nel computer locale usando la **scheda Immagini** nella **finestra** Contenitori. Le immagini estrasse da repository esterni vengono raggruppate in una visualizzazione albero. Selezionare un'immagine per esaminare i dettagli dell'immagine.

Per rimuovere un'immagine, fare clic con il pulsante destro del mouse sull'immagine nella visualizzazione albero e scegliere **Rimuovi** oppure selezionare l'immagine e usare il **pulsante** Rimuovi sulla barra degli strumenti.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sugli strumenti contenitore disponibili in Visual Studio, vedere Panoramica [di Strumenti contenitore](overview.md).

## <a name="see-also"></a>Vedi anche

[Sviluppo di contenitori in Visual Studio](./index.yml)

[Marketplace delle estensioni per Visual Studio](https://marketplace.visualstudio.com/)