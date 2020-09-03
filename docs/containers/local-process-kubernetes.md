---
title: Usare il processo locale con Kubernetes con Visual Studio (anteprima)
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: how-to
description: Informazioni su come usare il processo locale con Kubernetes con Visual Studio per connettere il computer di sviluppo a un cluster Kubernetes
keywords: Processo locale con Kubernetes, Azure Dev Spaces, spazi di sviluppo, Docker, Kubernetes, Azure, contenitori
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jillfra
ms.openlocfilehash: 191fd1df377bd15d78c329b88d20f1fed8669663
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "87913280"
---
# <a name="use-local-process-with-kubernetes-preview"></a>Usare il processo locale con Kubernetes (anteprima)

Il processo locale con Kubernetes consente di eseguire ed eseguire il debug del codice nel computer di sviluppo, mentre è ancora connesso al cluster Kubernetes con il resto dell'applicazione o dei servizi. Ad esempio, se si dispone di un'architettura di microservizi di grandi dimensioni con molti servizi e database interdipendenti, la replica di tali dipendenze nel computer di sviluppo può essere difficile. Inoltre, la compilazione e la distribuzione di codice nel cluster Kubernetes per ogni modifica del codice durante lo sviluppo a ciclo interno possono essere lenti, dispendiose in termini di tempo e difficili da usare con un debugger.

Il processo locale con Kubernetes evita di dover compilare e distribuire il codice nel cluster creando invece una connessione direttamente tra il computer di sviluppo e il cluster. Connettendo il computer di sviluppo al cluster durante il debug è possibile testare e sviluppare rapidamente il servizio nel contesto dell'applicazione completa senza creare una configurazione Docker o Kubernetes.

Il processo locale con Kubernetes reindirizza il traffico tra il cluster Kubernetes connesso e il computer di sviluppo. Questo reindirizzamento del traffico consente il codice nel computer di sviluppo e i servizi in esecuzione nel cluster Kubernetes per comunicare come se fossero nello stesso cluster Kubernetes. Il processo locale con Kubernetes fornisce anche un modo per replicare le variabili di ambiente e i volumi montati disponibili per i Pod nel cluster Kubernetes nel computer di sviluppo. Fornire l'accesso alle variabili di ambiente e ai volumi montati nel computer di sviluppo consente di lavorare rapidamente sul codice senza dover replicare manualmente tali dipendenze.

In questa guida si apprenderà come usare il processo locale con Kubernetes per reindirizzare il traffico tra il cluster Kubernetes e il codice in esecuzione nel computer di sviluppo. Questa guida fornisce anche uno script per la distribuzione di un'applicazione di esempio di grandi dimensioni con più microservizi in un cluster Kubernetes.

> [!IMPORTANT]
> Questa funzionalità è attualmente in anteprima. Le anteprime vengono rese disponibili per l'utente a condizione che si accettino le [condizioni d'uso aggiuntive][preview-terms]. Alcuni aspetti di questa funzionalità potrebbero subire modifiche prima della disponibilità a livello generale.

## <a name="before-you-begin"></a>Prima di iniziare

Questa guida usa l' [applicazione di esempio bike sharing][bike-sharing-github] per dimostrare la connessione del computer di sviluppo a un cluster Kubernetes. Se si dispone già di un'applicazione in esecuzione in un cluster Kubernetes, è comunque possibile seguire la procedura seguente e usare i nomi dei propri servizi.

### <a name="prerequisites"></a>Prerequisiti

