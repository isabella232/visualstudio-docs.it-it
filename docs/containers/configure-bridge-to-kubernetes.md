---
title: Uso di KubernetesLocalProcessConfig. YAML per una configurazione aggiuntiva con per Bridge a Kubernetes
services: azure-dev-spaces
ms.date: 07/28/2020
ms.topic: conceptual
description: Descrive le opzioni di configurazione aggiuntive per Bridge to Kubernetes usando KubernetesLocalProcessConfig. YAML
keywords: Bridge to Kubernetes, Azure Dev Spaces, dev Spaces, Docker, Kubernetes, Azure, AKS, Azure Kubernetes Service, container
monikerRange: '>=vs-2019'
author: ghogen
ms.author: ghogen
manager: jmartens
ms.openlocfilehash: b250454fe5e80ec18f75add92c8c2f653893e994
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867620"
---
# <a name="configure-bridge-to-kubernetes"></a>Configurare Bridge per Kubernetes

Il `KubernetesLocalProcessConfig.yaml` file consente di replicare le variabili di ambiente e i file montati disponibili per i Pod nel cluster AKS. È possibile specificare le azioni seguenti in un `KubernetesLocalProcessConfig.yaml` file:

* Scaricare un volume e impostare il percorso di tale volume come variabile di ambiente.
* Rendere il servizio in esecuzione nel cluster disponibile per i processi in esecuzione nel computer di sviluppo.
* Creare una variabile di ambiente con un valore costante.

Un `KubernetesLocalProcessConfig.yaml` file predefinito non viene creato automaticamente, pertanto è necessario creare manualmente il file nella radice del progetto.

## <a name="download-a-volume"></a>Scaricare un volume

In *ENV* specificare un *nome* e un *valore* per ogni volume da scaricare. Il *nome* è la variabile di ambiente che verrà usata nel computer di sviluppo. Il *valore* è il nome del volume e un percorso nel computer di sviluppo. Il valore per *value* assume il formato *$ (volumeMounts: VOLUME_NAME)/path/to/files*.

Ad esempio:

```yaml
version: 0.1
env:
  - name: ALLOW_LIST_PATH
    value: $(volumeMounts:allow-list)/allow-list
```

Nell'esempio precedente viene scaricato il volume *allow-list* dal contenitore e viene impostato tale percorso più il percorso della variabile di ambiente *ALLOW_LIST_PATH*. Il comportamento predefinito prevede il download dei file nel percorso specificato in una directory temporanea nel computer di sviluppo. Nell'esempio precedente *ALLOW_LIST_PATH* è impostato su `/TEMPORARY_DIR/allow-list` . 

> [!NOTE]
> Il download di un volume scaricherà l'intero contenuto di tale volume indipendentemente dal percorso impostato. Il percorso viene utilizzato solo per impostare la variabile di ambiente per l'utilizzo nel computer di sviluppo. L'aggiunta di */allow-list* o */path/to/files* alla fine del token non influisce effettivamente sulla posizione in cui il volume è persistente. La variabile di ambiente è semplicemente una praticità nel caso in cui l'app necessiti di un riferimento a un file specifico all'interno di tale volume.

È anche possibile specificare un percorso per scaricare il montaggio del volume nel computer di sviluppo anziché usare una directory temporanea. In *volumeMounts* specificare un *nome* e un *LocalPath* per ogni percorso specifico. Il *nome* è il nome del volume di cui si desidera trovare una corrispondenza, mentre *LocalPath* è il percorso assoluto nel computer di sviluppo. Ad esempio:

```yaml
version: 0.1
volumeMounts:
  - name: default-token-*
    localPath: /var/run/secrets/kubernetes.io/serviceaccount
env:
  - name: KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE
    value: $(volumeMounts:default-token-*)
```

Nell'esempio precedente viene usata la voce in *ENV* per scaricare un volume corrispondente a un *\* token predefinito*, ad esempio *default-token-1111* o *default-token-1234-5678-90abcdef*. Nei casi in cui più volumi corrispondono, viene utilizzato il primo volume corrispondente. Tutti i file vengono scaricati nel `/var/run/secrets/kubernetes.io/serviceaccount` computer di sviluppo usando la voce in *volumeMounts*. La variabile di ambiente *KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE* è impostata su `/var/run/secrets/kubernetes.io/serviceaccount` .

