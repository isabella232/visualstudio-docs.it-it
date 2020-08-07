---
title: Come funziona Processo locale con Kubernetes
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: conceptual
description: Descrive i processi per l'uso del processo locale con Kubernetes per connettere il computer di sviluppo al cluster Kubernetes
keywords: Processo locale con Kubernetes, Docker, Kubernetes, Azure, contenitori
monikerRange: '>=vs-2019'
manager: jillfra
author: ghogen
ms.author: ghogen
ms.openlocfilehash: 5b6c07d5987c52d818a35babd16681652ddf5830
ms.sourcegitcommit: 50bbb62525c91c5a31bab57e1caf37c5638872c8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/07/2020
ms.locfileid: "87913268"
---
# <a name="how-local-process-with-kubernetes-works"></a>Come funziona Processo locale con Kubernetes

Il processo locale con Kubernetes consente di eseguire ed eseguire il debug del codice nel computer di sviluppo, mentre è ancora connesso al cluster Kubernetes con il resto dell'applicazione o dei servizi. Ad esempio, se si dispone di un'architettura di microservizi di grandi dimensioni con molti servizi e database interdipendenti, la replica di tali dipendenze nel computer di sviluppo può essere difficile. Inoltre, la compilazione e la distribuzione di codice nel cluster Kubernetes per ogni modifica del codice durante lo sviluppo a ciclo interno possono essere lenti, dispendiose in termini di tempo e difficili da usare con un debugger.

Il processo locale con Kubernetes evita di dover compilare e distribuire il codice nel cluster creando invece una connessione direttamente tra il computer di sviluppo e il cluster. Connettendo il computer di sviluppo al cluster durante il debug è possibile testare e sviluppare rapidamente il servizio nel contesto dell'applicazione completa senza creare una configurazione Docker o Kubernetes.

Il processo locale con Kubernetes reindirizza il traffico tra il cluster Kubernetes connesso e il computer di sviluppo. Questo reindirizzamento del traffico consente il codice nel computer di sviluppo e i servizi in esecuzione nel cluster Kubernetes per comunicare come se fossero nello stesso cluster Kubernetes. Il processo locale con Kubernetes fornisce anche un modo per replicare le variabili di ambiente e i volumi montati disponibili per i Pod nel cluster Kubernetes nel computer di sviluppo. Fornire l'accesso alle variabili di ambiente e ai volumi montati nel computer di sviluppo consente di lavorare rapidamente sul codice senza dover replicare manualmente tali dipendenze.

> [!WARNING]
> Il processo locale per Kubernetes deve essere usato solo in scenari di sviluppo e test. Non è previsto né supportato per l'uso con cluster di produzione o servizi dinamici in uso attivo.

## <a name="using-local-process-with-kubernetes"></a>Uso del processo locale con Kubernetes

Per usare il processo locale con Kubernetes in Visual Studio, è necessario [Visual studio 2019][visual-studio] versione 16,7 Preview 4 o successiva in esecuzione in Windows 10 con il carico di lavoro *sviluppo ASP.NET e Web* installato e l' [estensione del processo locale Kubernetes][lpk-extension] installata. Quando si usa il processo locale con Kubernetes per stabilire una connessione al cluster Kubernetes, è possibile scegliere di reindirizzare tutto il traffico da e verso un pod esistente nel cluster al computer di sviluppo.

> [!NOTE]
> Quando si usa il processo locale con Kubernetes, viene richiesto il nome del servizio da reindirizzare al computer di sviluppo. Questa opzione è un modo pratico per identificare un pod per il reindirizzamento. Tutto il reindirizzamento tra il cluster Kubernetes e il computer di sviluppo è per un pod.

Quando il processo locale con Kubernetes stabilisce una connessione al cluster:

* Viene richiesto di configurare il servizio per sostituire il cluster, la porta nel computer di sviluppo da usare per il codice e l'attività di avvio per il codice come azione singola.
* Sostituisce il contenitore nel Pod nel cluster con un contenitore agente remoto che reindirizza il traffico al computer di sviluppo.
* Esegue [kubectl porta-in avanti][kubectl-port-forward] nel computer di sviluppo per l'invio del traffico dal computer di sviluppo all'agente remoto in esecuzione nel cluster.
* Raccoglie le informazioni sull'ambiente dal cluster utilizzando l'agente remoto. Queste informazioni sull'ambiente includono variabili di ambiente, servizi visibili, montaggi di volumi e montaggi di segreti.
* Configura l'ambiente in Visual Studio in modo che il servizio nel computer di sviluppo possa accedere alle stesse variabili come se fosse in esecuzione nel cluster.  
* Aggiorna il file degli host per eseguire il mapping dei servizi nel cluster agli indirizzi IP locali nel computer di sviluppo. Queste voci di file host consentono al codice in esecuzione nel computer di sviluppo di effettuare richieste ad altri servizi in esecuzione nel cluster. Per aggiornare il file degli host, il processo locale con Kubernetes chiederà l'accesso come amministratore nel computer di sviluppo quando si connette al cluster.
* Avvia l'esecuzione e il debug del codice nel computer di sviluppo. Se necessario, il processo locale con Kubernetes libererà le porte necessarie nel computer di sviluppo arrestando i servizi o i processi che attualmente utilizzano tali porte.

