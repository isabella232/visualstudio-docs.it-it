---
title: Esercitazione di strumenti di Kubernetes | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2018
ms.technology: vs-ide-deployment
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: douge
ms.workload:
- azure
ms.openlocfilehash: 778ad9112d4133871bd15292847d21af73c3ad86
ms.sourcegitcommit: 12e2f963dac76d53f87569c01198f6d0396d64cf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/12/2018
ms.locfileid: "44701709"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>Introduzione agli strumenti di Visual Studio Kubernetes

Strumenti di Visual Studio Kubernetes consentono di semplificare lo sviluppo di applicazioni in contenitori destinate a Kubernetes. Visual Studio possa creare automaticamente i file di configurazione come codice necessari per supportare la distribuzione di Kubernetes, ad esempio i grafici Helm e Dockerfile. È possibile eseguire il debug del codice in un cluster Azure Kubernetes Service (AKS) in tempo reale usando spazi di sviluppo di Azure oppure pubblicare direttamente in un cluster servizio contenitore di AZURE da Visual Studio.

## <a name="prerequisites"></a>Prerequisiti

Per sfruttare questa nuova funzionalità, è necessario:

- La versione più recente di [Visual Studio 2017](https://visualstudio.microsoft.com/download) con il *sviluppo ASP.NET e web* carico di lavoro.

- Il [Kubernetes tools per Visual Studio](https://aka.ms/get-vsk8stools), disponibile come download separato.

- [Docker per Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows) installati nella workstation di sviluppo (vale a dire, in cui si esegue Visual Studio), se si vuole compilare immagini Docker, eseguire il debug di contenitori Docker in esecuzione in locale o pubblicare in servizio contenitore di AZURE.

- Se si vuole pubblicare in servizio contenitore di AZURE da Visual Studio:

    1.  Il [AKS strumenti di pubblicazione](https://aka.ms/get-vsk8spublish), disponibile come download separato.

    1.  Un cluster Azure Kubernetes Service. Per altre informazioni, vedere [creazione di un cluster AKS](/azure/aks/kubernetes-walkthrough-portal#create-aks-cluster). Assicurarsi di [connettersi al cluster](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster) dalla workstation di sviluppo.

    1.  Helm CLI installata nella workstation di sviluppo. Per altre informazioni, vedere [installazione di Helm](https://github.com/kubernetes/helm/blob/master/docs/install.md).

    1.  Helm configurato per il cluster AKS usando la `helm init` comando. Per altre informazioni su come eseguire questa operazione, vedere [Jak nakonfigurovat Helm](/azure/aks/kubernetes-helm#configure-helm).

## <a name="create-a-new-kubernetes-project"></a>Creare un nuovo progetto di Kubernetes

Dopo aver creato gli strumenti appropriati installati, avviare Visual Studio e creare un nuovo progetto. Sotto **Cloud**, scegliere il **applicazione contenitore per Kubernetes** tipo di progetto. Selezionare questo tipo di progetto e scegliere **OK**.

![Screenshot della creazione di un nuovo progetto di app di Kubernetes](media/k8s-tools-new-k8s-app.png)

È quindi possibile scegliere quale tipo di ASP.NET Core applicazione web da creare. Scegli **applicazione Web** e scegliere **OK**. Le consuete **Abilita supporto Docker** opzione non viene visualizzata in questa finestra di dialogo.  Supporto di docker è abilitato per impostazione predefinita per un'applicazione contenitore per Kubernetes.

![Screenshot della selezione di app web](media/k8s-tools-web-app-selection-screen.png)

## <a name="add-kubernetes-support-to-an-existing-project"></a>Aggiungere il supporto per Kubernetes a un progetto esistente

In alternativa, è possibile aggiungere il supporto per Kubernetes a un progetto di applicazione web ASP.NET Core esistente. A tale scopo, fare doppio clic sul progetto e scegliere **Add** > **supporto dell'agente di orchestrazione dei contenitori**.

![Voce di menu screenshot di Aggiungi agente di orchestrazione contenitore](media/k8s-tools-add-container-orchestrator.png)

Nella finestra di dialogo, selezionare "Kubernetes/Helm" e scegliere **OK**.

![Finestra di dialogo screenshot di Aggiungi agente di orchestrazione contenitore](media/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>Ciò che Visual Studio crea automaticamente

Dopo aver creato un nuovo **applicazione contenitore per Kubernetes** progetto o l'aggiunta di supporto dell'agente di orchestrazione dei contenitori Kubernetes a un progetto esistente, vengono visualizzati alcuni file aggiuntivi nel progetto che semplificano la distribuzione in Kubernetes.

![Screenshot di Esplora soluzioni dopo l'aggiunta del supporto di agente di orchestrazione contenitore](media/k8s-tools-solution-explorer.png)

I file aggiunti sono:

- un file Docker, che consente di generare un comando Docker immagine del contenitore che ospita l'applicazione web. Come si vedrà, gli strumenti di Visual Studio si basa su questo Dockerfile durante il debug e la distribuzione in Kubernetes. Se si preferisce lavorare direttamente con l'immagine Docker, è possibile fare clic su Dockerfile e scegliere **immagine Docker Build**.

   ![Opzione screenshot di compilazione di immagini Docker](media/k8s-tools-build-docker-image.png)

- un grafico Helm e un *grafici* cartella. Questi file yaml costituiscono il grafico Helm per l'applicazione, che è possibile usare per la distribuzione in Kubernetes. Per altre informazioni su Helm, vedere [ https://www.helm.sh ](https://www.helm.sh).

- *azds.yaml*. Contiene le impostazioni per gli spazi di sviluppo di Azure, che offre un'esperienza di debug rapida e iterativa in Azure Kubernetes Service. Per altre informazioni, vedi [la documentazione di Azure Dev spazi](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces).

## <a name="publish-to-azure-kubernetes-service-aks"></a>Pubblicare in Azure Kubernetes Service (AKS)

Con tutti i file in punto, è possibile utilizzare l'IDE di Visual Studio per scrivere ed eseguire il debug di codice dell'applicazione, esattamente come è sempre necessario.

Dopo aver ottenuto il codice in esecuzione nel modo desiderato, è possibile pubblicare direttamente da Visual Studio in un cluster AKS.

A tale scopo, è innanzitutto necessario verificare di aver installato tutti gli elementi come descritto nel [prerequisiti](#prerequisities) sezione sotto l'elemento per la pubblicazione nel servizio contenitore di AZURE ed eseguire tutti i passaggi della riga di comando specificato usando i collegamenti. Quindi, configurare un profilo di pubblicazione che pubblica l'immagine del contenitore per registro contenitori di Azure (ACR). Servizio contenitore di AZURE possono quindi eseguire il pull dell'immagine del contenitore da registro contenitori di AZURE e distribuirla nel cluster.

1. In **Esplora soluzioni**, fare clic sui *project* e scegliere **Publish**.

   ![Schermata di pubblicazione della voce di menu](media/k8s-tools-publish-project.png)

1. Nel **Publish** schermata, scegli **registro contenitori di** come la pubblicazione di destinazione e seguire le istruzioni per selezionare il registro contenitori. Se si ha già un registro contenitori, scegliere **creare di nuovo registro di contenitori di Azure** per crearne uno da Visual Studio. Per altre informazioni, vedere [pubblicare il contenitore in Registro contenitori di Azure](#publish-your-container-to-azure-container-registry).

   ![Screenshot della selezione di una schermata di destinazione di pubblicazione](media/k8s-tools-publish-to-acr.png)

1. In Esplora soluzioni, fare clic sulla *soluzione* e fare clic su **Publish to Azure AKS**.

   ![Schermata di pubblicazione alla voce di menu Azure AKS](media/k8s-tools-publish-solution.png)

1. Scegliere la sottoscrizione e il cluster AKS, con il registro contenitori di AZURE pubblica profilo appena creato. Fare quindi clic su **OK**.

   ![Schermata di pubblicazione alla schermata di servizio contenitore di AZURE](media/k8s-tools-publish-to-aks.png)

   Verrà visualizzata la **Publish to Azure AKS** dello schermo.

1.  Scegliere il **configurare Helm** collega per aggiornare la riga di comando usata per installare i grafici Helm nel server.

   ![Collegamento di screenshot di configurare Helm](media/k8s-tools-configure-helm.png)

   Aggiornamento della riga di comando è utile se sono presenti argomenti della riga di comando personalizzati che si desiderano specificare, ad esempio un diverso nome contesto o un grafico di Kubernetes.

   ![Schermata di configurazione di schermata di Helm](media/k8s-tools-helm-configure-screen.png)

1. Quando si è pronti per distribuire, scegliere il **pubblica** pulsante per pubblicare l'applicazione al servizio contenitore di AZURE.

   ![Screenshot della pubblicazione alla schermata di Azure AKS](media/k8s-tools-publish-screen.png)

La procedura è stata completata. È ora possibile usare tutta la potenza di Visual Studio per lo sviluppo di app Kubernetes.

## <a name="next-steps"></a>Passaggi successivi

Altre informazioni sullo sviluppo in Kubernetes in Azure, vedere la [documentazione di AKS](/azure/aks).
