---
title: Esercitazione su Docker - Passaggi successivi
description: Descrive le opzioni per estendere le app Docker con l'orchestrazione, usando i progetti Cloud Native Computing Foundation.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: e777d80f44c9a11e4d2a893c968d33e348ca442a
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222695"
---
# <a name="whats-next"></a>Passaggi successivi

Anche se l'esercitazione è stata completata, sono ancora disponibili molte altre informazioni sui contenitori.
In questo caso non verranno approfondite le attività, ma di seguito sono disponibili alcune altre aree.

## <a name="container-orchestration"></a>Orchestrazione dei contenitori

L'esecuzione di contenitori nell'ambiente di produzione è difficile. Non si vuole accedere a un computer ed eseguire semplicemente o `docker run` `docker-compose up` . Perché no? Che cosa accade se i contenitori non vengono più esere? Come è possibile eseguire la scalabilità tra più computer? L'orchestrazione dei contenitori risolve questo problema. Strumenti come Kubernetes, Swarm, Nomad e servizio Kubernetes consentono di risolvere questo problema in modi leggermente diversi.

L'idea generale è che si dispone di "manager" che ricevono **lo stato previsto**. Questo stato potrebbe essere "Voglio eseguire due istanze dell'app Web ed esporre la porta 80". I responsabili quindi osservano tutti i computer del cluster e delegano il lavoro ai nodi "worker". I responsabili verificano le modifiche , ad esempio la chiusura di un contenitore, e quindi lavorano per fare in modo che lo stato effettivo **rifletta** lo stato previsto.

## <a name="cloud-native-computing-foundation-projects"></a>Progetti Cloud Native Computing Foundation

CNCF è una home page indipendente dal fornitore per vari progetti open source, tra cui Kubernetes, Prometheus, Envoy, Linkerd, NATS e altro ancora. È possibile visualizzare i [progetti graduali e incubati qui](https://www.cncf.io/projects/) e l'intero panorama [CNCF qui](https://landscape.cncf.io/). Sono disponibili molti progetti che consentono di risolvere i problemi relativi a monitoraggio, registrazione, sicurezza, registri immagini, messaggistica e altro ancora.

Pertanto, se non si ha di nuovo il panorama applicativo dei contenitori e lo sviluppo di applicazioni native del cloud, benvenuti. È possibile connettersi alla community, porre domande e continuare a imparare. Siamo molto contenti di averti.

## <a name="working-with-docker-in-vs-code"></a>Uso di Docker in VS Code

Altre informazioni sull'uso dell'VS Code Docker:

- [VS Code Panoramica dell'estensione Docker](https://code.visualstudio.com/docs/containers/overview)
- [Introduzione a Node.js](https://code.visualstudio.com/docs/containers/quickstart-node)
- [Introduzione a Python](https://code.visualstudio.com/docs/containers/quickstart-python)
- [Introduzione a .NET Core](https://code.visualstudio.com/docs/containers/quickstart-aspnet-core)
- [Eseguire il debug di app in contenitori](https://code.visualstudio.com/docs/containers/debug-common)
