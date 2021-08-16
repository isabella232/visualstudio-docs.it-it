---
title: Esercitazione su Docker - Novità
description: Vengono descritte le opzioni per l'estensione delle app Docker con l'orchestrazione, usando i progetti Cloud Native Computing Foundation.
ms.date: 08/06/2021
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-docker
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 831d7bdaaa93067f01178e98fcba9577ee248897da33f04c35e07e2d6c85b519
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121349105"
---
# <a name="whats-next"></a>Passaggi successivi

Anche se l'esercitazione è stata completata, sono ancora disponibili molte altre informazioni sui contenitori.
Non si appro fondono qui, ma di seguito sono disponibili alcune altre aree da esaminare.

## <a name="container-orchestration"></a>Orchestrazione dei contenitori

L'esecuzione di contenitori nell'ambiente di produzione è difficile. Non si vuole accedere a un computer ed eseguire semplicemente o `docker run` `docker-compose up` . Perché no? Che cosa accade se i contenitori si distondono? Come è possibile eseguire la scalabilità tra più computer? L'orchestrazione dei contenitori risolve questo problema. Strumenti come Kubernetes, Swarm, Nomad e AKS consentono di risolvere questo problema in modi leggermente diversi.

L'idea generale è che si dispone di "manager" che ricevono **lo stato previsto.** Questo stato potrebbe essere "Voglio eseguire due istanze dell'app Web ed esporre la porta 80". I responsabili osservano quindi tutti i computer del cluster e delegano il lavoro ai nodi "worker". I responsabili verificano le modifiche (ad esempio un contenitore che si chioda) e quindi lavorano per fare in modo che lo stato **effettivo** rifletta lo stato previsto.

## <a name="cloud-native-computing-foundation-projects"></a>Progetti di Cloud Native Computing Foundation

CNCF è una sede indipendente dal fornitore per vari progetti open source, tra cui Kubernetes, Prometheus, Envoy, Linkerd, NATS e altro ancora. È possibile visualizzare i [progetti con laurea e incubazione qui](https://www.cncf.io/projects/) e l'intero panorama [CNCF qui.](https://landscape.cncf.io/) Sono disponibili molti progetti che consentono di risolvere i problemi relativi a monitoraggio, registrazione, sicurezza, registri immagini, messaggistica e altro ancora.

Quindi, se non si ha una nuova versione del panorama dei contenitori e dello sviluppo di applicazioni native del cloud, benvenuti. Connettersi alla community, porre domande e continuare a imparare. Siamo molto contenti di averti.

## <a name="working-with-docker-in-vs-code"></a>Uso di Docker in VS Code

Altre informazioni sull'uso dell'VS Code Docker:

- [VS Code Panoramica dell'estensione Docker](https://code.visualstudio.com/docs/containers/overview)
- [Introduzione a Node.js](https://code.visualstudio.com/docs/containers/quickstart-node)
- [Introduzione a Python](https://code.visualstudio.com/docs/containers/quickstart-python)
- [Introduzione a .NET Core](https://code.visualstudio.com/docs/containers/quickstart-aspnet-core)
- [Eseguire il debug di app in contenitori](https://code.visualstudio.com/docs/containers/debug-common)
