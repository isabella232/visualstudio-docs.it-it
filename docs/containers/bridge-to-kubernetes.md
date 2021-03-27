---
title: Usare Bridge per Kubernetes con Visual Studio
titleSuffix: ''
ms.technology: vs-azure
ms.date: 03/24/2021
ms.topic: quickstart
description: Informazioni su come usare Bridge per Kubernetes con Visual Studio per connettere il computer di sviluppo a un cluster Kubernetes
keywords: Bridge per Kubernetes, Azure Dev Spaces, spazi di sviluppo, Docker, Kubernetes, Azure, contenitori
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jmartens
ms.openlocfilehash: fdcf31d062fe2be72709979f0892e6a7f535024a
ms.sourcegitcommit: 2049ec99f1439ec91d002853226934b067b1ee70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2021
ms.locfileid: "105635052"
---
# <a name="use-bridge-to-kubernetes"></a>Usare Bridge per Kubernetes

È possibile usare Bridge per Kubernetes per reindirizzare il traffico tra il cluster Kubernetes e il codice in esecuzione nel computer di sviluppo. Questa guida fornisce anche uno script per la distribuzione di un'applicazione di esempio di grandi dimensioni con più microservizi in un cluster Kubernetes.

## <a name="before-you-begin"></a>Prima di iniziare

Questa guida usa l' [applicazione di esempio todo app][todo-app-github] per dimostrare la connessione del computer di sviluppo a un cluster Kubernetes. Se si dispone già di un'applicazione in esecuzione in un cluster Kubernetes, è comunque possibile seguire la procedura seguente e usare i nomi dei propri servizi.

