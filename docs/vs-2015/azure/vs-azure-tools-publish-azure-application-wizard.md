---
title: Con Visual Studio pubblicazione guidata applicazione di Azure | Microsoft Docs
description: Informazioni su come configurare le varie impostazioni in Visual Studio la pubblicazione guidata di Azure dell'applicazione
author: ghogen
manager: douge
assetId: 7d8f1ac9-e439-47e0-a183-0642c4ea1920
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: c9c4104d4d07cab7486038a8787ed0c7759abd60
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002970"
---
# <a name="using-the-visual-studio-publish-azure-application-wizard"></a>Uso della procedura guidata di Visual Studio Pubblica applicazione Azure

Dopo aver sviluppato un'applicazione web in Visual Studio, è possibile pubblicare in un servizio cloud di Azure usando il **pubblica applicazione Azure** procedura guidata.

> [!Note]
> Questo articolo riguarda la distribuzione in servizi cloud, non in siti web. Per informazioni sulla distribuzione in siti web, vedere [come distribuire un sito Web Azure](https://social.msdn.microsoft.com/Search/windowsazure?query=How%20to%20Deploy%20an%20Azure%20Web%20Site&Refinement=138&ac=4#refinementChanges=117&pageNumber=1&showMore=false).

## <a name="accessing-the-publish-azure-application-wizard"></a>Accesso alla procedura guidata pubblica l'applicazione Azure

È possibile accedere la procedura guidata pubblica l'applicazione Azure in due modi a seconda del tipo di progetto di Visual Studio che è necessario.

**Se si dispone di un progetto di servizio cloud di Azure:**

1. Creare o aprire un progetto di servizio cloud di Azure in Visual Studio.

1. Nelle **Esplora soluzioni**, fare clic sul progetto e, dal menu di scelta rapida, selezionare **Publish**.

**Se si dispone di un progetto di applicazione web che non è abilitato per Azure:**

1. Creare o aprire un progetto di servizio cloud di Azure in Visual Studio.

1. Nelle **Esplora soluzioni**, fare clic sul progetto e, dal menu di scelta rapida, selezionare **convertire** > **Converti in progetto servizio Cloud Azure**. 

1. Nelle **Esplora soluzioni**, fare doppio clic su progetto Azure appena creato e, dal menu di scelta rapida, selezionare **Publish**.

## <a name="sign-in-page"></a>Nella pagina di accesso

![Nella pagina di accesso](./media/vs-azure-tools-publish-azure-application-wizard/sign-in.png)

**Account** : selezionare un account o selezionarne **aggiungere un account** nell'elenco a discesa degli account.

**Scegliere la sottoscrizione** -scegliere la sottoscrizione da usare per la distribuzione.

## <a name="settings-page---common-settings-tab"></a>Pagina Impostazioni - scheda delle impostazioni comuni

![Impostazioni comuni](./media/vs-azure-tools-publish-azure-application-wizard/settings-common-settings.png)

**Servizio cloud** -Usa l'elenco a discesa, selezionare un cloud esistente, oppure selezionare  **&lt;Crea nuovo >** e creare un servizio cloud. Il data center viene visualizzato tra parentesi per ogni servizio cloud. È consigliabile che la posizione del data center per il servizio cloud corrispondere alla posizione del data center dell'account di archiviazione (impostazioni avanzate).

**Ambiente** -selezionare il **produzione** oppure **Staging**. Se si desidera distribuire l'applicazione in un ambiente di test, scegliere l'ambiente di gestione temporanea. 

**Configurazione della build** -selezionare il **Debug** oppure **versione**.

**Configurazione del servizio** -selezionare il **Cloud** oppure **locale**.

**Abilitare Desktop remoto per tutti i ruoli** -selezionare questa opzione se si desidera essere in grado di connettersi in modalità remota al servizio. Questa opzione viene utilizzata principalmente per la risoluzione dei problemi. Per altre informazioni, vedere [abilitare connessione Desktop remoto per un ruolo nei servizi Cloud di Azure con Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

**Abilita distribuzione Web per tutti i ruoli web** -selezionare questa opzione per abilitare distribuzione web per il servizio. È necessario selezionare anche il **Abilita Desktop remoto per tutti i ruoli** possibilità di usare questa funzionalità. Per altre informazioni, vedere [pubblicazione di un servizio cloud con Visual Studio](vs-azure-tools-publishing-a-cloud-service.md).

## <a name="settings-page---advanced-settings-tab"></a>Pagina Impostazioni - scheda Impostazioni avanzata

![Impostazioni avanzate](./media/vs-azure-tools-publish-azure-application-wizard/settings-advanced-settings.png)

**Etichetta distribuzione** -accettare il nome predefinito oppure immettere un nome a scelta. Per aggiungere la data all'etichetta di distribuzione, lasciare selezionata la casella di controllo. 

**Account di archiviazione** -selezionare l'account di archiviazione da usare per questa distribuzione, * *&lt;Crea nuovo > per creare un account di archiviazione. Il data center viene visualizzato tra parentesi per ogni account di archiviazione. È consigliabile che la posizione del data center dell'account di archiviazione è quello utilizzato per la posizione del data center per il servizio cloud (impostazioni comuni).

L'account di archiviazione di Azure archivia il pacchetto per la distribuzione dell'applicazione. Dopo l'applicazione viene distribuita, il pacchetto viene rimosso dall'account di archiviazione.

**Elimina distribuzione in caso di errore** -selezionare questa opzione per eliminare la distribuzione se si verificano errori durante la pubblicazione. Deve essere deselezionata se si vuole mantenere un indirizzo IP virtuale costante per il servizio cloud.

**Aggiornamento distribuzione** -selezionare questa opzione se si desidera distribuire solo componenti aggiornati. Questo tipo di distribuzione può essere più veloce di una distribuzione completa. Ciò è necessario verificare se si vuole mantenere un indirizzo IP virtuale costante per il servizio cloud. 

**Impostazioni aggiornamento distribuzione** -questa finestra di dialogo viene utilizzata per specificare ulteriormente come aggiornare i ruoli. Se si sceglie **aggiornamento incrementale**, le istanze dell'applicazione vengono aggiornate una dopo l'altra, in modo che l'applicazione sia sempre disponibile. Se si sceglie **aggiornamento simultaneo**, tutte le istanze dell'applicazione vengono aggiornate contemporaneamente. L'aggiornamento simultaneo è più veloce, ma il servizio potrebbe non essere disponibile durante il processo di aggiornamento.

![Impostazioni di distribuzione](./media/vs-azure-tools-publish-azure-application-wizard/deployment-settings.png)

**Abilita IntelliTrace** -specificare se si vuole abilitare IntelliTrace. Con IntelliTrace, è possibile registrare informazioni di debug approfondite per un'istanza del ruolo quando è in esecuzione in Azure. Se è necessario individuare la causa di un problema, è possibile utilizzare i log di IntelliTrace per esaminare il codice da Visual Studio come se fosse in esecuzione in Azure. Per altre informazioni sull'uso di IntelliTrace, vedere [debug di un servizio cloud di Azure pubblicato con Visual Studio e IntelliTrace](./vs-azure-tools-intellitrace-debug-published-cloud-services.md).

**Abilitare la profilatura** -specificare se si desidera abilitare la profilatura delle prestazioni. Il profiler di Visual Studio consente di ottenere un'analisi approfondita degli aspetti computazionali dell'esecuzione del servizio cloud. Per altre informazioni sull'uso di profiler di Visual Studio, vedere [testare le prestazioni di un servizio cloud di Azure](./vs-azure-tools-performance-profiling-cloud-services.md).

**Abilita debug remoto per tutti i ruoli** -specificare se si desidera abilitare il debug remoto. Per altre informazioni sul debug dei servizi cloud con Visual Studio, vedere [debug di un servizio cloud di Azure o una macchina virtuale in Visual Studio](./vs-azure-tools-debug-cloud-services-virtual-machines.md).

## <a name="diagnostics-settings-page"></a>Pagina Impostazioni di diagnostica

![Impostazioni di diagnostica](./media/vs-azure-tools-publish-azure-application-wizard/diagnostic-settings.png)

È possibile utilizzare diagnostica risolvere i problemi di un servizio cloud di Azure (o macchina virtuale di Azure). Per informazioni sulla diagnostica, vedere [configurazione della diagnostica per servizi Cloud di Azure e macchine virtuali](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Per informazioni su Application Insights, vedere [What ' s Application Insights?](/azure/application-insights/app-insights-overview.md).

## <a name="summary-page"></a>Pagina di riepilogo

![Riepilogo](./media/vs-azure-tools-publish-azure-application-wizard/summary.png)

**Profilo di destinazione** -è possibile scegliere di creare un profilo di pubblicazione dalle impostazioni scelte. Ad esempio, si potrebbe creare un profilo per un ambiente di test e per la produzione. Per salvare questo profilo, scegliere il **salvare** icona. La procedura guidata crea il profilo e viene salvato nel progetto di Visual Studio. Per modificare il nome del profilo, aprire il **profilo di destinazione** elenco e quindi scegliere  **&lt;Gestisci... &gt;**.

   > [!Note]
   > Il profilo di pubblicazione viene visualizzato in Esplora soluzioni in Visual Studio e le impostazioni del profilo vengono scritte in un file con estensione azurepubxml. Le impostazioni vengono salvate come attributi di tag XML.

## <a name="publishing-your-application"></a>Pubblicazione dell'applicazione

Dopo aver configurato tutte le impostazioni per la distribuzione del progetto, selezionare **pubblica** nella parte inferiore della finestra di dialogo. È possibile monitorare lo stato del processo nel **Output** finestra in Visual Studio.

## <a name="next-steps"></a>Passaggi successivi

- [Eseguire la migrazione e pubblicare un'applicazione Web a un servizio cloud di Azure da Visual Studio](./vs-azure-tools-migrate-publish-web-app-to-cloud-service.md)

- [Informazioni su come usare Visual Studio per pubblicare un servizio cloud di Azure](./vs-azure-tools-publishing-a-cloud-service.md)

- [Debug di un servizio cloud di Azure pubblicato con IntelliTrace e Visual Studio](./vs-azure-tools-intellitrace-debug-published-cloud-services.md)

- [Test delle prestazioni di un servizio cloud di Azure](./vs-azure-tools-performance-profiling-cloud-services.md)

- [Configurazione della diagnostica per servizi Cloud di Azure e macchine virtuali](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md).

- [Che cos'è Application Insights?](/azure/application-insights/app-insights-overview.md)