Dopo aver stabilito una connessione al cluster, è possibile eseguire ed eseguire il debug del codice in modo nativo nel computer, senza contenitori e il codice può interagire direttamente con il resto del cluster. Qualsiasi traffico di rete ricevuto dall'agente remoto viene reindirizzato alla porta locale specificata durante la connessione, in modo che il codice in esecuzione a livello nativo possa accettare ed elaborare tale traffico. Le variabili di ambiente, i volumi e i segreti del cluster vengono resi disponibili per il codice in esecuzione nel computer di sviluppo. Inoltre, a causa delle voci del file hosts e del Port porting aggiunto al computer di sviluppo da un processo locale con Kubernetes, il codice può inviare il traffico di rete ai servizi in esecuzione nel cluster usando i nomi di servizio del cluster e il traffico viene inoltrato ai servizi in esecuzione nel cluster. Il traffico viene instradato tra il computer di sviluppo e il cluster per l'intera durata della connessione.

Il processo locale con Kubernetes consente inoltre di replicare le variabili di ambiente e i file montati disponibili nei Pod del cluster nel computer di sviluppo tramite il `KubernetesLocalProcessConfig.yaml` file. È anche possibile usare questo file per creare nuove variabili di ambiente e montaggi del volume.

> [!NOTE]
> Per la durata della connessione al cluster (oltre a altri 15 minuti), il processo locale con Kubernetes esegue un processo denominato *EndpointManager* con autorizzazioni di amministratore sul computer locale.

## <a name="additional-configuration-with-kuberneteslocalprocessconfigyaml"></a>Configurazione aggiuntiva con KubernetesLocalProcessConfig. YAML

Il `KubernetesLocalProcessConfig.yaml` file consente di replicare le variabili di ambiente e i file montati disponibili per i Pod nel cluster. Per altre informazioni sulle opzioni di configurazione aggiuntive, vedere [configurare un processo locale con Kubernetes][using-config-yaml].

## <a name="using-routing-capabilities-for-developing-in-isolation"></a>Uso delle funzionalità di routing per lo sviluppo in isolamento

Per impostazione predefinita, il processo locale con Kubernetes reindirizza tutto il traffico per un servizio al computer di sviluppo. È anche possibile usare le funzionalità di routing per reindirizzare solo le richieste a un servizio originato da un sottodominio nel computer di sviluppo. Queste funzionalità di routing consentono di usare il processo locale con Kubernetes per lo sviluppo in isolamento ed evitare di interferire con altro traffico nel cluster.

L'animazione seguente mostra due sviluppatori che lavorano sullo stesso cluster in isolamento:

