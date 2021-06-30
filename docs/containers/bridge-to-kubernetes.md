---
title: 'Esercitazione: Connettere computer di sviluppo con Bridge to Kubernetes'
ms.technology: vs-azure
ms.date: 03/24/2021
ms.topic: tutorial
description: Connettere il computer di sviluppo a un cluster Kubernetes con Bridge to Kubernetes con Visual Studio.
keywords: Bridge to Kubernetes, Azure Dev Spaces, Dev Spaces, Docker, Kubernetes, Azure, contenitori
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jmartens
ms.openlocfilehash: b8d6c98d2e2146ad57871b74cd2d522ed2b04259
ms.sourcegitcommit: 0499d813d5c24052c970ca15373d556a69507250
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2021
ms.locfileid: "113046118"
---
# <a name="tutorial-use-bridge-to-kubernetes-to-connect-your-clusters-and-your-development-computers"></a>Esercitazione: Usare Bridge to Kubernetes per connettere i cluster e i computer di sviluppo

In questa esercitazione si apprenderà come usare Bridge to Kubernetes per reindirizzare il traffico tra il cluster Kubernetes e il codice in esecuzione nel computer di sviluppo. 

Questa guida fornisce anche uno script per la distribuzione di un'applicazione di esempio di grandi dimensioni con più microservizi in un cluster Kubernetes.

Per altre informazioni Bridge to Kubernetes vedere l'articolo [Come Bridge to Kubernetes funzionamento.](overview-bridge-to-kubernetes.md)

## <a name="prerequisites"></a>Prerequisiti

