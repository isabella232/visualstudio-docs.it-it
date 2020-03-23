---
title: Log del contenitore Docker, variabili di ambiente e accesso al file systemDocker container logs, environment variables, and file system access
description: Viene descritto come migliorare la capacità di eseguire il debug e diagnosticare le app basate su contenitori in Visual Studio usando una finestra degli strumenti per vedere cosa succede all'interno dei contenitori che ospitano l'app.
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 01/20/2020
ms.technology: vs-azure
monikerRange: vs-2019
ms.openlocfilehash: b4670c003c06f8d16979589a4dce5abf33d5e27d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027298"
---
# <a name="how-to-view-and-diagnose-containers-and-images-in-visual-studio"></a>Come visualizzare e diagnosticare contenitori e immagini in Visual StudioHow to view and diagnose containers and images in Visual Studio

Puoi visualizzare cosa succede all'interno dei contenitori che ospitano la tua app usando la finestra **Contenitori.** Se si è abituati a utilizzare il prompt dei comandi per eseguire i comandi Docker per visualizzare e diagnosticare ciò che sta succedendo con i contenitori, questa finestra fornisce un modo più pratico per monitorare i contenitori senza uscire dall'IDE di Visual Studio.

## <a name="prerequisites"></a>Prerequisites

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- [Visual Studio 2019 versione 16.4 Preview 2](https://visualstudio.microsoft.com/downloads) o versione successiva oppure, se si usa una versione precedente di Visual Studio 2019, installare l'estensione della [finestra Contenitori](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-containers-tools-extensions).

## <a name="view-information-about-your-containers"></a>Visualizzare le informazioni sui contenitori

La finestra **Contenitori** si apre automaticamente quando si avvia un progetto .NET con contenitore. Per visualizzare i contenitori in Visual Studio in qualsiasi momento, usare `Containers` **Ctrl**+**Q** per attivare la casella di ricerca di Visual Studio e digitare e scegliere il primo elemento. È anche possibile aprire la finestra **Contenitori** dal menu principale. Utilizzare il percorso di menu **View** > **Other Windows** > **Containers**.  

![Screenshot della scheda Ambiente nella finestra Contenitori](media/view-and-diagnose-containers/container-window.png)

Sul lato sinistro viene visualizzato l'elenco dei contenitori nel computer locale. I contenitori associati alla soluzione vengono visualizzati in **Contenitori di soluzioni**. A destra viene visualizzato un riquadro con le schede **Ambiente**, **Porte**, **Registri**e **File**.

> [!TIP]
> È possibile personalizzare facilmente la posizione in cui la finestra degli strumenti **Contenitori** è ancorata in Visual Studio.You can easily customize where the Containers tool window is docked in Visual Studio. Vedere [Personalizzazione dei layout di finestra in Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md). Per impostazione predefinita, la finestra **Contenitori** viene ancorata alla finestra **Espressioni di** controllo quando il debugger è in esecuzione.

## <a name="view-environment-variables"></a>Visualizzare le variabili di ambiente

La scheda **Ambiente** mostra le variabili di ambiente nel contenitore. Per il contenitore dell'app, puoi impostare queste variabili in molti modi, ad esempio nel file Docker, in un file con estensione env o usando l'opzione -e quando avvii un contenitore usando un comando Docker.

![Screenshot della scheda Ambiente nella finestra Contenitori](media/view-and-diagnose-containers/containers-environment-vars.png)

> [!NOTE]
> Eventuali modifiche alle variabili di ambiente non vengono riflesse in tempo reale. Inoltre, le variabili di ambiente in questa scheda sono le variabili di ambiente di sistema nel contenitore e non riflettono le variabili di ambiente utente locali per l'app.

## <a name="view-port-mappings"></a>Visualizzare i mapping delle porte

Nella scheda **Porte** è possibile controllare i mapping delle porte in vigore per il contenitore.

![Screenshot della scheda Porte nella finestra Contenitori](media/view-and-diagnose-containers/containers-ports.png)

Le porte note sono collegate, quindi se c'è contenuto disponibile su una porta, è possibile fare clic sul collegamento per aprire il browser.

## <a name="view-logs"></a>Visualizzare i log

La scheda **Registri** mostra `docker logs` i risultati del comando. Per impostazione predefinita, la scheda mostra i flussi stdout e stderr in un contenitore, ma è possibile configurare l'output. Per informazioni dettagliate, vedere [Registrazione Docker](https://docs.docker.com/config/containers/logging/).  Per impostazione predefinita, la scheda **Registri** trasmette i log, ma è possibile disabilitarlo scegliendo il pulsante **Interrompi** nella scheda.

![Screenshot della scheda Registri nella finestra Contenitori](media/view-and-diagnose-containers/containers-logs.png)

Per cancellare i registri, utilizzare il pulsante **Cancella** nella scheda **Registri.**  Per ottenere tutti i log, utilizzare il pulsante **Aggiorna.**

> [!NOTE]
> Visual Studio reindirizza automaticamente stdout e stderr alla finestra **di output** quando si esegue il debug senza eseguire il debug con i contenitori di Windows, pertanto i contenitori di Windows avviati da Visual Studio usando **Ctrl**+**F5** non visualizzano i log in questa scheda; utilizzare invece la finestra **Output.**

## <a name="view-the-filesystem"></a>Visualizzare il file system

Nella scheda **File** è possibile visualizzare il file system del contenitore, inclusa la cartella dell'app che contiene il progetto.

![Schermata della scheda File nella finestra Contenitori](media/view-and-diagnose-containers/container-filesystem.png)

Per aprire i file in Visual Studio, individuare il file e fare doppio clic su di esso oppure fare clic con il pulsante destro del mouse e scegliere **Apri**. Visual Studio apre i file in modalità di sola lettura.

![Screenshot del file aperto per la visualizzazione in Visual Studio](media/view-and-diagnose-containers/container-file-open.png)

La scheda **File** consente di visualizzare i registri delle applicazioni, ad esempio i registri di IIS, i file di configurazione e altri file di contenuto nel file system del contenitore.

## <a name="start-stop-and-remove-containers"></a>Avviare, arrestare e rimuovere i contenitoriStart, stop, and remove containers

Per impostazione predefinita, la finestra **Contenitori** mostra tutti i contenitori nel computer gestito da Docker.By default, the Containers window shows all containers on the machine that Docker manages. È possibile utilizzare i pulsanti della barra degli strumenti per avviare, arrestare o rimuovere (eliminare) un contenitore non più desiderato.  Questo elenco viene aggiornato dinamicamente quando i contenitori vengono creati o rimossi.

## <a name="open-a-terminal-window-in-a-running-container"></a>Aprire una finestra del terminale in un contenitore in esecuzione

È possibile aprire una finestra del terminale (prompt dei comandi o shell interattiva) nel contenitore utilizzando il pulsante **Apri finestra terminale** nella finestra **Contenitore.**

![Screenshot della finestra Apri terminale nella finestra Contenitori](media/view-and-diagnose-containers/containers-open-terminal-window.png)

Per i contenitori Windows, viene aperto il prompt dei comandi di Windows.For Windows containers, the Windows command prompt opens. Per i contenitori Linux, si apre una finestra utilizzando la shell bash.

![Schermata della finestra bash](media/view-and-diagnose-containers/container-bash-window.png)

In genere, la finestra del terminale si apre all'esterno di Visual Studio come finestra separata. Se si desidera un ambiente della riga di comando integrato nell'IDE di Visual Studio come finestra degli strumenti ancorabile, è possibile installare [Whack Whack Terminal](https://marketplace.visualstudio.com/items?itemName=DanielGriffen.WhackWhackTerminal).

## <a name="attach-the-debugger-to-a-process"></a>Connettere il debugger a un processo

È possibile connettere il debugger a un processo in esecuzione nel contenitore utilizzando il pulsante **Connetti a processo** sulla barra degli strumenti della finestra Contenitori. Quando si utilizza questo pulsante, viene visualizzata la finestra di dialogo **Connetti a processo** con i processi disponibili in esecuzione nel contenitore.  

![Schermata della finestra di dialogo Connetti a processo](media/view-and-diagnose-containers/containers-attach-to-process.jpg)

È possibile connettersi ai processi gestiti nel contenitore. Per cercare un processo in un altro contenitore, usare il pulsante **Trova** e selezionare un altro contenitore nella finestra di dialogo **Seleziona contenitore docker.**

## <a name="viewing-images"></a>Visualizzazione delle immagini

È inoltre possibile visualizzare le immagini nel computer locale utilizzando la scheda **Immagini** nella finestra **Contenitori.** Le immagini estratte da repository esterni vengono raggruppate in una visualizzazione albero. Selezionare un'immagine per esaminare i dettagli dell'immagine.

Per rimuovere un'immagine, fare clic con il pulsante destro del mouse sull'immagine nella struttura ad albero e scegliere **Rimuovi**oppure selezionare l'immagine e utilizzare il pulsante **Rimuovi** sulla barra degli strumenti.

## <a name="next-steps"></a>Passaggi successivi

Per ulteriori informazioni sugli strumenti contenitore disponibili in Visual Studio, leggere Cenni preliminari sugli [strumenti contenitore](overview.md).

## <a name="see-also"></a>Vedere anche

[Sviluppo di contenitori in Visual StudioContainer Development in Visual Studio](/visualstudio/containers)

[Estensioni Marketplace per Visual Studio](https://marketplace.visualstudio.com/)
