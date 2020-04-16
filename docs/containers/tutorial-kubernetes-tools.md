---
title: Esercitazione degli strumenti di Kubernetes Documenti Microsoft
ms.date: 06/08/2018
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.workload:
- azure
ms.openlocfilehash: 931f8c2a6d3be130ef78f59f9b3853d28fad8cd4
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444687"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>Introduzione a Visual Studio Kubernetes Tools

Gli strumenti di Visual Studio Kubernetes consentono di semplificare lo sviluppo di applicazioni containerizzate destinate a Kubernetes. Visual Studio è in grado di creare automaticamente i file di configurazione come codice necessari per supportare la distribuzione di Kubernetes, ad esempio Dockerfiles e Helm charts. È possibile eseguire il debug del codice in un cluster di Azure Kubernetes Service (AKS) attivo usando Azure Dev Spaces o pubblicare direttamente in un cluster AKS dall'interno di Visual Studio.You can debug your code in a live Azure Kubernetes Service (AKS) cluster using Azure Dev Spaces, or publish directly to an AKS cluster from inside Visual Studio.

Questa esercitazione illustra l'uso di Visual Studio per aggiungere il supporto Kubernetes a un progetto e pubblicare in AKS.This tutorial covers using Visual Studio to add Kubernetes support to an project and publish to AKS. Se si è interessati principalmente all'uso di Azure Dev Spaces per eseguire il debug e testare il progetto in esecuzione in AKS, è possibile passare all'esercitazione di Azure Dev Spaces.If you are primarily interested in using [Azure Dev Spaces](/azure/dev-spaces/) to debug and test your project running in AKS, you can jump to the [Azure Dev Spaces tutorial](/azure/dev-spaces/get-started-netcore-visualstudio) instead.

## <a name="prerequisites"></a>Prerequisiti

Per sfruttare questa nuova funzionalità, è necessario:To leverage this new functionality, you'll need:

