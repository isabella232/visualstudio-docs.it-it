---
title: 'Esercitazione su Docker - Parte 10: Distribuire nel cloud'
description: Distribuire un'app Docker in un servizio cloud per l'hosting.
ms.date: 08/06/2021
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-docker
ms.custom: contperf-fy22q1
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: faa4fe632662a9e57ab6e39573a42ad4e3da4c97
ms.sourcegitcommit: f930bc28bdb0ba01d6f7cb48f229afecfa0c90cd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/18/2021
ms.locfileid: "122334493"
---
# <a name="deploy-to-the-cloud"></a>Distribuire nel cloud

Ora che l'app è stata eseguita in locale, è possibile iniziare a pensare di eseguirla nel cloud in modo che altri utenti possano accedervi e usarla. A tale scopo, si useranno i contesti Docker. Un contesto è la posizione in cui si lavora attualmente con i contenitori. Al momento è disponibile solo il contesto "predefinito", quindi sarà necessario aggiungerne uno cloud e distribuirvi l'app.

## <a name="create-your-cloud-context"></a>Creare il contesto cloud

1. Per iniziare, è possibile visualizzare i contesti che si hanno esaminando la sezione contesti del pannello Docker:

   ![Mostra solo il contesto predefinito](media/defaultcontext.png)

Verrà visualizzato solo il contesto predefinito per il lavoro locale.

1. Per eseguire la distribuzione nel cloud, è necessario creare un nuovo contesto ACI, ma a tale scopo, è prima necessario l'estensione dell'account Azure per l'autenticazione con Azure.

   ![Aggiunta dell'estensione di Azure](media/addazureextension.png)

Se non è già presente, è necessario configurare un account Azure.

1. È ora possibile creare il nuovo contesto ACI. A tale scopo, fare clic sul pulsante con il segno più nella **sezione** Contesti della visualizzazione Docker.

   ![Creazione del contesto ACI](media/createnewcontext.png)

Verrà chiesto in quale gruppo di risorse eseguire questi contenitori. Selezionare un gruppo esistente usando i tasti di direzione oppure usare l'opzione predefinita per usare il nuovo gruppo.

![Selezione del gruppo di risorse](media/selectresourcegroup.png)

È ora possibile visualizzare il contesto ACI elencato e fare clic con il pulsante destro del mouse per renderlo il contesto corrente attivo/in uso:

![È possibile selezionare un nuovo contesto ACI](media/listofcontexts.png)

## <a name="run-containers-in-the-cloud"></a>Eseguire contenitori nel cloud

1. A questo punto, usare il contesto ACI ed eseguire il contenitore.

   ```bash
   docker context use myacicontext
   docker run  -dp 3000:3000 <username>/getting-started
   ```

1. Dopo aver eseguito questa operazione, esaminare ora il contenitore nel contesto.

   ![Contenitore in esecuzione nel contesto ACI](media/contextcontainer.png)

1. Per verificare che tutto funzioni correttamente, è possibile fare clic con il pulsante destro del mouse sul contenitore in esecuzione e **scegliere Visualizza nel browser**.

   ![Contenitore in ACI con IP pubblico](media/containerinaci.png)

È anche possibile vedere che il contenitore è in esecuzione in un indirizzo IP pubblico e funziona correttamente.

1. A questo punto, è possibile esaminare il contenitore in esecuzione per verificare il funzionamento. Per iniziare, esaminare i log dei contenitori:
 
 ```bash
   docker logs distracted-jackson
   ```

1. È anche possibile eseguire l'exec nel contenitore come si farebbe con un contenitore locale.
 
 ```bash
   docker exec -it distracted-jackson sh
   ```

1. Infine, per pulire lo spazio di lavoro e assicurarsi che non vengano addebitati costi per continuare a eseguire il contenitore di test, è sufficiente fare clic con il pulsante destro del mouse sul contenitore in esecuzione e scegliere **Rimuovi**.

## <a name="recap"></a>Riepilogo

Il carico di lavoro è stato quindi distribuito correttamente nel cloud per la prima volta. È possibile eseguire tutte queste operazioni anche dalla riga di comando all'interno del contesto ACI usando e anche usando per eseguire `docker run` `docker compose up` le applicazioni multi-contenitore. Per altre informazioni sull'esecuzione dei contenitori nel cloud, leggere la documentazione [estesa sull'uso di ACI](https://docs.docker.com/engine/context/aci-integration/).

## <a name="next-steps"></a>Passaggi successivi

Continuare con l'esercitazione.

> [!div class="nextstepaction"]
> [Novità](whats-next.md)
