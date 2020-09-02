---
title: Esercitazione su Docker-passaggi successivi
description: Descrive le opzioni per estendere le app Docker con l'orchestrazione, usando i progetti cloud native Computing Foundation.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: f93185641a0814797b66eae90714e04cac83f7e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "89178288"
---
# <a name="whats-next"></a>Passaggi successivi

Anche se l'esercitazione è stata eseguita, c'è ancora molto altro da scoprire sui contenitori.
Non verrà approfondita questa procedura, ma di seguito sono elencate alcune altre aree da esaminare.

## <a name="container-orchestration"></a>Orchestrazione dei contenitori

L'esecuzione dei contenitori nell'ambiente di produzione è difficile. Non si vuole accedere a un computer ed eseguire semplicemente un `docker run` o `docker-compose up` . Perché no? Bene, cosa accade se i contenitori muoiono? In che modo è possibile eseguire la scalabilità tra più computer? L'orchestrazione del contenitore risolve questo problema. Strumenti come Kubernetes, Swarm, Nomad e AKS contribuiscono a risolvere questo problema, in modo leggermente diverso.

L'idea generale è che i "Manager" ricevono **lo stato previsto**. Questo stato potrebbe essere "Voglio eseguire due istanze dell'app Web ed esporre la porta 80". I manager esaminano quindi tutti i computer del cluster e delegano il lavoro ai nodi "worker". I manager controllano le modifiche (ad esempio, l'uscita da un contenitore) e quindi il lavoro per fare in modo che lo stato **effettivo** rispecchi lo stato previsto.

## <a name="cloud-native-computing-foundation-projects"></a>Progetti cloud native Computing Foundation

CNCF è una casa indipendente dal fornitore per diversi progetti open source, tra cui Kubernetes, Prometeo, emissario, Linkerd, NAT e altro ancora. Qui è possibile visualizzare i [progetti laureati e incubati](https://www.cncf.io/projects/) e l'intero [panorama CNCF qui](https://landscape.cncf.io/). Sono disponibili numerosi progetti che consentono di risolvere i problemi relativi al monitoraggio, alla registrazione, alla sicurezza, ai registri immagini, alla messaggistica e altro ancora.

Se non si ha familiarità con il paesaggio del contenitore e lo sviluppo di applicazioni native del cloud, Benvenuti! Contatta la community, fai domande e continua a imparare! Siamo entusiasti.

## <a name="working-with-docker-in-vs-code"></a>Uso di Docker in VS Code

Altre informazioni sull'uso dell'estensione Docker VS Code:

- [Panoramica dell'estensione Docker VS Code](https://code.visualstudio.com/docs/containers/overview)
- [Inizia a usare Node.js](https://code.visualstudio.com/docs/containers/quickstart-node)
- [Introduzione a Python](https://code.visualstudio.com/docs/containers/quickstart-python)
- [Introduzione a .NET Core](https://code.visualstudio.com/docs/containers/quickstart-aspnet-core)
- [Eseguire il debug di app in contenitori](https://code.visualstudio.com/docs/containers/debug-common)
