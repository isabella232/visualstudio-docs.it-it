---
title: Log del contenitore Docker, variabili di ambiente e accesso al file System
description: Viene descritto come migliorare la capacità di eseguire il debug e la diagnosi delle app basate su contenitori in Visual Studio usando una finestra degli strumenti per vedere cosa accade all'interno dei contenitori che ospitano l'app.
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 10/16/2019
ms.technology: vs-azure
monikerRange: vs-2019
ms.openlocfilehash: 355a08b2ff322226d347d999f4ec8a9ebb7ba5fc
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188718"
---
# <a name="how-to-view-and-diagnose-containers-and-images-in-visual-studio"></a>Come visualizzare e diagnosticare contenitori e immagini in Visual Studio

È possibile visualizzare gli elementi in corso all'interno dei contenitori che ospitano l'app usando la finestra **contenitori** . Se si è abituati a usare il prompt dei comandi per eseguire comandi di Docker per visualizzare e diagnosticare ciò che accade nei contenitori, questa finestra offre un modo più pratico per monitorare i contenitori senza uscire dall'IDE di Visual Studio.

## <a name="prerequisites"></a>Prerequisites

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- [Visual studio 2019 versione 16,4 Preview 2](https://visualstudio.microsoft.com/downloads) o successiva o se si usa una versione precedente di visual studio 2019, installare l'estensione della [finestra contenitori](https://aka.ms/vscontainerspreview).

## <a name="view-information-about-your-containers"></a>Visualizzare le informazioni sui contenitori

La finestra **contenitori** viene visualizzata automaticamente quando si avvia un progetto .NET in contenitori. Per visualizzare i contenitori in Visual Studio in qualsiasi momento, usare **Ctrl** +**Q** per attivare la casella di ricerca di visual studio e digitare `Containers` e scegliere il primo elemento. È anche possibile aprire la finestra **contenitori** dal menu principale. Utilizzare la **visualizzazione** percorso menu  > **altri** **contenitori** >  Windows.  

![Screenshot della scheda ambiente nella finestra contenitori](media/view-and-diagnose-containers/container-window.png)

Sul lato sinistro viene visualizzato l'elenco dei contenitori nel computer locale. I contenitori associati alla soluzione vengono visualizzati in **contenitori della soluzione**. A destra viene visualizzato un riquadro con schede per l' **ambiente**, le **porte**, i **log**e **i file**.

> [!TIP]
> È possibile personalizzare facilmente il punto in cui la finestra degli strumenti dei **contenitori** è ancorata in Visual Studio. Vedere [personalizzazione del layout delle finestre in Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md). Per impostazione predefinita, la finestra **contenitori** è ancorata alla finestra **espressioni di controllo** quando il debugger è in esecuzione.

## <a name="view-environment-variables"></a>Visualizzare le variabili di ambiente

La scheda **Environment (ambiente** ) Visualizza le variabili di ambiente nel contenitore. Per il contenitore dell'app, è possibile impostare queste variabili in molti modi, ad esempio in Dockerfile, in un file con estensione ENV oppure usando l'opzione-e quando si avvia un contenitore con un comando di Docker.

![Screenshot della scheda ambiente nella finestra contenitori](media/view-and-diagnose-containers/containers-environment-vars.png)

> [!NOTE]
> Tutte le modifiche apportate alle variabili di ambiente non vengono riflesse in tempo reale. Inoltre, le variabili di ambiente in questa scheda sono le variabili di ambiente di sistema nel contenitore e non riflettono le variabili di ambiente utente locali per l'app.

## <a name="view-port-mappings"></a>Visualizzare i mapping delle porte

Nella scheda **porte** è possibile controllare i mapping delle porte attivi per il contenitore.

![Screenshot della scheda porte nella finestra contenitori](media/view-and-diagnose-containers/containers-ports.png)

Le porte note sono collegate, quindi se è disponibile contenuto su una porta, è possibile fare clic sul collegamento per aprire il browser.

## <a name="view-logs"></a>Visualizzare i log

La scheda **logs** Mostra i risultati del comando `docker logs`. Per impostazione predefinita, la scheda Visualizza i flussi stdout e stderr in un contenitore, ma è possibile configurare l'output. Per informazioni dettagliate, vedere la pagina relativa alla [registrazione di Docker](https://docs.docker.com/config/containers/logging/).  Per impostazione predefinita, la scheda **logs** trasmette i log, ma è possibile disabilitarla scegliendo il pulsante **Interrompi** nella scheda.

![Screenshot della scheda log nella finestra contenitori](media/view-and-diagnose-containers/containers-logs.png)

Per cancellare i log, usare il pulsante **Cancella** nella scheda **logs** .  Per ottenere tutti i log, usare il pulsante **Aggiorna** .

> [!NOTE]
> Visual Studio reindirizza automaticamente stdout e stderr alla finestra di **output** quando si esegue senza eseguire il debug con i contenitori di Windows, quindi i contenitori di Windows avviati da Visual Studio con **CTRL** +**F5** non visualizzeranno i log in Questa scheda; usare invece la finestra **output** .

## <a name="view-the-filesystem"></a>Visualizzare il file System

Nella scheda **file** è possibile visualizzare il file System del contenitore, inclusa la cartella dell'app che contiene il progetto.

![Screenshot della scheda file nella finestra contenitori](media/view-and-diagnose-containers/container-filesystem.png)

Per aprire i file in Visual Studio, passare al file e fare doppio clic su di esso oppure fare clic con il pulsante destro del mouse e scegliere **Apri**. Visual Studio apre i file in modalità di sola lettura.

![Screenshot del file aperto per la visualizzazione in Visual Studio](media/view-and-diagnose-containers/container-file-open.png)

Usando la scheda **file** è possibile visualizzare i log delle applicazioni, ad esempio i log di IIS, i file di configurazione e altri file di contenuto nel file System del contenitore.

## <a name="start-stop-and-remove-containers"></a>Avviare, arrestare e rimuovere contenitori

Per impostazione predefinita, la finestra **contenitori** Mostra tutti i contenitori nel computer gestito da Docker. È possibile utilizzare i pulsanti della barra degli strumenti per avviare, arrestare o rimuovere (eliminare) un contenitore che non si desidera più.  Questo elenco viene aggiornato dinamicamente durante la creazione o la rimozione di contenitori.

## <a name="open-a-terminal-window-in-a-running-container"></a>Aprire una finestra del terminale in un contenitore in esecuzione

È possibile aprire una finestra del terminale (prompt dei comandi o la shell interattiva) nel contenitore usando il pulsante **Apri finestra terminale** nella finestra del **contenitore** .

![Screenshot della finestra Apri terminale nella finestra contenitori](media/view-and-diagnose-containers/containers-open-terminal-window.png)

Per i contenitori di Windows, viene visualizzato il prompt dei comandi di Windows. Per i contenitori Linux, apre una finestra usando la shell bash.

![Screenshot della finestra bash](media/view-and-diagnose-containers/container-bash-window.png)

In genere, la finestra del terminale si apre all'esterno di Visual Studio come finestra separata. Se si vuole che un ambiente della riga di comando sia integrato nell'IDE di Visual Studio come finestra degli strumenti ancorabile, è possibile installare il [terminale Whack Whack](https://marketplace.visualstudio.com/items?itemName=DanielGriffen.WhackWhackTerminal).

## <a name="attach-the-debugger-to-a-process"></a>Connetti il debugger a un processo

È possibile aggiungere il debugger a un processo in esecuzione nel contenitore usando il pulsante **Connetti a processo** sulla barra degli strumenti della finestra contenitori. Quando si usa questo pulsante, viene visualizzata la finestra **di dialogo Connetti a processo** che mostra i processi disponibili in esecuzione nel contenitore.  

![Screenshot della finestra di dialogo Connetti a processo](media/view-and-diagnose-containers/containers-attach-to-process.jpg)

È possibile connettersi ai processi gestiti nel contenitore. Per cercare un processo in un altro contenitore, usare il pulsante **trova** e selezionare un altro contenitore nella finestra di dialogo **Seleziona contenitore Docker** .

## <a name="viewing-images"></a>Visualizzazione di immagini

È anche possibile visualizzare le immagini nel computer locale usando la scheda **Immagini** nella finestra **contenitori** . Le immagini estratte da repository esterni vengono raggruppate in un oggetto TreeView. Selezionare un'immagine per esaminare i dettagli per l'immagine.

Per rimuovere un'immagine, fare clic con il pulsante destro del mouse sull'immagine nella visualizzazione albero e scegliere **Rimuovi**oppure selezionare l'immagine e utilizzare il pulsante **Rimuovi** sulla barra degli strumenti.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sugli strumenti contenitore disponibili in Visual Studio, vedere [Panoramica degli strumenti](overview.md)per i contenitori.

## <a name="see-also"></a>Vedere anche

[Sviluppo di contenitori in Visual Studio](/visualstudio/containers)

[Marketplace delle estensioni per Visual Studio](https://marketplace.visualstudio.com/)