![GIF animata che illustra l'isolamento](media/local-process-kubernetes/lpk-graphic-isolated.gif)

Quando si Abilita l'uso in isolamento, il processo locale con Kubernetes esegue le operazioni seguenti oltre alla connessione al cluster Kubernetes:

* Verifica che il cluster Kubernetes non disponga Azure Dev Spaces abilitata.
* Replica il servizio scelto nel cluster nello stesso spazio dei nomi e aggiunge un'etichetta *routing.VisualStudio.io/Route-from=SERVICE_NAME* e *routing.VisualStudio.io/Route-on-header=kubernetes-route-As: GENERATED_NAME* annotazione.
* Configura e avvia gestione routing nello stesso spazio dei nomi nel cluster Kubernetes. Gestione routing utilizza un selettore di etichette per cercare l'etichetta *routing.VisualStudio.io/Route-from=SERVICE_NAME* e *routing.VisualStudio.io/Route-on-header=kubernetes-route-As: GENERATED_NAME* annotazione durante la configurazione del routing nello spazio dei nomi.

Se il processo locale con Kubernetes rileva che Azure Dev Spaces è abilitato nel cluster Kubernetes, viene richiesto di disabilitare Azure Dev Spaces prima di poter usare il processo locale con Kubernetes.

Quando viene avviato, gestione routing esegue le operazioni seguenti:
* Duplica tutti gli ingressi trovati nello spazio dei nomi utilizzando la *GENERATED_NAME* per il sottodominio. 
* Crea un pod di invio per ogni servizio associato a ingress duplicato con il sottodominio *GENERATED_NAME* .
* Crea un pod di invio aggiuntivo per il servizio su cui si sta lavorando in isolamento. Ciò consente di indirizzare le richieste con il sottodominio al computer di sviluppo.
* Configura le regole di routing per ogni pod di invio per gestire il routing per i servizi con il sottodominio.

Quando nel cluster viene ricevuta una richiesta con il sottodominio *GENERATED_NAME* , viene aggiunta un'intestazione *kubernetes-route-As = GENERATED_NAME* alla richiesta. I pod di invio gestiscono il routing della richiesta al servizio appropriato nel cluster. Se la richiesta viene indirizzata al servizio su cui si sta lavorando in isolamento, la richiesta viene reindirizzata al computer di sviluppo dall'agente remoto.

Quando nel cluster viene ricevuta una richiesta senza il sottodominio *GENERATED_NAME* , non viene aggiunta alcuna intestazione alla richiesta. I pod di invio gestiscono il routing della richiesta al servizio appropriato nel cluster. Se la richiesta viene instradata al servizio che viene sostituito, la richiesta viene invece indirizzata al servizio originale anziché all'agente remoto.

> [!IMPORTANT]
> Ogni servizio del cluster deve inoltrare l'intestazione *kubernetes-route-As = GENERATED_NAME* quando si effettuano richieste aggiuntive. Ad esempio, quando *servicea* riceve una richiesta, effettua una richiesta a *serviceB* prima di restituire una risposta. In questo esempio, *servicea* deve inoltrare l'intestazione *kubernetes-route-As = GENERATED_NAME* nella richiesta a *serviceB*. Alcuni linguaggi, ad esempio [ASP.NET][asp-net-header], possono avere metodi per la gestione della propagazione dell'intestazione.

Quando si esegue la disconnessione dal cluster, per impostazione predefinita il processo locale con Kubernetes rimuoverà tutti i pod di invio e il servizio duplicato. 

> Si noti Il servizio e la distribuzione di gestione routing rimarranno in esecuzione nello spazio dei nomi. Per rimuovere la distribuzione e il servizio, eseguire i comandi seguenti per lo spazio dei nomi.
>
> ```azurecli
> kubectl delete deployment routingmanager-deployment -n NAMESPACE
> kubectl delete service routingmanager-service -n NAMESPACE
> ```

## <a name="diagnostics-and-logging"></a>Diagnostica e registrazione

Quando si usa il processo locale con Kubernetes per la connessione al cluster, i log di diagnostica del cluster vengono registrati nella directory *temporanea* del computer di sviluppo nel *processo locale con* la cartella Kubernetes.

## <a name="limitations"></a>Limitazioni

Il processo locale con Kubernetes presenta le limitazioni seguenti:

* Il processo locale con Kubernetes reindirizza il traffico per un singolo servizio al computer di sviluppo. Non è possibile usare il processo locale con Kubernetes per reindirizzare più servizi nello stesso momento.
* Un servizio deve essere supportato da un singolo POD per potersi connettere a tale servizio. Non è possibile connettersi a un servizio con più POD, ad esempio un servizio con repliche.
* Un pod può avere un solo contenitore in esecuzione in tale Pod affinché il processo locale con Kubernetes possa connettersi. Il processo locale con Kubernetes non è in grado di connettersi ai servizi con Pod con contenitori aggiuntivi, ad esempio contenitori sidecar inseriti da mesh dei servizi.
* Il processo locale con Kubernetes richiede autorizzazioni elevate per l'esecuzione nel computer di sviluppo per modificare il file degli host.
* Il processo locale con Kubernetes non può essere usato in cluster con Azure Dev Spaces abilitata.

### <a name="local-process-with-kubernetes-and-clusters-with-azure-dev-spaces-enabled"></a>Processo locale con Kubernetes e cluster con Azure Dev Spaces abilitato

Non è possibile usare il processo locale con Kubernetes in un cluster con Azure Dev Spaces abilitata. Se si vuole usare il processo locale con Kubernetes in un cluster con Azure Dev Spaces abilitato, è necessario disabilitare Azure Dev Spaces prima di connettersi al cluster.

## <a name="next-steps"></a>Passaggi successivi

Per iniziare a usare il processo locale con Kubernetes per connettersi al computer di sviluppo locale al cluster, vedere [usare il processo locale con Kubernetes](local-process-kubernetes.md).

[asp-net-header]: https://www.nuget.org/packages/Microsoft.AspNetCore.HeaderPropagation/
[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-tmp-dir]: /azure/dev-spaces/troubleshooting#before-you-begin
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-latest
[local-process-kubernetes-vs]: local-process-kubernetes.md
[kubectl-port-forward]: https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#port-forward
[visual-studio]: https://visualstudio.microsoft.com/downloads/
[lpk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[using-config-yaml]: configure-local-process-with-kubernetes.md