* Una sottoscrizione di Azure. Se non si ha una sottoscrizione di Azure, è possibile creare un [account gratuito](https://azure.microsoft.com/free).
* [L'interfaccia della riga di comando di Azure installata][azure-cli].
* [Visual Studio 2019][visual-studio] versione 16,7 Preview 4 o successiva in esecuzione in Windows 10 con il carico di lavoro *sviluppo di Azure* installato.
* [Processo locale per l'estensione Kubernetes installato][lpk-extension].

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
chmod +x ./local-process-quickstart.sh
./local-process-quickstart.sh -g MyResourceGroup -n MyAKS
```

Passare all'applicazione di esempio che esegue il cluster aprendo il relativo URL pubblico, che viene visualizzato nell'output dello script di installazione.

```console
$ ./local-process-quickstart.sh -g MyResourceGroup -n MyAKS
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

Aprire *Mindaro/Samples/BikeSharingApp/ReservationEngine/app. csproj* dall' [applicazione di esempio bike sharing][bike-sharing-github] in Visual Studio.

Nel progetto selezionare *processo locale con Kubernetes* dall'elenco a discesa Impostazioni di avvio, come illustrato di seguito.

![Scegliere il processo locale con Kubernetes](media/local-process-kubernetes/choose-local-process.png)

Fare clic sul pulsante Start accanto a *processo locale con Kubernetes*. Nella finestra di dialogo *processo locale con Kubernetes* :

* Selezionare la propria sottoscrizione.
* Selezionare *MyAKS* per il cluster.
* Selezionare *dev* per lo spazio dei nomi.
* Selezionare *reservationengine* per il servizio da reindirizzare.
* Selezionare *app* per il profilo di avvio.
* Selezionare `http://bikeapp.bikesharingweb.EXTERNAL_IP.nip.io` l'URL per avviare il browser.

![Scegliere il processo locale con il cluster Kubernetes](media/local-process-kubernetes/choose-local-process-cluster.png)

> [!IMPORTANT]
> È possibile reindirizzare solo i servizi che dispongono di un singolo POD.

Fare clic su *Salva e avviare il debug*.

Tutto il traffico nel cluster Kubernetes viene reindirizzato per il servizio *reservationengine* alla versione dell'applicazione in esecuzione nel computer di sviluppo. Il processo locale con Kubernetes instrada anche tutto il traffico in uscita dall'applicazione al cluster Kubernetes.

> [!NOTE]
> Verrà richiesto di consentire l'esecuzione di *KubernetesDNSManager* con privilegi elevati e di modificare il file degli host.

Il computer di sviluppo è connesso quando la barra di stato indica che si è connessi al servizio *reservationengine* .

![Computer di sviluppo connesso](media/local-process-kubernetes/development-computer-connected.png)

> [!NOTE]
> All'avvio di subesquent, non verrà visualizzata la finestra di dialogo *processo locale con Kubernetes* . Le impostazioni vengono aggiornate nel riquadro *debug* delle proprietà del progetto.

Quando il computer di sviluppo è connesso, il traffico inizia a reindirizzare al computer di sviluppo per il servizio che si sta sostituendo.

## <a name="set-a-break-point"></a>Imposta un punto di rottura

Aprire [BikesHelper.cs][bikeshelper-cs-breakpoint] e fare clic in un punto qualsiasi della riga 26 per posizionare il cursore. Per impostare un punto di interruzione, premere *F9* oppure fare clic su *debug* e quindi su *Imposta/Rimuovi*punto

Passare all'applicazione di esempio aprendo l'URL pubblico. Selezionare *Aurelia Briggs (Customer)* come utente, quindi selezionare una bicicletta da affittare. Fare clic su *Rent Bike*. Tornare a Visual Studio e osservare che la riga 26 è evidenziata. Il punto di interruzione impostato ha sospeso il servizio alla riga 26. Per riprendere il servizio, premere *F5* oppure fare clic su *Debug* e quindi su *Continua*. Tornare al browser e verificare che la pagina indichi che la bicicletta è stata affittata.

Rimuovere il punto di interruzione inserendo il cursore sulla riga 26 in `BikesHelper.cs` e premendo *F9*.

> [!NOTE]
> Per impostazione predefinita, l'arresto dell'attività di debug disconnette anche il computer di sviluppo dal cluster Kubernetes. È possibile modificare questo comportamento modificando *Disconnetti dopo il debug* su *false* nella sezione *strumenti di debug Kubernetes* delle opzioni di debug. Dopo aver aggiornato questa impostazione, il computer di sviluppo rimarrà connesso quando si arresta e si avvia il debug. Per disconnettere il computer di sviluppo dal cluster, fare clic sul pulsante *Disconnetti* sulla barra degli strumenti.
>
> Se Visual Studio termina improvvisamente la connessione al cluster o termina, il servizio da reindirizzare potrebbe non essere ripristinato allo stato originale prima della connessione al processo locale con Kubernetes. Per risolvere questo problema, vedere la [Guida alla risoluzione dei problemi][troubleshooting].

## <a name="additional-configuration"></a>Configurazione aggiuntiva

Il processo locale con Kubernetes può gestire il routing del traffico e la replica delle variabili di ambiente senza alcuna configurazione aggiuntiva. Se è necessario scaricare i file montati nel contenitore del cluster Kubernetes, ad esempio un file ConfigMap, è possibile creare un per scaricare i file nel `KubernetesLocalProcessConfig.yaml` computer di sviluppo. Per ulteriori informazioni, vedere [utilizzo di KubernetesLocalProcessConfig. YAML per la configurazione aggiuntiva con per il processo locale con Kubernetes][kubernetesLocalProcessConfig-yaml].

## <a name="using-logging-and-diagnostics"></a>Uso della registrazione e della diagnostica

È possibile trovare i log di diagnostica in `Local Process with Kubernetes` directory nella directory *temporanea* del computer di sviluppo. 

## <a name="remove-the-sample-application-from-your-cluster"></a>Rimuovere l'applicazione di esempio dal cluster

Usare lo script fornito per rimuovere l'applicazione di esempio dal cluster.

```azurecli-interactive
./local-process-quickstart.sh -c -g MyResourceGroup -n MyAKS
```

## <a name="next-steps"></a>Passaggi successivi

Informazioni sul funzionamento del processo Kubernetes locale.

> [!div class="nextstepaction"]
> [Come funziona Processo locale con Kubernetes](overview-local-process-kubernetes.md)

[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-vs-code]: https://marketplace.visualstudio.com/items?itemName=azuredevspaces.azds
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-lates
[azure-cloud-shell]: /azure/cloud-shell/w.md
[az-aks-get-credentials]: /cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials
[az-aks-vs-code]: https://marketplace.visualstudio.com/items?itemName=ms-kubernetes-tools.vscode-aks-tools
[bike-sharing-github]: https://github.com/Microsoft/mindaro
[preview-terms]: https://azure.microsoft.com/support/legal/preview-supplemental-terms/
[bikeshelper-cs-breakpoint]: https://github.com/Microsoft/mindaro/blob/master/samples/BikeSharingApp/ReservationEngine/BikesHelper.cs#L26
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[lpk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-local-process-with-kubernetes.md