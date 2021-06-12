---
title: Come funziona Bridge per Kubernetes
ms.technology: vs-azure
ms.date: 11/19/2020
ms.topic: conceptual
description: Descrive i processi per l'uso Bridge to Kubernetes connettere il computer di sviluppo al cluster Kubernetes
keywords: Bridge to Kubernetes, Docker, Kubernetes, Azure, contenitori
monikerRange: '>=vs-2019'
manager: jmartens
author: ghogen
ms.author: ghogen
ms.openlocfilehash: 838589e0dd81232de25b88989d621a07fb22f972
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2021
ms.locfileid: "112043055"
---
# <a name="how-bridge-to-kubernetes-works"></a>Come funziona Bridge per Kubernetes

Bridge to Kubernetes consente di eseguire ed eseguire il debug del codice nel computer di sviluppo, mentre è ancora connesso al cluster Kubernetes con il resto dell'applicazione o dei servizi. Ad esempio, se si dispone di un'architettura di microservizi di grandi dimensioni con molti database e servizi interdipendenti, la replica di tali dipendenze nel computer di sviluppo può risultare difficile. Inoltre, la compilazione e la distribuzione di codice nel cluster Kubernetes per ogni modifica del codice durante lo sviluppo del ciclo interno può essere lenta, dispendiosa in termini di tempo e difficile da usare con un debugger.

Bridge to Kubernetes evitare di dover compilare e distribuire il codice nel cluster creando invece una connessione direttamente tra il computer di sviluppo e il cluster. La connessione del computer di sviluppo al cluster durante il debug consente di testare e sviluppare rapidamente il servizio nel contesto dell'applicazione completa senza creare alcuna configurazione Docker o Kubernetes.

Bridge to Kubernetes reindirizza il traffico tra il cluster Kubernetes connesso e il computer di sviluppo. Questo reindirizzamento del traffico consente al codice nel computer di sviluppo e ai servizi in esecuzione nel cluster Kubernetes di comunicare come se fossero nello stesso cluster Kubernetes. Bridge to Kubernetes offre anche un modo per replicare le variabili di ambiente e i volumi montati disponibili per i pod nel cluster Kubernetes nel computer di sviluppo. L'accesso alle variabili di ambiente e ai volumi montati nel computer di sviluppo consente di lavorare rapidamente sul codice senza dover replicare manualmente tali dipendenze.

> [!WARNING]
> Bridge to Kubernetes è destinato all'uso solo negli scenari di sviluppo e test. Non è destinato o supportato per l'uso con cluster di produzione o servizi live in uso attivo.

