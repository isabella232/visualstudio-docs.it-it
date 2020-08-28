---
title: 'Esercitazione su Docker-parte 9: eseguire la distribuzione nel cloud'
description: Distribuire un'app Docker in un servizio cloud per l'hosting.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 661f9f6833b5ac5d42aacde7f228b042bef00bb0
ms.sourcegitcommit: f4d734329c82f2c8005b36af4b2b5516d90e6c63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "89039140"
---
# <a name="deploy-to-the-cloud"></a>Eseguire la distribuzione nel cloud

Ora che l'app è stata eseguita localmente, è possibile iniziare a pensarne l'esecuzione nel cloud in modo che altri utenti possano accedervi e usarla. A tale scopo, si useranno i contesti docker. Un contesto è la posizione in cui si lavora attualmente con i contenitori. Al momento, è disponibile solo il contesto "predefinito", quindi è necessario aggiungere un cloud e distribuirvi l'app.

## <a name="create-your-cloud-context"></a>Creare il contesto cloud

1. Per iniziare, è possibile visualizzare i contesti esaminati nella sezione contesti del pannello docker:

   ![Mostra solo il contesto predefinito](media/defaultcontext.png)

Il contesto predefinito per il lavoro locale dovrebbe essere visibile solo.

1. Per eseguire la distribuzione nel cloud, è necessario creare un nuovo contesto di ACI, ma a tale scopo è necessario prima di tutto l'estensione dell'account Azure per l'autenticazione con Azure.

   ![Aggiunta dell'estensione di Azure](media/addazureextension.png)

Se non si ha già un account, sarà necessario configurare un account Azure.

1. A questo punto è possibile creare il nuovo contesto ACI. A tale scopo, fare clic sul pulsante con il segno più nella sezione **contesti** della visualizzazione docker.

   ![Creazione del contesto ACI](media/createnewcontext.png)

Verrà chiesto il gruppo di risorse in cui si vogliono eseguire questi contenitori. Selezionare un gruppo esistente usando i tasti di direzione oppure usare l'opzione predefinita per usare il nuovo gruppo.

![Selezione del gruppo di risorse](media/selectresourcegroup.png)

È ora possibile visualizzare l'elenco dei contesti ACI ed è possibile fare clic con il pulsante destro del mouse su di esso per impostarlo come contesto corrente/in uso:

![È possibile selezionare il nuovo contesto ACI](media/listofcontexts.png)

## <a name="run-containers-in-the-cloud"></a>Esegui i contenitori nel cloud

1. A questo punto, usare il contesto ACI ed eseguire il contenitore.

   ```bash
   docker context use myacicontext
   docker run  -dp 3000:3000 <username>/getting-started
   ```

1. Eseguendo questa operazione, è ora possibile esaminare il contenitore nel contesto.

   ![Contenitore in esecuzione nel contesto di ACI](media/contextcontainer.png)

1. Per verificare che funzioni correttamente, è possibile fare clic con il pulsante destro del mouse sul contenitore in esecuzione e scegliere **Visualizza nel browser**.

   ![Contenitore in ACI con IP pubblico](media/containerinaci.png)

È possibile osservare che il contenitore è in esecuzione in un IP pubblico e funziona correttamente.

1. A questo punto, è possibile esaminare il contenitore in esecuzione per verificarne il funzionamento. È possibile iniziare osservando i log dei contenitori:
 
 ```bash
   docker logs distracted-jackson
   ```

1. È anche possibile accedere al contenitore come si farebbe con un contenitore locale.
 
 ```bash
   docker exec -it distracted-jackson sh
   ```

1. Infine, per pulire lo spazio di lavoro e assicurarsi che non venga addebitato alcun costo per continuare a eseguire il contenitore di test, è possibile semplicemente fare clic con il pulsante destro del mouse sul contenitore in esecuzione e scegliere **Rimuovi**.

## <a name="recap"></a>Riepilogo

A questo punto, è stato eseguito il carico di lavoro e la distribuzione nel cloud è stata completata per la prima volta. È possibile eseguire tutte queste operazioni dalla riga di comando e dall'interno del contesto di ACI usando `docker run` e anche `docker compose up` per eseguire le applicazioni multicontenitore. Per altre informazioni sull'esecuzione dei contenitori nel cloud, vedere la [documentazione estesa sull'uso di ACI](https://docs.docker.com/engine/context/aci-integration/).

## <a name="next-steps"></a>Passaggi successivi

Continuare con l'esercitazione.

> [!div class="nextstepaction"]
> [Passaggi successivi](whats-next.md)