Questo esempio illustra il modo in cui è possibile usare Bridge per Kubernetes per sviluppare una versione di microservizio di una semplice applicazione TODO in qualsiasi cluster Kubernetes. Questo esempio, usando Visual Studio, è stato adattato dal codice fornito da [TodoMVC](http://todomvc.com). Questi passaggi dovrebbero funzionare con qualsiasi cluster Kubernetes.

L'esempio TODO Application è costituito da un front-end e da un back-end che fornisce l'archiviazione permanente. Questo esempio esteso aggiunge un componente Statistics e suddivide l'applicazione in diversi microservizi, in particolare:

- Il front-end chiama l'API del database per salvare in modo permanente e aggiornare gli elementi TODO.
- Il servizio API di database si basa su un database Mongo per salvare in modo permanente gli elementi TODO.
- Il front-end scrive gli eventi Aggiungi, completa ed Elimina in una coda RabbitMQ;
- Un ruolo di lavoro statistici riceve gli eventi dalla coda RabbitMQ e aggiorna una cache Redis;
- Un'API Statistics espone le statistiche memorizzate nella cache per il front-end da visualizzare.

In tutte queste applicazioni TODO estese sono costituite da sei componenti correlati.

### <a name="prerequisites"></a>Prerequisiti

- un cluster Kubernetes
- [Visual Studio 2019][visual-studio] versione 16,7 Preview 4 o versione successiva in esecuzione in Windows 10.
- [Estensione Bridge to Kubernetes installata][btk-extension].

## <a name="check-the-cluster"></a>Controllare il cluster

Aprire un prompt dei comandi e verificare che kubectl sia installato e nel percorso, il cluster che si vuole usare sia disponibile e pronto e impostare il contesto su tale cluster.

```cmd
kubectl cluster-info
kubectl config use-context {context-name}
```

dove {Context-Name} è il nome del contesto per il cluster che si vuole usare per l'esempio todo-app.

## <a name="deploy-the-application"></a>Distribuire l'applicazione

Clonare il [repository Mindaro](https://github.com/Microsoft/mindaro) e aprire una finestra di comando con la cartella di lavoro corrente in *Samples/todo-app*.

Creare uno spazio dei nomi per l'esempio.

```cmd
kubectl create namespace todo-app
```

Applicare quindi il manifesto di distribuzione:

```cmd
kubectl apply -n todo-app -f deployment.yaml
```

Si tratta di una semplice distribuzione che espone il front-end usando un servizio di tipo `LoadBalancer` . Attendere che tutti i pod siano in esecuzione e che l'indirizzo IP esterno del `frontend` servizio diventi disponibile.

Se si esegue il test con MiniKube, sarà necessario usare `minikube tunnel` per risolvere un indirizzo IP esterno. Se si usa AKS o un altro provider Kubernetes basato sul cloud, viene assegnato automaticamente un indirizzo IP esterno. Usare il comando seguente per monitorare il `frontend` servizio per attendere che sia attivo e in esecuzione:

```output
kubectl get service -n todo-app frontend --watch

NAME       TYPE           CLUSTER-IP    EXTERNAL-IP     PORT(S)        AGE
frontend   LoadBalancer   10.0.245.78   20.73.226.228   80:31910/TCP   6m26s
```

Individuare l'applicazione usando l'indirizzo IP esterno e la porta locale (il primo numero nella colonna porta/e).

```
http://{external-ip}:{local-port}
```

Testare l'app in esecuzione nel browser. Quando si aggiungono, completano ed eliminano elementi todo, si noti che la pagina statistiche viene aggiornata con le metriche previste.

## <a name="connect-to-your-cluster-and-debug-a-service"></a>Connettersi al cluster ed eseguire il debug di un servizio

Aprire *samples\todo-app\database-api\database-API.csproj* in Visual Studio. Nel progetto selezionare **Bridge to Kubernetes** dall'elenco a discesa delle impostazioni di avvio, come illustrato di seguito.

![Scegliere Bridge to Kubernetes](media/bridge-to-kubernetes/choose-bridge-to-kubernetes.png)

Fare clic sul pulsante Start accanto a *Bridge to Kubernetes*. Nella finestra di dialogo **Crea profilo per Bridge to Kubernetes** :

- Selezionare il nome del cluster.
- Selezionare *todo-app* per lo spazio dei nomi.
- Selezionare *database-API* per il servizio da reindirizzare.
- Selezionare lo stesso URL usato in precedenza per avviare il browser, http://{External-IP}: {Local-Port}

![Scegliere il Bridge per il cluster Kubernetes](media/bridge-to-kubernetes/configure-bridge-debugging.png)

Scegliere se eseguire o meno l'isolamento, vale a dire che altri utenti che usano il cluster non saranno interessati dalle modifiche apportate. Questa modalità di isolamento viene eseguita tramite il routing delle richieste alla copia di ogni servizio interessato, ma il routing di tutto il traffico in modo normale. Per ulteriori informazioni su come eseguire questa operazione, vedere la pagina relativa alla [modalità di funzionamento di Bridge to Kubernetes][btk-overview-routing].

Fare clic su **OK**. Tutto il traffico nel cluster Kubernetes viene reindirizzato per il servizio *API del database* alla versione dell'applicazione in esecuzione nel computer di sviluppo. Bridge to Kubernetes instrada anche tutto il traffico in uscita dall'applicazione al cluster Kubernetes.

> [!NOTE]
> Verrà richiesto di consentire l'esecuzione di *EndpointManager* con privilegi elevati e di modificare il file degli host.

Il computer di sviluppo è connesso quando la barra di stato indica che si è connessi al `database-api` servizio.

![Computer di sviluppo connesso](media/bridge-to-kubernetes/development-computer-connected.png)

> [!NOTE]
> All'avvio successivo non verrà visualizzata la finestra di dialogo **Crea profilo per Bridge per Kubernetes** . Le impostazioni vengono aggiornate in **debug** nelle proprietà del progetto.

Quando il computer di sviluppo è connesso, il traffico inizia a reindirizzare al computer di sviluppo per il servizio che si sta sostituendo.

> [!NOTE]
> Per modificare il profilo di debug in un secondo momento, ad esempio se si vuole eseguire il test con un servizio Kubernetes diverso, scegliere **debug**  >  **Proprietà debug**, quindi fare clic sul pulsante **Cambia** .

## <a name="set-a-break-point"></a>Imposta un punto di rottura

Aprire MongoHelper. cs e fare clic in un punto qualsiasi della riga 68 nel metodo CreateTask per posizionare il cursore. Per impostare un punto di interruzione, premere *F9* o selezionare **debug**  >  **Imposta/Rimuovi** punto di interruzione.

Passare all'applicazione di esempio aprendo l'URL pubblico (l'indirizzo IP esterno per il servizio front-end). Per riprendere il servizio, premere **F5** o fare clic su **debug**  >  **continua**.

Rimuovere il punto di interruzione inserendo il cursore sulla riga con il punto di interruzione e premendo **F9**.

> [!NOTE]
> Per impostazione predefinita, l'arresto dell'attività di debug disconnette anche il computer di sviluppo dal cluster Kubernetes. È possibile modificare questo comportamento modificando **Disconnetti dopo** il debug `false` in nella sezione **strumenti di debug Kubernetes** della   >  finestra di dialogo **Opzioni** strumenti. Dopo aver aggiornato questa impostazione, il computer di sviluppo rimarrà connesso quando si arresta e si avvia il debug. Per disconnettere il computer di sviluppo dal cluster, fare clic sul pulsante **Disconnetti** sulla barra degli strumenti.
>
>![Screenshot delle opzioni di debug di Kubernetes](media/bridge-to-kubernetes/kubernetes-debugging-options.png)

## <a name="additional-configuration"></a>Configurazione aggiuntiva

Bridge to Kubernetes è in grado di gestire il routing del traffico e di replicare le variabili di ambiente senza alcuna configurazione aggiuntiva. Se è necessario scaricare i file montati nel contenitore del cluster Kubernetes, ad esempio un file ConfigMap, è possibile creare un per scaricare i file nel `KubernetesLocalProcessConfig.yaml` computer di sviluppo. Per ulteriori informazioni, vedere [utilizzo di KubernetesLocalProcessConfig. YAML per la configurazione aggiuntiva con per Bridge in Kubernetes][kubernetesLocalProcessConfig-yaml].

## <a name="using-logging-and-diagnostics"></a>Uso della registrazione e della diagnostica

È possibile trovare i log di diagnostica in `Bridge to Kubernetes` directory nella directory *temporanea* del computer di sviluppo.

## <a name="next-steps"></a>Passaggi successivi

Informazioni sul funzionamento del Bridge per Kubernetes.

> [!div class="nextstepaction"]
> [Come funziona Bridge per Kubernetes](overview-bridge-to-kubernetes.md)

[todo-app-github]: https://github.com/Microsoft/mindaro
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-bridge-to-kubernetes.md
[btk-overview-routing]: overview-bridge-to-kubernetes.md#using-routing-capabilities-for-developing-in-isolation