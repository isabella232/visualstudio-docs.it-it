---
title: Log del contenitore, variabili di ambiente, accesso & filesystem
description: Viene descritto come migliorare la capacità di eseguire il debug e la diagnosi delle app basate su contenitori in Visual Studio usando una finestra degli strumenti per vedere cosa accade all'interno dei contenitori che ospitano l'app.
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 05/06/2019
ms.technology: vs-azure
monikerRange: vs-2019
ms.openlocfilehash: 3fb9a52f990a2e492c63a6e71a7cc2063110c816
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/30/2019
ms.locfileid: "70312169"
---
# <a name="how-to-view-and-diagnose-containers-in-visual-studio"></a>Come visualizzare e diagnosticare i contenitori in Visual Studio

È possibile visualizzare gli elementi in corso all'interno dei contenitori che ospitano l'app usando la finestra **contenitori** . Se si è abituati a usare il prompt dei comandi per eseguire comandi di Docker per visualizzare e diagnosticare ciò che accade nei contenitori, questa finestra offre un modo più pratico per monitorare i contenitori senza uscire dall'IDE di Visual Studio.

> [!NOTE]
> La finestra contenitori è attualmente disponibile come estensione di anteprima che è possibile [scaricare](https://aka.ms/vscontainerspreview) per Visual Studio 2019.

## <a name="prerequisites"></a>Prerequisiti

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- Installare [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
- Installare l' [estensione della finestra contenitori](https://aka.ms/vscontainerspreview)

## <a name="view-information-about-your-containers"></a>Visualizzare le informazioni sui contenitori

La finestra **contenitori** viene visualizzata automaticamente quando si avvia un progetto .NET in contenitori. Per visualizzare i contenitori in Visual Studio in qualsiasi momento, usare **CTRL**+**Q** per attivare la casella di ricerca di Visual Studio e `Containers` digitare e scegliere il primo elemento. È anche possibile aprire la finestra **contenitori** dal menu principale. Usare il percorso dei menu per **visualizzare** > **altri** > **contenitori**di Windows.  

![Screenshot della scheda ambiente nella finestra contenitori](media/view-and-diagnose-containers/container-window.png)

Sul lato sinistro viene visualizzato l'elenco dei contenitori nel computer locale. I contenitori associati alla soluzione vengono visualizzati in **contenitori della soluzione**. A destra viene visualizzato un riquadro con schede per l' **ambiente**, le **porte**, i **log**e **i file**.

> [!TIP]
> È possibile personalizzare facilmente il punto in cui la finestra degli strumenti dei **contenitori** è ancorata in Visual Studio. Vedere [personalizzazione del layout delle finestre in Visual Studio](/visualstudio/ide/customizing-window-layouts-in-visual-studio). Per impostazione predefinita, la finestra **contenitori** è ancorata alla finestra **espressioni di controllo** quando il debugger è in esecuzione.

## <a name="view-environment-variables"></a>Visualizzare le variabili di ambiente

La scheda **Environment (ambiente** ) Visualizza le variabili di ambiente nel contenitore. Per il contenitore dell'app, è possibile impostare queste variabili in molti modi, ad esempio in Dockerfile, in un file con estensione ENV oppure usando l'opzione-e quando si avvia un contenitore con un comando di Docker.

![Screenshot della scheda ambiente nella finestra contenitori](media/view-and-diagnose-containers/container-environment-vars.png)

> [!NOTE]
> Tutte le modifiche apportate alle variabili di ambiente non vengono riflesse in tempo reale. Inoltre, le variabili di ambiente in questa scheda sono le variabili di ambiente di sistema nel contenitore e non riflettono le variabili di ambiente utente locali per l'app.

## <a name="view-port-mappings"></a>Visualizzare i mapping delle porte

Nella scheda **porte** è possibile controllare i mapping delle porte attivi per il contenitore.

![Screenshot della scheda porte nella finestra contenitori](media/view-and-diagnose-containers/container-ports.png)

Le porte note sono collegate, quindi se è disponibile contenuto su una porta, è possibile fare clic sul collegamento per aprire il browser.

## <a name="view-logs"></a>Visualizzare i log

La scheda **logs** Mostra i risultati del `docker logs` comando. Per impostazione predefinita, la scheda Visualizza i flussi stdout e stderr in un contenitore, ma è possibile configurare l'output. Per informazioni dettagliate, vedere la pagina relativa alla [registrazione di Docker](https://docs.docker.com/config/containers/logging/).  Per impostazione predefinita, la scheda **logs** trasmette i log, ma è possibile disabilitarla scegliendo il pulsante **Interrompi** nella scheda.

![Screenshot della scheda log nella finestra contenitori](media/view-and-diagnose-containers/containers-logs.jpg)

Per cancellare i log, usare il pulsante **Cancella** nella scheda **logs** .  Per ottenere tutti i log, usare il pulsante **Aggiorna** .

> [!NOTE]
> Visual Studio reindirizza automaticamente stdout e stderr alla finestra di **output** , quindi i contenitori avviati da Visual Studio, ovvero i contenitori nella sezione contenitori della **soluzione** , non visualizzeranno i log in questa scheda. usare invece la finestra **output** .

## <a name="view-the-filesystem"></a>Visualizzare il file System

Nella scheda **file** è possibile visualizzare il file System del contenitore, inclusa la cartella dell'app che contiene il progetto.

![Screenshot della scheda file nella finestra contenitori](media/view-and-diagnose-containers/container-filesystem.png)

Per aprire i file in Visual Studio, passare al file e fare doppio clic su di esso oppure fare clic con il pulsante destro del mouse e scegliere **Apri**. Visual Studio apre i file in modalità di sola lettura.

![Screenshot del file aperto per la visualizzazione in Visual Studio](media/view-and-diagnose-containers/container-file-open.png)

Usando la scheda **file** è possibile visualizzare i log delle applicazioni, ad esempio i log di IIS, i file di configurazione e altri file di contenuto nel file System del contenitore.

## <a name="start-stop-and-remove-containers"></a>Avviare, arrestare e rimuovere contenitori

Per impostazione predefinita, la finestra **contenitori** Mostra tutti i contenitori nel computer gestito da Docker. È possibile utilizzare i pulsanti della barra degli strumenti per avviare, arrestare o rimuovere (eliminare) un contenitore che non si desidera più.  Questo elenco viene aggiornato dinamicamente durante la creazione o la rimozione di contenitori.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sugli strumenti contenitore disponibili in Visual Studio, vedere [Panoramica degli strumenti](overview.md)per i contenitori.

## <a name="see-also"></a>Vedere anche

[Sviluppo di contenitori in Visual Studio](/visualstudio/containers)

[Marketplace delle estensioni per Visual Studio](https://marketplace.visualstudio.com/)