## <a name="make-a-service-available"></a>Rendere disponibile un servizio

In *ENV* specificare un *nome* e un *valore* per ogni servizio che si desidera rendere disponibile nel computer di sviluppo. Il *nome* è la variabile di ambiente che verrà usata nel computer di sviluppo. Il *valore* è il nome del servizio del cluster e un percorso. Il valore per *value* assume il formato *$ (Services: SERVICE_NAME)/path*.

Ad esempio:

```yaml
version: 0.1
env:
  - name: MYAPP1_SERVICE_HOST
    value: $(services:myapp1)/api/v1/
```

L'esempio precedente rende disponibile il servizio *MyApp1* per il computer di sviluppo e la variabile di ambiente *MYAPP1_SERVICE_HOST* è impostata sull'indirizzo IP locale del servizio *MyApp1* con il `/api/v1` percorso (ovvero `127.1.1.4/api/v1` ). Il servizio *MyApp1* è accessibile tramite la variabile di ambiente, *MyApp1* o *MyApp1. svc. cluster. local*.

> [!NOTE]
> Rendendo disponibile un servizio nel computer di sviluppo, l'intero servizio viene reso disponibile indipendentemente dal percorso impostato. Il percorso viene utilizzato solo per impostare la variabile di ambiente per l'utilizzo nel computer di sviluppo.
È anche possibile rendere disponibile un servizio da uno spazio dei nomi Kubernetes specifico usando *$ (Services: SERVICE_NAME. NAMESPACE_NAME)*. Ad esempio:

```yaml
version: 0.1
env:
  - name: MYAPP2_SERVICE_HOST
    value: $(services:myapp2.mynamespace)
```

L'esempio precedente rende *MyApp2* *lo spazio dei nomi MyNamespace* disponibile nel computer di sviluppo e imposta la variabile di ambiente *MYAPP2_SERVICE_HOST* sull'indirizzo IP locale di *MyApp2* *dallo spazio dei nomi MyNamespace* .

## <a name="create-an-environment-variable-with-a-constant-value"></a>Creare una variabile di ambiente con un valore costante

In *ENV* specificare un *nome* e un *valore* per ogni variabile di ambiente che si desidera creare nel computer di sviluppo. Il *nome* è la variabile di ambiente che verrà usata nel computer di sviluppo e il *valore* è il valore. Ad esempio:

```yaml
version: 0.1
env:
  - name: DEBUG_MODE
    value: "true"
```

Nell'esempio precedente viene creata una variabile di ambiente denominata *debug_mode* con un valore *true*.

## <a name="example-kuberneteslocalprocessconfigyaml"></a>Esempio di KubernetesLocalProcessConfig. YAML

Di seguito è riportato un esempio di un `KubernetesLocalProcessConfig.yaml` file completo:

```yaml
version: 0.1
volumeMounts:
  - name: default-token-*
    localPath: /var/run/secrets/kubernetes.io/serviceaccount
env:
  - name: KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE
    value: $(volumeMounts:default-token-*)
  - name: ALLOW_LIST_PATH
    value: $(volumeMounts:allow-list)/allow-list
  - name: MYAPP1_SERVICE_HOST
    value: $(services:myapp1)/api/v1/
  - name: MYAPP2_SERVICE_HOST
    value: $(services:myapp2.mynamespace)
  - name: DEBUG_MODE 
    value: "true"
```

## <a name="next-steps"></a>Passaggi successivi

Per iniziare a usare Bridge per Kubernetes per connettersi al computer di sviluppo locale al cluster, vedere [usare Bridge per Kubernetes con Visual Studio Code][bridge-to-kubernetes-vs-code] e [usare Bridge per Kubernetes con Visual Studio][bridge-to-kubernetes-vs].

[bridge-to-kubernetes-vs-code]: https://code.visualstudio.com/docs/containers/bridge-to-kubernetes
[bridge-to-kubernetes-vs]: bridge-to-kubernetes.md
