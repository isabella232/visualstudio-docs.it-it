---
title: Usare Bridge per Kubernetes con Visual Studio
titleSuffix: ''
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: how-to
description: Informazioni su come usare Bridge per Kubernetes con Visual Studio per connettere il computer di sviluppo a un cluster Kubernetes
keywords: Bridge per Kubernetes, Azure Dev Spaces, spazi di sviluppo, Docker, Kubernetes, Azure, contenitori
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jillfra
ms.openlocfilehash: c7d046ca63af5aa65f5cd286e9a6199afc6c2947
ms.sourcegitcommit: f9179a3a6d74fbd871f62b72491e70b9e7b05637
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/21/2020
ms.locfileid: "90845869"
---
# <a name="use-bridge-to-kubernetes"></a>Usare Bridge per Kubernetes

È possibile usare Bridge per Kubernetes per reindirizzare il traffico tra il cluster Kubernetes e il codice in esecuzione nel computer di sviluppo. Questa guida fornisce anche uno script per la distribuzione di un'applicazione di esempio di grandi dimensioni con più microservizi in un cluster Kubernetes.

## <a name="before-you-begin"></a>Prima di iniziare

Questa guida usa l' [applicazione di esempio bike sharing][bike-sharing-github] per dimostrare la connessione del computer di sviluppo a un cluster Kubernetes. Se si dispone già di un'applicazione in esecuzione in un cluster Kubernetes, è comunque possibile seguire la procedura seguente e usare i nomi dei propri servizi.

### <a name="prerequisites"></a>Prerequisiti

