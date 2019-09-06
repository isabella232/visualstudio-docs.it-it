---
title: Esercitazione sugli strumenti Kubernetes | Microsoft Docs
ms.date: 06/08/2018
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.workload:
- azure
ms.openlocfilehash: 45397ddf21f1ea1d735c2753864e5954850a4d98
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/30/2019
ms.locfileid: "70312188"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>Inizia a usare gli strumenti di Visual Studio Kubernetes

Gli strumenti Kubernetes di Visual Studio consentono di semplificare lo sviluppo di applicazioni in contenitori destinate a Kubernetes. Visual Studio può creare automaticamente i file di configurazione come codice necessari per supportare la distribuzione di Kubernetes, ad esempio i grafici Dockerfile e Helm. È possibile eseguire il debug del codice in un cluster Azure Kubernetes Service (AKS) in tempo reale usando Azure Dev Spaces o pubblicare direttamente in un cluster AKS dall'interno di Visual Studio.

Questa esercitazione illustra l'uso di Visual Studio per aggiungere il supporto Kubernetes a un progetto e la pubblicazione in AKS. Se si è interessati principalmente all'uso di [Azure Dev Spaces](https://aka.ms/get-azds) per eseguire il debug e testare il progetto in esecuzione in AKS, è possibile passare all' [esercitazione Azure Dev Spaces](/azure/dev-spaces/get-started-netcore-visualstudio) .

## <a name="prerequisites"></a>Prerequisiti

Per sfruttare questa nuova funzionalità, è necessario:

::: moniker range="vs-2017"
- La versione più recente di [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) con il carico di lavoro di *sviluppo ASP.NET e Web* .
- [Kubernetes Tools per Visual Studio](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes), disponibile come download separato.
::: moniker-end
::: moniker range="vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) con il carico di lavoro di *sviluppo ASP.NET e Web* .
::: moniker-end
- [Docker desktop](https://store.docker.com/editions/community/docker-ce-desktop-windows) installato nella workstation di sviluppo, ovvero in cui si esegue Visual Studio, se si vuole creare immagini Docker, eseguire il debug dei contenitori Docker in esecuzione in locale o pubblicare in AKS. (Docker *non* è necessario per la compilazione e il debug di contenitori Docker in AKS con Azure Dev Spaces).
::: moniker range="vs-2017"
- Se si vuole pubblicare in AKS da Visual Studio (*non* necessario per il debug in aks usando Azure Dev Spaces):

    1. Gli [strumenti di pubblicazione AKS](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes), disponibili come download separati.

    1. Un cluster del servizio Azure Kubernetes. Per altre informazioni, vedere [creazione di un cluster AKS](/azure/aks/kubernetes-walkthrough-portal#create-an-aks-cluster). Assicurarsi di [connettersi al cluster](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster) dalla workstation di sviluppo.

    1. INTERFACCIA della riga di comando di Helm installata nella workstation di sviluppo. Per ulteriori informazioni, vedere [installazione di Helm](https://github.com/kubernetes/helm/blob/master/docs/install.md).

    1. Helm configurato per il cluster AKS tramite il `helm init` comando. Per ulteriori informazioni su come eseguire questa operazione, vedere [How to configure Helm](/azure/aks/kubernetes-helm#configure-helm).
::: moniker-end

## <a name="create-a-new-kubernetes-project"></a>Creare un nuovo progetto Kubernetes

::: moniker range="vs-2017"

Una volta installati gli strumenti appropriati, avviare Visual Studio e creare un nuovo progetto. In **cloud**scegliere l' **applicazione contenitore per** il tipo di progetto Kubernetes. Selezionare questo tipo di progetto e scegliere **OK**.

![Screenshot della creazione di un nuovo progetto di app Kubernetes](media/tutorial-kubernetes-tools/k8s-tools-new-k8s-app.png)

::: moniker-end
::: moniker range=">= vs-2019"

Nella finestra di avvio di Visual Studio cercare *Kubernetes*e scegliere l' **applicazione contenitore per Kubernetes**.

![Screenshot della creazione di un nuovo progetto di app Kubernetes](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app1.png)

Specificare il nome del progetto.

![Screenshot della creazione di un nuovo progetto di app Kubernetes](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app2.png)

::: moniker-end

È quindi possibile scegliere il tipo di ASP.NET Core applicazione Web da creare. Scegliere **Applicazione Web**. La consueta opzione **Abilita supporto Docker** non viene visualizzata in questa finestra di dialogo.  Per impostazione predefinita, il supporto di Docker è abilitato per un'applicazione contenitore per Kubernetes.

::: moniker range="vs-2017"

![Screenshot della selezione dell'app Web](media/tutorial-kubernetes-tools/k8s-tools-web-app-selection-screen.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Screenshot della selezione dell'app Web](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-web-app-selection-screen-2019.png)

::: moniker-end

## <a name="add-kubernetes-support-to-an-existing-project"></a>Aggiungere il supporto Kubernetes a un progetto esistente

In alternativa, è possibile aggiungere il supporto Kubernetes a un progetto di applicazione Web ASP.NET Core esistente. A tale scopo, fare clic con il pulsante destro del mouse sul progetto e scegliere **Aggiungi** > supporto per l'agente di**orchestrazione del contenitore**.

::: moniker range="vs-2017"

![Screenshot della voce di menu dell'agente di orchestrazione del contenitore](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Screenshot della voce di menu dell'agente di orchestrazione del contenitore](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-add-container-orchestrator-2019.png)

::: moniker-end

Nella finestra di dialogo selezionare **Kubernetes/Helm** e scegliere **OK**.

![Screenshot della finestra di dialogo Aggiungi agente di orchestrazione contenitore](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>Cosa crea automaticamente Visual Studio

Dopo la creazione di una nuova **applicazione contenitore per** il progetto Kubernetes o l'aggiunta del supporto per l'agente di orchestrazione del contenitore Kubernetes a un progetto esistente, nel progetto vengono visualizzati alcuni file aggiuntivi che facilitano la distribuzione in Kubernetes.

::: moniker range="vs-2017"

![Screenshot di Esplora soluzioni dopo l'aggiunta del supporto per l'agente di orchestrazione](media/tutorial-kubernetes-tools/k8s-tools-solution-explorer.png)

::: moniker-end
::: moniker range="vs-2019"

![Screenshot di Esplora soluzioni dopo l'aggiunta del supporto per l'agente di orchestrazione](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-solution-explorer-2019.png)

::: moniker-end

I file aggiunti sono:

- un Dockerfile, che consente di generare un'immagine del contenitore Docker che ospita questa applicazione Web. Come si vedrà, gli strumenti di Visual Studio sfruttano questo Dockerfile durante il debug e la distribuzione in Kubernetes. Se si preferisce usare direttamente l'immagine Docker, è possibile fare clic con il pulsante destro del mouse su Dockerfile e scegliere **Compila immagine Docker**.

   ![Screenshot dell'opzione di compilazione dell'immagine Docker](media/tutorial-kubernetes-tools/k8s-tools-build-docker-image.png)

- un grafico Helm e una cartella *Charts* . Questi file YAML costituiscono il grafico Helm per l'applicazione, che può essere usato per distribuirlo in Kubernetes. Per ulteriori informazioni su Helm, vedere [https://www.helm.sh](https://www.helm.sh).

- *azds.yaml*. Contiene le impostazioni per Azure Dev Spaces, che fornisce un'esperienza di debug rapida e iterativa nel servizio Azure Kubernetes. Per ulteriori informazioni, vedere [la documentazione Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces).

::: moniker range="vs-2017"

## <a name="publish-to-azure-kubernetes-service-aks"></a>Pubblicare in Azure Kubernetes Service (AKS)

Con tutti questi file, è possibile usare l'IDE di Visual Studio per scrivere ed eseguire il debug del codice dell'applicazione, così come è sempre. È anche possibile usare [Azure Dev Spaces](https://aka.ms/get-azds) per eseguire rapidamente ed eseguire il debug del codice in esecuzione in un cluster AKS. Per ulteriori informazioni, fare riferimento all' [esercitazione Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/get-started-netcore-visualstudio)

Una volta che il codice è in esecuzione nel modo desiderato, è possibile pubblicare direttamente da Visual Studio in un cluster AKS.

A tale scopo, è prima di tutto necessario verificare di aver installato tutti gli elementi, come descritto nella sezione [prerequisiti](#prerequisites) sotto l'elemento per la pubblicazione in AKS, ed eseguire tutti i passaggi della riga di comando indicati nei collegamenti. Quindi, configurare un profilo di pubblicazione che pubblica l'immagine del contenitore in Azure Container Registry (ACR). Quindi, AKS può effettuare il pull dell'immagine del contenitore da ACR e distribuirla nel cluster.

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul *progetto* e scegliere **pubblica**.

   ![Screenshot della voce di menu pubblica](media/tutorial-kubernetes-tools/k8s-tools-publish-project.png)

2. Nella schermata **pubblica** scegliere **container Registry** come destinazione di pubblicazione e seguire le istruzioni per selezionare il registro contenitori. Se non si ha già un registro contenitori, scegliere **Crea nuovo container Registry di Azure** per crearne uno da Visual Studio. Per altre informazioni, vedere [pubblicare il contenitore in Azure container Registry](vs-azure-tools-docker-hosting-web-apps-in-docker.md).

   ![Screenshot della schermata Seleziona una destinazione di pubblicazione](media/tutorial-kubernetes-tools/k8s-tools-publish-to-acr.png)

3. Tornare in Esplora soluzioni, fare clic con il pulsante destro del mouse sulla *soluzione* e fare clic su **pubblica in Azure AKS**.

   ![Screenshot della voce di menu Publish to Azure AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-solution.png)

4. Scegliere la sottoscrizione e il cluster AKS insieme al profilo di pubblicazione ACR appena creato. Fare quindi clic su **OK**.

   ![Screenshot della schermata Publish to AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-to-aks.png)

   Verrà visualizzata la schermata **Publish to Azure AKS** .

5. Scegliere il collegamento **Configura Helm** per aggiornare la riga di comando usata per installare i grafici Helm nel server.

   ![Screenshot del collegamento di configurazione Helm](media/tutorial-kubernetes-tools/k8s-tools-configure-helm.png)

   L'aggiornamento della riga di comando è utile se sono presenti argomenti della riga di comando personalizzati che si desidera specificare, ad esempio un contesto Kubernetes o un nome di grafico diverso.

   ![Screenshot della schermata di configurazione di Helm](media/tutorial-kubernetes-tools/k8s-tools-helm-configure-screen.png)

6. Quando si è pronti per la distribuzione, fare clic sul pulsante **pubblica** per pubblicare l'applicazione in AKS.

   ![Screenshot della schermata Publish to Azure AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-screen.png)

::: moniker-end

La procedura è stata completata. È ora possibile sfruttare tutte le potenzialità di Visual Studio per lo sviluppo di app Kubernetes.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sullo sviluppo di Kubernetes in Azure, leggere la [documentazione di AKS](/azure/aks).

Per altre informazioni sui Azure Dev Spaces, vedere la [documentazione di Azure Dev Spaces](https://aka.ms/get-azds)