- Un cluster Kubernetes
- [Visual Studio 2019][visual-studio] versione 16.7 Preview 4 o successiva in esecuzione Windows 10.
- [Bridge to Kubernetes'estensione installata][btk-extension]

## <a name="about-the-data"></a>Informazioni sui dati

Questa esercitazione usa Bridge to Kubernetes per sviluppare una versione di microservizio di una semplice applicazione di esempio TODO in qualsiasi cluster Kubernetes. Questa [applicazione di esempio di app TODO,][todo-app-github]Visual Studio, è stata adattata dal codice fornito da [TodoMVC.](http://todomvc.com) 

 Questi passaggi dovrebbero funzionare con qualsiasi cluster Kubernetes. Pertanto, se la propria applicazione è già in esecuzione in un cluster Kubernetes, è comunque possibile seguire la procedura seguente e usare i nomi dei propri servizi.

L'esempio di applicazione TODO è costituito da un front-end e un back-end che fornisce l'archiviazione permanente. Questo esempio esteso aggiunge un componente statistiche e suddivide l'applicazione in diversi microservizi, in particolare:

- Il front-end chiama database-api per rendere persistenti e aggiornare gli elementi TODO.
- Il servizio database-api si basa su un database Mongo per rendere persistenti gli elementi TODO.
- Il front-end scrive eventi di aggiunta, completamento ed eliminazione in una coda RabbitMQ.
- Un ruolo di lavoro per le statistiche riceve gli eventi dalla coda RabbitMQ e aggiorna una cache Redis.
- Un'API per le statistiche espone le statistiche memorizzate nella cache per la visualizzazione del front-end.

In tutto, questa applicazione TODO estesa è costituita da sei componenti correlati.


## <a name="check-the-cluster"></a>Controllare il cluster

Aprire un prompt dei comandi, verificare che sia installato e nel percorso il cluster che si vuole usare sia disponibile e pronto e impostare il contesto `kubectl` su tale cluster.

```cmd
kubectl cluster-info
kubectl config use-context {context-name}
```

dove {context-name} è il nome del contesto per il cluster che si vuole usare per l'esempio todo-app.

## <a name="deploy-the-application"></a>Distribuire l'applicazione

Clonare [il repo mindaro e](https://github.com/Microsoft/mindaro) aprire una finestra di comando con la cartella di lavoro corrente in *samples/todo-app.*

Creare uno spazio dei nomi per l'esempio.

```cmd
kubectl create namespace todo-app
```

Applicare quindi il manifesto della distribuzione:

```cmd
kubectl apply -n todo-app -f deployment.yaml
```

Si tratta di una distribuzione semplice che espone il front-end usando un servizio di tipo `LoadBalancer` . Attendere che tutti i pod siano in esecuzione e che l'indirizzo IP esterno `frontend` del servizio diventi disponibile.

Se si sta testando con MiniKube, è necessario usare `minikube tunnel` per risolvere un indirizzo IP esterno. Se si usa il servizio Kubernetes o un altro provider Kubernetes basato sul cloud, viene assegnato automaticamente un indirizzo IP esterno. Usare il comando seguente per monitorare il servizio in modo che attenda che `frontend` sia operativo:

```output
kubectl get service -n todo-app frontend --watch

NAME       TYPE           CLUSTER-IP    EXTERNAL-IP     PORT(S)        AGE
frontend   LoadBalancer   10.0.245.78   20.73.226.228   80:31910/TCP   6m26s
```

Passare all'applicazione usando l'indirizzo IP esterno e la porta locale (il primo numero nella colonna PORT(S) ).

```
http://{external-ip}:{local-port}
```

Testare l'app in esecuzione nel browser. Quando si aggiungono, completano ed eliminano elementi Attività, si noti che la pagina delle statistiche viene aggiornata con le metriche previste.

## <a name="connect-to-your-cluster-and-debug-a-service"></a>Connettersi al cluster ed eseguire il debug di un servizio

Aprire *samples\todo-app\database-api\database-api.csproj* in Visual Studio. Nel progetto selezionare  Bridge to Kubernetes dall'elenco a discesa delle impostazioni di avvio, come illustrato di seguito.

![Scegliere Bridge to Kubernetes](media/bridge-to-kubernetes/choose-bridge-to-kubernetes.png)

Fare clic sul pulsante Start accanto a *Bridge to Kubernetes*. Nella finestra **di dialogo Crea profilo per Bridge to Kubernetes:**

- Selezionare il nome del cluster.
- Selezionare *todo-app per* lo spazio dei nomi.
- Selezionare *database-api per* il reindirizzamento del servizio.
- Selezionare lo stesso URL usato in precedenza per avviare il browser, http://{external-ip}:{local-port}

![Scegliere Bridge to Kubernetes cluster](media/bridge-to-kubernetes/configure-bridge-debugging.png)

Scegliere se eseguire o meno l'esecuzione isolata, vale a dire che gli altri utenti che usano il cluster non saranno interessati dalle modifiche. Questa modalità di isolamento viene eseguita indirizzando le richieste alla copia di ogni servizio interessato, ma indirizzando normalmente tutto il traffico. Per altre informazioni su come eseguire questa operazione, vedere How Bridge to Kubernetes Works (Funzionamento [di Bridge to Kubernetes).][btk-overview-routing]

Fare clic su **OK**. Tutto il traffico nel cluster Kubernetes viene reindirizzato per il *servizio database-api* alla versione dell'applicazione in esecuzione nel computer di sviluppo. Bridge to Kubernetes anche tutto il traffico in uscita dall'applicazione al cluster Kubernetes.

> [!NOTE]
> Verrà richiesto di consentire a *EndpointManager* di eseguire con privilegi elevati e modificare il file hosts.

Il computer di sviluppo è connesso quando la barra di stato indica che si è connessi al `database-api` servizio.

![Computer di sviluppo connesso](media/bridge-to-kubernetes/development-computer-connected.png)

> [!NOTE]
> Agli avvii successivi, non verrà visualizzata la finestra di dialogo Crea profilo **per** Bridge to Kubernetes. È possibile aggiornare queste impostazioni in **Debug** nelle proprietà del progetto.

Una volta connesso il computer di sviluppo, il traffico inizia a reindirizzare al computer di sviluppo per il servizio che si sta sostituendo.

> [!NOTE]
> Per modificare il profilo di debug in un secondo momento, ad esempio se si vuole eseguire il test con un servizio Kubernetes diverso, scegliere **Debug** Debug Properties (Proprietà debug debug) e fare clic  >  sul pulsante **Change (Modifica).**

## <a name="set-a-break-point"></a>Impostare un punto di interruzione

Aprire MongoHelper.cs e fare clic in un punto qualsiasi della riga 68 nel metodo CreateTask per posizionare il cursore in questa posizione. Impostare un punto di interruzione premendo *F9 o* selezionando Debug   >  **Attiva/Disattiva punto di interruzione**.

Passare all'applicazione di esempio aprendo l'URL pubblico (l'indirizzo IP esterno per il servizio front-end). Per riprendere il servizio, premere **F5 o** fare clic su **Debug**  >  **Continua.**

Rimuovere il punto di interruzione inserendo il cursore sulla riga con il punto di interruzione e premendo **F9.**

> [!NOTE]
> Per impostazione predefinita, l'arresto dell'attività di debug disconnette anche il computer di sviluppo dal cluster Kubernetes. È possibile modificare questo comportamento impostando **Disconnetti dopo** il debug su nella sezione Strumenti di debug `false` di **Kubernetes** della finestra **di dialogo**  >  **Opzioni** degli strumenti. Dopo aver aggiornato questa impostazione, il computer di sviluppo rimarrà connesso quando si arresta e si avvia il debug. Per disconnettere il computer di sviluppo dal cluster, fare clic sul **pulsante Disconnetti** sulla barra degli strumenti.
>
>![Screenshot delle opzioni di debug di Kubernetes](media/bridge-to-kubernetes/kubernetes-debugging-options.png)

## <a name="additional-configuration"></a>Configurazione aggiuntiva

Bridge to Kubernetes possibile gestire il traffico di routing e replicare le variabili di ambiente senza alcuna configurazione aggiuntiva. Se è necessario scaricare i file montati nel contenitore nel cluster Kubernetes, ad esempio un file ConfigMap, è possibile creare un per scaricare tali file nel computer di `KubernetesLocalProcessConfig.yaml` sviluppo. Per altre informazioni, vedere [Uso di KubernetesLocalProcessConfig.yaml][kubernetesLocalProcessConfig-yaml]per la configurazione aggiuntiva con per Bridge to Kubernetes .

## <a name="using-logging-and-diagnostics"></a>Uso della registrazione e della diagnostica

È possibile trovare i log di diagnostica `Bridge to Kubernetes` nella directory nella directory TEMP del computer *di* sviluppo.

## <a name="next-steps"></a>Passaggi successivi

Informazioni sul Bridge to Kubernetes funzionamento.

> [!div class="nextstepaction"]
> [Come funziona Bridge per Kubernetes](overview-bridge-to-kubernetes.md)

[todo-app-github]: https://github.com/Microsoft/mindaro
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-bridge-to-kubernetes.md
[btk-overview-routing]: overview-bridge-to-kubernetes.md#using-routing-capabilities-for-developing-in-isolation
