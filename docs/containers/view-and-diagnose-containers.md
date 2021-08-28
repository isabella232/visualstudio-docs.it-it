---
title: Usare la finestra Contenitori in Visual Studio
description: Descrive come migliorare la possibilità di eseguire il debug e la diagnosi delle app basate su contenitori in Visual Studio usando la finestra degli strumenti Contenitori per visualizzare variabili di ambiente, file, log, porte e altri contenitori che ospitano l'app, nonché le immagini Docker disponibili in locale.
author: ghogen
ms.author: ghogen
ms.topic: how-to
ms.date: 01/20/2020
ms.technology: vs-container-tools
monikerRange: vs-2019
ms.openlocfilehash: d6e4ce1e92afea971d02242c03595020d27c23e3
ms.sourcegitcommit: 8f8804b885c3a68f20bf0e9fe3729f2764145815
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2021
ms.locfileid: "123096808"
---
# <a name="use-the-containers-window"></a>Usare la finestra Contenitori

È possibile visualizzare il contenuto dei contenitori che ospitano l'app usando la **finestra Contenitori.** Se si è utenti che usano il prompt dei comandi per eseguire comandi Docker per visualizzare e diagnosticare ciò che succede con i contenitori, questa finestra offre un modo più pratico per monitorare i contenitori senza uscire dall'IDE di Visual Studio.

È anche possibile visualizzare informazioni sulle immagini del contenitore usando la **finestra Contenitori.**