Informazioni sulle funzionalità attualmente supportate e una roadmap futura per Bridge to Kubernetes sono disponibili in Bridge to Kubernetes [roadmap](https://github.com/microsoft/mindaro/projects/1).

## <a name="using-bridge-to-kubernetes"></a>Uso di Bridge to Kubernetes

Per usare Bridge to Kubernetes in Visual Studio, è necessario [Visual Studio 2019][visual-studio] versione 16.7 Preview 4 o successiva in esecuzione in Windows 10 con il carico di lavoro sviluppo web e *ASP.NET* installato e l'estensione [Bridge to Kubernetes][btk-extension] installata. Quando si usa Bridge to Kubernetes per stabilire una connessione al cluster Kubernetes, è possibile reindirizzare tutto il traffico da e verso un pod esistente nel cluster al computer di sviluppo.

> [!NOTE]
> Quando si Bridge to Kubernetes, viene richiesto il nome del servizio da reindirizzare al computer di sviluppo. Questa opzione è un modo pratico per identificare un pod per il reindirizzamento. Tutti i reindirizzamenti tra il cluster Kubernetes e il computer di sviluppo sono per un pod.

Quando Bridge to Kubernetes stabilisce una connessione al cluster, è possibile:

* Richiede di configurare il servizio per la sostituzione nel cluster, la porta nel computer di sviluppo da usare per il codice e l'attività di avvio per il codice come azione una sola volta.
* Sostituisce il contenitore nel pod nel cluster con un contenitore agente remoto che reindirizza il traffico al computer di sviluppo.
* Esegue [kubectl port-forward][kubectl-port-forward] nel computer di sviluppo per inoltrare il traffico dal computer di sviluppo all'agente remoto in esecuzione nel cluster.
* Raccoglie le informazioni sull'ambiente dal cluster usando l'agente remoto. Queste informazioni sull'ambiente includono variabili di ambiente, servizi visibili, montamenti di volumi e montamenti segreti.
* Configura l'ambiente in Visual Studio in modo che il servizio nel computer di sviluppo possa accedere alle stesse variabili di se fosse in esecuzione nel cluster.
* Aggiorna il file hosts per eseguire il mapping dei servizi nel cluster agli indirizzi IP locali nel computer di sviluppo. Queste voci di file host consentono al codice in esecuzione nel computer di sviluppo di effettuare richieste ad altri servizi in esecuzione nel cluster. Per aggiornare il file hosts, Bridge to Kubernetes richiederà l'accesso come amministratore nel computer di sviluppo durante la connessione al cluster.
* Avvia l'esecuzione e il debug del codice nel computer di sviluppo. Se necessario, Bridge to Kubernetes le porte necessarie nel computer di sviluppo arrestando i servizi o i processi che attualmente usano tali porte.

Dopo aver stabilito una connessione al cluster, è possibile eseguire ed eseguire il debug del codice in modo nativo nel computer, senza contenitori, e il codice può interagire direttamente con il resto del cluster. Qualsiasi traffico di rete ricevuto dall'agente remoto viene reindirizzato alla porta locale specificata durante la connessione, in modo che il codice in esecuzione in modo nativo possa accettare ed elaborare il traffico. Le variabili di ambiente, i volumi e i segreti del cluster vengono resi disponibili per il codice in esecuzione nel computer di sviluppo. Inoltre, a causa delle voci del file hosts e del port forwarding aggiunto al computer di sviluppo da Bridge to Kubernetes, il codice può inviare il traffico di rete ai servizi in esecuzione nel cluster usando i nomi dei servizi dal cluster e tale traffico viene inoltrato ai servizi in esecuzione nel cluster. Il traffico viene instradato tra il computer di sviluppo e il cluster per l'intera durata della connessione.

Inoltre, Bridge to Kubernetes un modo per replicare le variabili di ambiente e i file montati disponibili per i pod nel cluster nel computer di sviluppo tramite il `KubernetesLocalProcessConfig.yaml` file. È anche possibile usare questo file per creare nuove variabili di ambiente e montamenti di volume.

> [!NOTE]
> Per la durata della connessione al cluster (più altri 15 minuti), Bridge to Kubernetes un processo denominato *EndpointManager* con autorizzazioni di amministratore nel computer locale.

> [!NOTE]
> È possibile eseguire il debug in parallelo, con più servizi, ma è necessario avviare tutte le istanze di Visual Studio dei servizi di cui si vuole eseguire il debug. Assicurarsi che i servizi siano in ascolto su porte diverse in locale e quindi configurarli ed eseguirne il debug separatamente. L'isolamento non è supportato in questo scenario.

## <a name="additional-configuration-with-kuberneteslocalprocessconfigyaml"></a>Configurazione aggiuntiva con KubernetesLocalProcessConfig.yaml

Il `KubernetesLocalProcessConfig.yaml` file consente di replicare le variabili di ambiente e i file montati disponibili per i pod nel cluster. Quando si usa Visual Studio per lo sviluppo Bridge to Kubernetes, il file KubernetesLocalConfig.yaml deve trovarsi nella stessa directory del file di progetto per il servizio che si sta reindirizzando. Per altre informazioni sulle opzioni di configurazione aggiuntive, vedere [Configurare Bridge to Kubernetes][using-config-yaml].

## <a name="using-routing-capabilities-for-developing-in-isolation"></a>Uso delle funzionalità di routing per lo sviluppo in isolamento

Per impostazione predefinita, Bridge to Kubernetes tutto il traffico per un servizio al computer di sviluppo. È anche possibile usare le funzionalità di routing per reindirizzare solo le richieste a un servizio proveniente da un sottodominio al computer di sviluppo. Queste funzionalità di routing consentono di usare Bridge to Kubernetes sviluppare in isolamento ed evitare l'interruzione di altro traffico nel cluster.

L'animazione seguente mostra due sviluppatori che lavorano nello stesso cluster in isolamento:

![GIF animata che illustra l'isolamento](media/bridge-to-kubernetes/btk-graphic-isolated.gif)

Quando si abilita l'isolamento, Bridge to Kubernetes le operazioni seguenti oltre alla connessione al cluster Kubernetes:

* Verifica che il cluster Kubernetes non abbia Azure Dev Spaces abilitata.
* Replica il servizio scelto nel cluster nello stesso spazio dei nomi e aggiunge un'etichetta routing.visualstudio.io/route-from=SERVICE_NAME *e* *routing.visualstudio.io/route-on-header=kubernetes-route-as:* GENERATED_NAME annotazione.
* Configura e avvia gestione routing nello stesso spazio dei nomi nel cluster Kubernetes. Il gestore di routing usa un  selettore di etichetta per cercare l'etichetta routing.visualstudio.io/route-from=SERVICE_NAME e *routing.visualstudio.io/route-on-header=kubernetes-route-as:* annotazione GENERATED_NAME quando si configura il routing nello spazio dei nomi.

Se Bridge to Kubernetes rileva che Azure Dev Spaces è abilitato nel cluster Kubernetes, viene richiesto di disabilitare Azure Dev Spaces prima di poter usare Bridge to Kubernetes.

Il gestore di routing esegue le operazioni seguenti all'avvio:

* Duplica tutti gli ingressi (inclusi gli ingressi del servizio di bilanciamento del carico) trovati nello spazio dei *nomi usando* il GENERATED_NAME per il sottodominio.
* Crea un pod envoy per ogni servizio associato a ingressi duplicati con il *GENERATED_NAME* sottodominio.
* Crea un pod dell'inviato aggiuntivo per il servizio su cui si sta lavorando in isolamento. In questo modo le richieste con il sottodominio possono essere indirizzate al computer di sviluppo.
* Configura le regole di routing per ogni pod dell'inviato per gestire il routing per i servizi con il sottodominio.

Il diagramma seguente illustra un cluster Kubernetes prima Bridge to Kubernetes connettersi al cluster:

![Diagramma del cluster senza Bridge to Kubernetes](media/bridge-to-kubernetes/kubr-cluster.svg)

Il diagramma seguente mostra lo stesso cluster con Bridge to Kubernetes abilitata in modalità di isolamento. Qui è possibile visualizzare il servizio duplicato e i pod di envoy che supportano il routing in isolamento.

![Diagramma del cluster con Bridge to Kubernetes abilitata](media/bridge-to-kubernetes/kubr-cluster-devcomputer.svg)

Quando una richiesta con *GENERATED_NAME* sottodominio viene ricevuta nel cluster, viene aggiunta un'intestazione *kubernetes-route-as=GENERATED_NAME* alla richiesta. I pod dell'inviato gestiscono il routing della richiesta al servizio appropriato nel cluster. Se la richiesta viene instradata al servizio su cui viene lavorato in isolamento, tale richiesta viene reindirizzata al computer di sviluppo dall'agente remoto.

Quando una richiesta senza *GENERATED_NAME* sottodominio viene ricevuta nel cluster, non viene aggiunta alcuna intestazione alla richiesta. I pod dell'inviato gestiscono il routing della richiesta al servizio appropriato nel cluster. Se la richiesta viene instradata al servizio che viene sostituito, tale richiesta viene invece indirizzata al servizio originale anziché all'agente remoto.

> [!IMPORTANT]
> Ogni servizio nel cluster deve inoltrare l'intestazione *kubernetes-route-as=GENERATED_NAME* quando si effettuano richieste aggiuntive. Ad esempio, quando *il servizioA* riceve una richiesta, effettua una richiesta a *serviceB* prima di restituire una risposta. In questo esempio, *serviceA* deve inoltrare l'intestazione *kubernetes-route-as=GENERATED_NAME* nella richiesta a *serviceB*. Alcuni linguaggi, ad esempio [ASP.NET][asp-net-header], possono avere metodi per la gestione della propagazione dell'intestazione.

Quando ci si disconnette dal cluster, per impostazione Bridge to Kubernetes rimuoverà tutti i pod dell'inviato e il servizio duplicato.

> [!NOTE]
> La distribuzione del gestore di routing e il servizio rimarranno in esecuzione nello spazio dei nomi. Per rimuovere la distribuzione e il servizio, eseguire i comandi seguenti per lo spazio dei nomi.
>
> ```azurecli
> kubectl delete deployment routingmanager-deployment -n NAMESPACE
> kubectl delete service routingmanager-service -n NAMESPACE
> ```

## <a name="diagnostics-and-logging"></a>Diagnostica e registrazione

Quando si Bridge to Kubernetes per connettersi al cluster, i log di diagnostica del cluster vengono registrati nella directory *TEMP* del computer di sviluppo nella *cartella Bridge to Kubernetes.*

## <a name="rbac-authorization"></a>Autorizzazione del controllo degli accessi in base al ruolo

Kubernetes fornisce il controllo degli accessi in base al ruolo per gestire le autorizzazioni per utenti e gruppi. Per informazioni, vedere la documentazione di [Kubernetes](https://kubernetes.io/docs/reference/access-authn-authz/rbac/) È possibile impostare le autorizzazioni per un cluster abilitato per il controllo degli accessi in base al ruolo creando un file YAML e usando per `kubectl` applicarlo al cluster. 

Per impostare le autorizzazioni per il cluster, creare o modificare un file YAML, ad esempio *permissions.yml* come il seguente, usando il proprio spazio dei nomi per e gli argomenti (utenti e gruppi) che necessitano `<namespace>` dell'accesso.

```yml
kind: RoleBinding
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: bridgetokubernetes-<namespace>
  namespace: development
subjects:
  - kind: User
    name: jane.w6wn8.k8s.ginger.eu-central-1.aws.gigantic.io
    apiGroup: rbac.authorization.k8s.io
  - kind: Group
    name: dev-admin
    apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: ClusterRole
  name: admin
  apiGroup: rbac.authorization.k8s.io
```

Applicare le autorizzazioni usando il comando :

```cmd
kubectl -n <namespace> apply -f <yaml file name>
```

## <a name="limitations"></a>Limitazioni

Bridge to Kubernetes presenta le limitazioni seguenti:

* Un pod può avere un solo contenitore in esecuzione in tale pod per Bridge to Kubernetes la connessione.
* Attualmente, Bridge to Kubernetes pod devono essere contenitori Linux. I contenitori Windows non sono supportati.
* Bridge to Kubernetes autorizzazioni elevate per l'esecuzione nel computer di sviluppo per modificare il file hosts.
* Bridge to Kubernetes non può essere usato nei cluster con Azure Dev Spaces abilitata.

### <a name="bridge-to-kubernetes-and-clusters-with-azure-dev-spaces-enabled"></a>Bridge to Kubernetes e cluster con Azure Dev Spaces abilitata

Non è possibile usare Bridge to Kubernetes in un cluster con Azure Dev Spaces abilitata. Se si vuole usare Bridge to Kubernetes in un cluster con Azure Dev Spaces abilitata, è necessario disabilitare Azure Dev Spaces prima di connettersi al cluster.

## <a name="next-steps"></a>Passaggi successivi

Per iniziare a usare Bridge to Kubernetes connettersi al computer di sviluppo locale al cluster, vedere [Usare](bridge-to-kubernetes.md)Bridge to Kubernetes .

[asp-net-header]: https://www.nuget.org/packages/Microsoft.AspNetCore.HeaderPropagation/
[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-tmp-dir]: /azure/dev-spaces/troubleshooting#before-you-begin
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-latest&preserve-view=true
[bridge-to-kubernetes-vs]: bridge-to-kubernetes.md
[kubectl-port-forward]: https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#port-forward
[visual-studio]: https://visualstudio.microsoft.com/downloads/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[using-config-yaml]: configure-bridge-to-kubernetes.md