::: moniker range="vs-2017"
- La versione più recente di [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) con il carico di lavoro *di sviluppo Web e di ASP.NET.*
- Gli [strumenti Kubernetes per Visual Studio](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes), disponibili come download separato.
::: moniker-end
::: moniker range="vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) con il carico di lavoro *Sviluppo ASP.NET e Web*.
::: moniker-end
- [Docker Desktop](https://store.docker.com/editions/community/docker-ce-desktop-windows) installato nella workstation di sviluppo (ovvero, dove si esegue Visual Studio), se si desidera creare immagini Docker, eseguire il debug di contenitori Docker in esecuzione in locale o pubblicare in AKS. (Docker *non* è necessario per la compilazione e il debug di contenitori Docker in AKS utilizzando Azure Dev Spaces.)
::: moniker range="vs-2017"
- Se si desidera pubblicare in AKS da Visual Studio *(non* necessario per il debug in AKS usando Azure Dev Spaces):

    1. Gli strumenti di [pubblicazione AKS](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes), disponibili come download separato.

    1. Un cluster del servizio Azure Kubernetes. Per ulteriori informazioni, vedere [Creazione di un cluster AKS](/azure/aks/kubernetes-walkthrough-portal#create-an-aks-cluster). Assicurarsi di [connettersi al cluster](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster) dalla workstation di sviluppo.

    1. Helm CLI installato sulla workstation di sviluppo. Per ulteriori informazioni, consultate [Installazione di Helm.](https://github.com/helm/helm-www/blob/master/content/en/docs/helm/helm_install.md)

    1. Helm configurato sul cluster AKS `helm init` utilizzando il comando. Per ulteriori informazioni su come eseguire questa operazione, vedere [Come configurare Helm](/azure/aks/kubernetes-helm#configure-helm).
::: moniker-end

## <a name="create-a-new-kubernetes-project"></a>Creare un nuovo progetto Kubernetes

::: moniker range="vs-2017"

Dopo aver installato gli strumenti appropriati, avviare Visual Studio e creare un nuovo progetto. In **Cloud**scegliere il tipo di progetto **Applicazione contenitore per Kubernetes.** Selezionare questo tipo di progetto e scegliere **OK**.

![Screenshot della creazione di un nuovo progetto di app Kubernetes](media/tutorial-kubernetes-tools/k8s-tools-new-k8s-app.png)

::: moniker-end
::: moniker range=">= vs-2019"

Nella finestra di avvio di Visual Studio cercare *Kubernetes*e scegliere **l'applicazione Contenitore per Kubernetes**.

![Screenshot della creazione di un nuovo progetto di app Kubernetes](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app1.png)

Specificare il nome del progetto.

![Screenshot della creazione di un nuovo progetto di app Kubernetes](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app2.png)

::: moniker-end

È quindi possibile scegliere il tipo di ASP.NETapplicazione Web Core da creare. Scegliere **Applicazione Web**. La solita opzione **Abilita supporto Docker** non viene visualizzata in questa finestra di dialogo.  Docker support is enabled by default for a container application for Kubernetes.

::: moniker range="vs-2017"

![Screenshot della selezione dell'app Web](media/tutorial-kubernetes-tools/k8s-tools-web-app-selection-screen.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Screenshot della selezione dell'app Web](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-web-app-selection-screen-2019.png)

::: moniker-end

## <a name="add-kubernetes-support-to-an-existing-project"></a>Aggiungere il supporto Kubernetes a un progetto esistente

In alternativa, è possibile aggiungere il supporto Kubernetes a un progetto di applicazione Web ASP.NET Core esistente. A tale scopo, fare clic con il pulsante destro del mouse sul progetto e scegliere **Aggiungi** > **supporto orchestratore contenitore**.

::: moniker range="vs-2017"

![Schermata della voce di menu Aggiungi orchestratore contenitore](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Schermata della voce di menu Aggiungi orchestratore contenitore](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-add-container-orchestrator-2019.png)

::: moniker-end

Nella finestra di dialogo, selezionare **Kubernetes/Helm** e scegliere **OK**.

![Screenshot della finestra di dialogo Aggiungi orchestratore contenitori](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>Cosa crea Visual Studio automaticamente

Dopo aver creato una nuova **applicazione contenitore per Kubernetes** progetto o l'aggiunta di Kubernetes supporto dell'orchestratore contenitore a un progetto esistente, vengono visualizzati alcuni file aggiuntivi nel progetto che facilitano la distribuzione in Kubernetes.

::: moniker range="vs-2017"

![Screenshot di Esplora soluzioni dopo l'aggiunta del supporto di Container Orchestrator](media/tutorial-kubernetes-tools/k8s-tools-solution-explorer.png)

::: moniker-end
::: moniker range="vs-2019"

![Screenshot di Esplora soluzioni dopo l'aggiunta del supporto di Container Orchestrator](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-solution-explorer-2019.png)

::: moniker-end

I file aggiunti sono:

- oggetto Dockerfile, che consente di generare un'immagine contenitore Docker che ospita questa applicazione Web. Come si vedrà, gli strumenti di Visual Studio sfrutta questo Dockerfile durante il debug e la distribuzione a Kubernetes. Se si preferisce lavorare direttamente con l'immagine Docker, è possibile fare clic con il pulsante destro del mouse sul file Docker e scegliere **Crea immagine Docker**.

   ![Screenshot dell'opzione Crea immagine docker](media/tutorial-kubernetes-tools/k8s-tools-build-docker-image.png)

- un grafico Helm e una cartella *di grafici.* Questi file yaml costituiscono il grafico Helm per l'applicazione, che è possibile utilizzare per distribuirlo a Kubernetes. Per ulteriori informazioni su [https://www.helm.sh](https://www.helm.sh)Helm, vedere .

- *azds.yaml*. Contiene le impostazioni per Azure Dev Spaces, che offre un'esperienza di debug rapida e iterativa nel servizio Azure Kubernetes.This contains settings for Azure Dev Spaces, which provides a rapid, iterative debugging experience in Azure Kubernetes Service. Per altre informazioni, vedere [la documentazione](/azure/dev-spaces/azure-dev-spaces)relativa agli spazi di sviluppo di Azure .For more information, see the Azure Dev Spaces documentation .

::: moniker range="vs-2017"

## <a name="publish-to-azure-kubernetes-service-aks"></a>Pubblicare nel servizio Azure Kubernetes (AKS)Publish to Azure Kubernetes Service (AKS)

Con tutti questi file sul posto, è possibile utilizzare l'IDE di Visual Studio per scrivere ed eseguire il debug del codice dell'applicazione, proprio come si ha sempre fatto. È anche possibile usare [Spazi di sviluppo di Azure](/azure/dev-spaces/) per eseguire rapidamente ed eseguire il debug del codice in esecuzione in un cluster AKS. Per altre informazioni, fare riferimento all'esercitazione sugli [spazi di sviluppo di AzureFor](/azure/dev-spaces/get-started-netcore-visualstudio) more information, please reference the Azure Dev Spaces tutorial

Dopo aver eseguito il codice nel modo desiderato, è possibile pubblicare direttamente da Visual Studio in un cluster AKS.

A tale scopo, è innanzitutto necessario verificare di aver installato tutti gli elementi descritti nella sezione [Prerequisiti](#prerequisites) sotto l'elemento per la pubblicazione in AKS ed eseguire tutti i passaggi della riga di comando forniti nei collegamenti. Impostare quindi un profilo di pubblicazione che pubblica l'immagine del contenitore in Azure Container Registry (ACR). AKS può quindi estrarre l'immagine del contenitore da ACR e distribuirla nel cluster.

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul *progetto* e **scegliere Pubblica**.

   ![Schermata della voce di menu Pubblica](media/tutorial-kubernetes-tools/k8s-tools-publish-project.png)

2. Nella schermata **Pubblica** scegliere **Registro di** sistema contenitore come destinazione di pubblicazione e seguire le istruzioni visualizzate per selezionare il Registro di sistema del contenitore. Se non si dispone già di un registro contenitori, scegliere **Crea nuovo registro contenitori** di Azure per crearne uno da Visual Studio.If you don't already have a container registry, choose Create New Azure Container Registry to create one from Visual Studio. Per altre informazioni, vedere [Pubblicare il contenitore](hosting-web-apps-in-docker.md)nel Registro di sistema del contenitore di Azure.For more information, see Publish your container to Azure Container Registry.

   ![Screenshot della schermata Di selezione di una destinazione di pubblicazione](media/tutorial-kubernetes-tools/k8s-tools-publish-to-acr.png)

3. In Esplora soluzioni fare clic con il pulsante destro del mouse sulla *soluzione* e **scegliere Pubblica in Azure AKS**.

   ![Screenshot della voce di menu Pubblica in Azure AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-solution.png)

4. Scegliere l'abbonamento e il cluster AKS, insieme al profilo di pubblicazione ACR appena creato. Fare quindi clic su **OK**.

   ![Screenshot della schermata Pubblica in AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-to-aks.png)

   Verrà visualizzata la schermata **Pubblica in Azure AKS.**

5. Scegliere il collegamento **Configura Helm** per aggiornare la riga di comando utilizzata per installare i grafici Helm nel server.

   ![Screenshot del collegamento Configura Elmo](media/tutorial-kubernetes-tools/k8s-tools-configure-helm.png)

   L'aggiornamento della riga di comando è utile se sono presenti argomenti della riga di comando personalizzati che si desidera specificare, ad esempio un contesto Kubernetes diverso o il nome del grafico.

   ![Schermata della schermata di configurazione di Helm](media/tutorial-kubernetes-tools/k8s-tools-helm-configure-screen.png)

6. Quando si è pronti per la distribuzione, fare clic sul pulsante **Pubblica** per pubblicare l'applicazione in AKS.

   ![Screenshot della schermata Pubblica in Azure AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-screen.png)

::: moniker-end

Congratulazioni! È ora possibile usare tutta la potenza di Visual Studio per tutto lo sviluppo di app Kubernetes.You can now use the full power of Visual Studio for all your Kubernetes app development.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sullo sviluppo di Kubernetes in Azure, leggere la documentazione di [AKS](/azure/aks).

Per altre informazioni sugli spazi di sviluppo di Azure, leggere la [documentazione di Azure Dev SpacesLearn](/azure/dev-spaces/) more about Azure Dev Spaces by reading the Azure Dev Spaces documentation