* Una sottoscrizione di Azure. Se non si ha una sottoscrizione di Azure, è possibile creare un [account gratuito](https://azure.microsoft.com/free).
* [L'interfaccia della riga di comando di Azure installata][azure-cli].
* [Visual Studio 2019][visual-studio] versione 16,7 Preview 4 o successiva in esecuzione in Windows 10 con il carico di lavoro *sviluppo di Azure* installato.
* [Estensione Bridge to Kubernetes installata][btk-extension].

Inoltre, per le applicazioni console .NET, installare il pacchetto NuGet *Microsoft. VisualStudio. Azure. Kubernetes. Tools. targets* .

## <a name="create-a-kubernetes-cluster"></a>Creare un cluster Kubernetes

Creare un cluster AKS in un' [area supportata][supported-regions]. I comandi seguenti creano un gruppo di risorse denominato *MyResourceGroup* e un cluster del servizio Azure Kubernetes denominato *MyAKS*.

```azurecli-interactive
az group create \
    --name MyResourceGroup \
    --location eastus

az aks create \
    --resource-group MyResourceGroup \
    --name MyAKS \
    --location eastus \
    --node-count 3 \
    --generate-ssh-keys
```

## <a name="install-the-sample-application"></a>Installare l'applicazione di esempio

Installare l'applicazione di esempio nel cluster usando lo script fornito. È possibile eseguire questo script usando il [Azure cloud Shell][azure-cloud-shell].

```azurecli-interactive
git clone https://github.com/Microsoft/mindaro
cd mindaro
chmod +x ./bridge-quickstart.sh
./bridge-quickstart.sh -g MyResourceGroup -n MyAKS
```

Passare all'applicazione di esempio che esegue il cluster aprendo il relativo URL pubblico, che viene visualizzato nell'output dello script di installazione.

```console
$ ./bridge-quickstart.sh -g MyResourceGroup -n MyAKS
Defaulting Dev spaces repository root to current directory : ~/mindaro
Setting the Kube context
...
To try out the app, open the url:
bikeapp.bikesharingweb.EXTERNAL_IP.nip.io
```

Nell'esempio precedente l'URL pubblico è `bikeapp.bikesharingweb.EXTERNAL_IP.nip.io` .

## <a name="connect-to-your-cluster-and-debug-a-service"></a>Connettersi al cluster ed eseguire il debug di un servizio

Nel computer di sviluppo scaricare e configurare l'interfaccia della riga di comando di Kubernetes per connettersi al cluster Kubernetes usando [AZ AKS Get-credentials][az-aks-get-credentials].

```azurecli
az aks get-credentials --resource-group MyResourceGroup --name MyAKS
```

Dal repository [dell'applicazione di esempio bike sharing][bike-sharing-github] in GitHub, usare l'elenco a discesa del pulsante **codice** verde e scegliere **Apri in Visual Studio** per clonare il repository in locale e aprire la cartella in Visual Studio. Quindi, usare **file**  >  **Apri progetto** per aprire il progetto **app. csproj** nella cartella *Samples/BikeSharingApp/ReservationEngine* .

Nel progetto selezionare **Bridge to Kubernetes** dall'elenco a discesa delle impostazioni di avvio, come illustrato di seguito.

![Scegliere Bridge to Kubernetes](media/bridge-to-kubernetes/choose-bridge-to-kubernetes.png)

Fare clic sul pulsante Start accanto a *Bridge to Kubernetes*. Nella finestra di dialogo **Crea profilo per Bridge to Kubernetes** :

* Selezionare la propria sottoscrizione.
* Selezionare *MyAKS* per il cluster.
* Selezionare *bikeapp* per lo spazio dei nomi.
* Selezionare *reservationengine* per il servizio da reindirizzare.
* Selezionare *app* per il profilo di avvio.
* Selezionare `http://bikeapp.bikesharingweb.EXTERNAL_IP.nip.io` l'URL per avviare il browser.

![Scegliere il Bridge per il cluster Kubernetes](media/bridge-to-kubernetes/choose-bridge-cluster2.png)

> [!IMPORTANT]
> È possibile reindirizzare solo i servizi che dispongono di un singolo POD.

Scegliere se eseguire o meno l'isolamento, vale a dire che altri utenti che usano il cluster non saranno interessati dalle modifiche apportate. Questa modalità di isolamento viene eseguita tramite il routing delle richieste alla copia di ogni servizio interessato, ma il routing di tutto il traffico in modo normale. Per ulteriori informazioni su come eseguire questa operazione, vedere la pagina relativa alla [modalità di funzionamento di Bridge to Kubernetes][btk-overview-routing].

Fare clic su **Salva e avviare il debug**.

Tutto il traffico nel cluster Kubernetes viene reindirizzato per il servizio *reservationengine* alla versione dell'applicazione in esecuzione nel computer di sviluppo. Bridge to Kubernetes instrada anche tutto il traffico in uscita dall'applicazione al cluster Kubernetes.

> [!NOTE]
> Verrà richiesto di consentire l'esecuzione di *EndpointManager* con privilegi elevati e di modificare il file degli host.

Il computer di sviluppo è connesso quando la barra di stato indica che si è connessi al `reservationengine` servizio.

![Computer di sviluppo connesso](media/bridge-to-kubernetes/development-computer-connected.png)

> [!NOTE]
> All'avvio successivo non verrà visualizzata la finestra di dialogo **Crea profilo per Bridge per Kubernetes** . Le impostazioni vengono aggiornate in **debug** nelle proprietà del progetto.

Quando il computer di sviluppo è connesso, il traffico inizia a reindirizzare al computer di sviluppo per il servizio che si sta sostituendo.

## <a name="set-a-break-point"></a>Imposta un punto di rottura

Aprire [BikesHelper.cs][bikeshelper-cs-breakpoint] e fare clic in un punto qualsiasi della riga 26 per posizionare il cursore. Per impostare un punto di interruzione, premere *F9* o selezionare **debug**  >  **Imposta/Rimuovi**punto di interruzione.

Passare all'applicazione di esempio aprendo l'URL pubblico. Selezionare **Aurelia Briggs (Customer)** come utente, quindi selezionare una bicicletta da affittare. Scegliere **Rent Bike**. Tornare a Visual Studio e osservare che la riga 26 è evidenziata. Il punto di interruzione impostato ha sospeso il servizio alla riga 26. Per riprendere il servizio, premere **F5** o fare clic su **debug**  >  **continua**. Tornare al browser e verificare che la pagina indichi che la bicicletta è stata affittata.

Rimuovere il punto di interruzione inserendo il cursore sulla riga 26 in `BikesHelper.cs` e premendo **F9**.

> [!NOTE]
> Per impostazione predefinita, l'arresto dell'attività di debug disconnette anche il computer di sviluppo dal cluster Kubernetes. È possibile modificare questo comportamento modificando **Disconnetti dopo** il debug `false` nella sezione **strumenti** di debug di Kubernetes delle opzioni di debug. Dopo aver aggiornato questa impostazione, il computer di sviluppo rimarrà connesso quando si arresta e si avvia il debug. Per disconnettere il computer di sviluppo dal cluster, fare clic sul pulsante **Disconnetti** sulla barra degli strumenti.

## <a name="additional-configuration"></a>Configurazione aggiuntiva

Bridge to Kubernetes è in grado di gestire il routing del traffico e di replicare le variabili di ambiente senza alcuna configurazione aggiuntiva. Se è necessario scaricare i file montati nel contenitore del cluster Kubernetes, ad esempio un file ConfigMap, è possibile creare un per scaricare i file nel `KubernetesLocalProcessConfig.yaml` computer di sviluppo. Per ulteriori informazioni, vedere [utilizzo di KubernetesLocalProcessConfig. YAML per la configurazione aggiuntiva con per Bridge in Kubernetes][kubernetesLocalProcessConfig-yaml].

## <a name="using-logging-and-diagnostics"></a>Uso della registrazione e della diagnostica

È possibile trovare i log di diagnostica in `Bridge to Kubernetes` directory nella directory *temporanea* del computer di sviluppo. 

## <a name="remove-the-sample-application-from-your-cluster"></a>Rimuovere l'applicazione di esempio dal cluster

Usare lo script fornito per rimuovere l'applicazione di esempio dal cluster.

```azurecli-interactive
./bridge-quickstart.sh -c -g MyResourceGroup -n MyAKS
```

## <a name="next-steps"></a>Passaggi successivi

Informazioni sul funzionamento del Bridge per Kubernetes.

> [!div class="nextstepaction"]
> [Funzionamento del Bridge per Kubernetes](overview-bridge-to-kubernetes.md)

[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-vs-code]: https://marketplace.visualstudio.com/items?itemName=azuredevspaces.azds
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-lates&preserve-view=true
[azure-cloud-shell]: /azure/cloud-shell/w.md
[az-aks-get-credentials]: /cli/azure/aks?view=azure-cli-latest&preserve-view=true#az-aks-get-credentials
[az-aks-vs-code]: https://marketplace.visualstudio.com/items?itemName=ms-kubernetes-tools.vscode-aks-tools
[bike-sharing-github]: https://github.com/Microsoft/mindaro
[preview-terms]: https://azure.microsoft.com/support/legal/preview-supplemental-terms/
[bikeshelper-cs-breakpoint]: https://github.com/Microsoft/mindaro/blob/master/samples/BikeSharingApp/ReservationEngine/BikesHelper.cs#L26
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-bridge-to-kubernetes.md
[btk-overview-routing]: overview-bridge-to-kubernetes.md#using-routing-capabilities-for-developing-in-isolation