## <a name="prerequisites"></a>Prerequisiti

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- [Visual Studio 2019 versione 16.4 o](https://visualstudio.microsoft.com/downloads) successiva.

## <a name="view-information-about-your-containers"></a>Visualizzare le informazioni sui contenitori

La **finestra Contenitori** viene aperta automaticamente quando si avvia un progetto .NET in contenitori. Per visualizzare i contenitori in Visual Studio in qualsiasi momento, usare **CTRL** Q per attivare la casella di ricerca Visual Studio e digitare e +  scegliere il `Containers` primo elemento. È anche possibile aprire **la finestra** Contenitori dal menu principale. Usare il percorso del menu  >  **Visualizza altri Windows**  >  **contenitori**.  

![Screenshot della finestra Contenitori in Visual Studio con un contenitore selezionato nel riquadro sinistro e la scheda Ambiente selezionata nel riquadro destro.](media/view-and-diagnose-containers/container-window.png)

Sul lato sinistro viene visualizzato l'elenco dei contenitori nel computer locale. I contenitori associati alla soluzione vengono visualizzati in **Contenitori della soluzione.** A destra viene visualizzato un riquadro con le schede **Ambiente** **,** Etichette , **Porte**, **Volumi**, **Log** e **File**.

> [!TIP]
> È possibile personalizzare facilmente il punto **in cui la finestra degli** strumenti Contenitori è ancorata Visual Studio. Vedere [Personalizzazione del layout delle finestre in Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md). Per impostazione predefinita, **la finestra Contenitori** è ancorata alla **finestra** Espressioni di controllo quando il debugger è in esecuzione.

## <a name="view-environment-variables"></a>Visualizzare le variabili di ambiente

La **scheda Ambiente** mostra le variabili di ambiente nel contenitore. Per il contenitore dell'app, è possibile impostare queste variabili in molti modi, ad esempio nel Dockerfile, in un file con estensione env o usando l'opzione -e quando si avvia un contenitore usando un comando Docker.

![Screenshot della finestra Contenitori in Visual Studio le variabili di ambiente per un contenitore.](media/view-and-diagnose-containers/containers-environment-vars.png)

> [!NOTE]
> Le modifiche apportate alle variabili di ambiente non vengono riflesse in tempo reale. Inoltre, le variabili di ambiente in questa scheda sono le variabili di ambiente di sistema nel contenitore e non riflettono le variabili di ambiente dell'utente locali per l'app.

## <a name="view-labels"></a>Visualizzare le etichette

La **scheda Etichette** mostra le etichette per il contenitore. Le etichette sono un modo per impostare metadati personalizzati sugli oggetti Docker. Alcune etichette vengono impostate automaticamente Visual Studio.

![Screenshot della finestra Contenitori in Visual Studio la scheda Etichette](media/view-and-diagnose-containers/containers-labels.png)

## <a name="view-port-mappings"></a>Visualizzare i mapping delle porte

Nella **scheda Porte** è possibile controllare i mapping delle porte in vigore per il contenitore.

![Screenshot della scheda Porte nella finestra Contenitori](media/view-and-diagnose-containers/containers-ports.png)

Le porte note sono collegate, quindi se è disponibile contenuto su una porta, è possibile fare clic sul collegamento per aprire il browser.

## <a name="view-volumes"></a>Visualizzare volumi

La **scheda Volumi** mostra i volumi (nodi del file system montati) nel contenitore.

![Screenshot della scheda Volumi nella finestra Contenitori](media/view-and-diagnose-containers/containers-volumes.png)

## <a name="view-logs"></a>Visualizzare i log

La **scheda** Logs (Log) mostra i risultati del `docker logs` comando. Per impostazione predefinita, la scheda mostra i flussi stdout e stderr in un contenitore, ma è possibile configurare l'output. Per informazioni dettagliate, vedere [Registrazione di Docker.](https://docs.docker.com/config/containers/logging/)  Per impostazione predefinita, **la scheda** Log esegue lo streaming dei log, ma è possibile disabilitarla scegliendo il **pulsante** Arresta nella scheda.

![Screenshot della scheda Log nella finestra Contenitori](media/view-and-diagnose-containers/containers-logs.png)

Per cancellare i log, usare **il pulsante** Cancella nella **scheda** Log.  Per ottenere tutti i log, usare il **pulsante** Aggiorna.

> [!NOTE]
> Visual Studio reindirizza automaticamente stdout e stderr alla finestra **Output** quando si esegue senza eseguire il debug con contenitori Windows, quindi i contenitori Windows avviati da Visual Studio con **CTRL** + **F5** non visualizzano i log in questa scheda. Usare invece la finestra **Output.**

## <a name="view-the-filesystem"></a>Visualizzare il file system

Nella scheda **File** è possibile visualizzare il file system del contenitore, inclusa la cartella dell'app che contiene il progetto.

![Screenshot della scheda File nella finestra Contenitori](media/view-and-diagnose-containers/container-filesystem.png)

Per aprire i file in Visual Studio, individuare il file e fare doppio clic su di esso oppure fare clic con il pulsante destro del mouse e scegliere **Apri.** Visual Studio apre i file in modalità di sola lettura.

![Screenshot del file aperto per la visualizzazione in Visual Studio](media/view-and-diagnose-containers/container-file-open.png)

La scheda **File** consente di visualizzare i log applicazioni, ad esempio i log IIS, i file di configurazione e altri file di contenuto nel file system del contenitore.

## <a name="start-stop-and-remove-containers"></a>Avviare, arrestare e rimuovere contenitori

Per impostazione predefinita, **la finestra** Contenitori mostra tutti i contenitori nel computer gestiti da Docker. È possibile usare i pulsanti della barra degli strumenti per avviare, arrestare o rimuovere (eliminare) un contenitore che non si vuole più usare.  Questo elenco viene aggiornato dinamicamente quando i contenitori vengono creati o rimossi.

Per selezionare più contenitori, ad esempio per rimuovere più contenitori contemporaneamente, usare **CTRL+clic.** Se si tenta di avviare più di 10 contenitori, viene richiesto di confermare l'operazione. Se lo si desidera, è possibile disabilitare la richiesta di conferma.

## <a name="open-a-terminal-window-in-a-running-container"></a>Aprire una finestra del terminale in un contenitore in esecuzione

È possibile aprire una finestra del terminale (prompt dei comandi o shell interattiva) nel contenitore usando il pulsante Apri finestra **terminale** nella **finestra Contenitore.**

![Screenshot della finestra Apri terminale nella finestra Contenitori](media/view-and-diagnose-containers/containers-open-terminal-window.png)

Per Windows contenitori, viene aperto Windows prompt dei comandi. Per i contenitori Linux, viene aperta una finestra usando la shell Bash.

![Screenshot della finestra bash](media/view-and-diagnose-containers/container-bash-window.png)

In genere, la finestra del terminale si apre Visual Studio come finestra separata. Se si vuole un ambiente da riga di comando integrato nell'IDE Visual Studio come finestra degli strumenti ancorabile, è possibile installare [W w w più terminale.](https://marketplace.visualstudio.com/items?itemName=DanielGriffen.WhackWhackTerminal)

## <a name="attach-the-debugger-to-a-process"></a>Connettere il debugger a un processo

È possibile collegare il debugger a un processo in  esecuzione nel contenitore usando il pulsante Associa a processo sulla barra degli strumenti della finestra Contenitori. Quando si usa questo pulsante, viene **visualizzata la** finestra di dialogo Associa a processo che mostra i processi disponibili in esecuzione nel contenitore.  

![Screenshot della finestra di dialogo Associa a processo](media/view-and-diagnose-containers/containers-attach-to-process.jpg)

È possibile connettersi ai processi gestiti nel contenitore. Per cercare un processo in un altro contenitore, usare il **pulsante Trova** e selezionare un altro contenitore nella finestra di dialogo **Seleziona contenitore Docker.**

## <a name="viewing-images"></a>Visualizzazione di immagini

È anche possibile visualizzare le immagini nel computer locale usando la **scheda Immagini** nella **finestra Contenitori.** Le immagini estrate da repository esterni vengono raggruppate in una visualizzazione albero.

![Screenshot che mostra la finestra Contenitori che mostra le immagini del contenitore](media/view-and-diagnose-containers/containers-images.png)

La finestra contiene solo le schede applicabili alle immagini: **Etichette** e **Dettagli.** La **scheda Dettagli** mostra i dettagli di configurazione per l'immagine in formato JSON.

![Screenshot che mostra le > nella scheda Dettagli della finestra Contenitori](media/view-and-diagnose-containers/containers-images-details.png)

Per rimuovere un'immagine, fare clic con il pulsante destro del mouse sull'immagine nella visualizzazione albero e scegliere Rimuovi **oppure** selezionare l'immagine e usare il **pulsante** Rimuovi sulla barra degli strumenti.

## <a name="prune-containers-and-images"></a>Eliminare contenitori e immagini

È possibile rimuovere facilmente contenitori e immagini non più in uso usando il pulsante **Elimina** sulla barra **degli strumenti della** finestra Contenitori.

![Screenshot che mostra il pulsante Elimina](media/view-and-diagnose-containers/container-window-prune.png)

Verrà chiesto di confermare che si vogliono rimuovere tutti i contenitori inutilizzati.

Quando la **scheda** Images (Immagini) è selezionata, il **pulsante Prune** (Elimina) chiederà se si vogliono rimuovere tutte le immagini traslate. Le immagini inevase sono immagini di livelli che non sono più associati a un'immagine con tag. La loro rimozione occasionale consente di risparmiare spazio su disco.

## <a name="configuration-options"></a>Opzioni di configurazione

È possibile configurare le finestre di dialogo di conferma per varie attività, ad esempio la rimozione di contenitori e immagini o l'avvio di più di 10 contenitori alla volta. È possibile disabilitare ogni richiesta usando la casella di controllo nella finestra di dialogo. È anche possibile abilitare o disabilitare queste opzioni usando le impostazioni disponibili in Strumenti Opzioni Finestra degli strumenti  >    >    >  **Contenitori di Strumenti contenitori**. Vedere [Configurare gli strumenti contenitore.](container-tools-configure.md)

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sugli strumenti contenitore disponibili in Visual Studio, vedere Panoramica [di Strumenti contenitore.](overview.md)

## <a name="see-also"></a>Vedi anche

[Sviluppo di contenitori in Visual Studio](./index.yml)
