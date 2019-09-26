---
title: Configurare gli strumenti di Visual Studio container
description: Configurare gli strumenti disponibili in Visual Studio per l'uso di contenitori docker.
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: f05eb5d92c0cdaa1242f0d98c3d877eebae27bb1
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253183"
---
# <a name="how-to-configure-visual-studio-container-tools"></a>Come configurare Visual Studio container Tools

Usando le impostazioni di Visual Studio, è possibile controllare alcuni aspetti del funzionamento di Visual Studio con i contenitori Docker, incluse le impostazioni che influiscono sulle prestazioni e sull'utilizzo delle risorse quando si lavora con i contenitori docker.

## <a name="container-tools-settings"></a>Impostazioni degli strumenti contenitore

Dal menu principale scegliere **Strumenti > Opzioni** ed espandere **Strumenti contenitore > Impostazioni**. Vengono visualizzate le impostazioni degli strumenti contenitore.

::: moniker range="vs-2017"

![Opzioni di Visual Studio container Tools, che mostra: Pull automatico delle immagini Docker richieste al caricamento del progetto, Avvia automaticamente i contenitori in background, Termina automaticamente i contenitori alla chiusura della soluzione e Non chiedere di considerare attendibile il certificato SSL per localhost.](./media/overview/visual-studio-docker-tools-options.png)
::: moniker-end

::: moniker range=">=vs-2019"

Impostazioni **generali** degli strumenti contenitore:

![Opzioni di Visual Studio container Tools, che mostra: Installare Docker desktop se necessario e considerare attendibile ASP.NET Core certificato SSL.](./media/configure-container-tools/tools-options-1.png)

Impostazioni del **singolo progetto** e del **Docker compose** di strumenti contenitore:

![Opzioni di Visual Studio container Tools, che mostra: Terminare i contenitori alla chiusura del progetto, estrarre le immagini Docker necessarie nel progetto aperto ed eseguire i contenitori nel progetto aperto.](./media/configure-container-tools/tools-options-2.png)
::: moniker-end

La tabella seguente può essere utile per decidere come impostare queste opzioni.

::: moniker range="vs-2017"
| nome | Impostazione predefinita | Si applica a | Descrizione |
| -----|:---------------:|:----------:| ----------- |
| Pull automatico delle immagini Docker richieste al caricamento del progetto | Attivato | Docker Compose | Per ottenere migliori prestazioni durante il caricamento dei progetti, Visual Studio avvierà un'operazione di pull automatico di Docker in modo che quando si è pronti per eseguire il codice l'immagine sia già stata scaricata o in fase di download. Se si stanno semplicemente caricando progetti ed esplorando codice, è possibile disattivare questa opzione per evitare che vengano scaricate immagini del contenitore non necessarie. |
| Avvia automaticamente i contenitori in background | Attivato | Docker Compose | Sempre per ottenere migliori prestazioni, Visual Studio crea un contenitore con punti di montaggio di volume pronti per quando viene compilato ed eseguito il contenitore. Se si vuole controllare quando viene creato il contenitore, disattivare questa opzione. |
| Termina automaticamente i contenitori alla chiusura della soluzione | Attivato | Docker Compose | Disattivare questa opzione se si vuole che i contenitori della soluzione continuino a essere eseguiti dopo la chiusura della soluzione o di Visual Studio. |
| Non chiedere di considerare attendibile il certificato SSL per localhost | Disattivato | Progetti ASP.NET Core 2,1 | Se il certificato SSL per localhost non è attendibile, Visual Studio lo richiederà ogni volta che si eseguirà il progetto, a meno che questa casella di controllo non sia selezionata. |
::: moniker-end

::: moniker range=">=vs-2019"

Nella tabella seguente vengono descritte le impostazioni **generali** :

| nome | Impostazione predefinita | Si applica a | Descrizione |
| -----|:---------------:|:----------:| ----------- |
| Installare Docker desktop se necessario | Richiedi | Progetto singolo, Docker Compose | Scegliere se si vuole che venga richiesto se Docker desktop non è installato. |
| Attendibilità ASP.NET Core certificato SSL | Richiedi | Progetti ASP.NET Core 2. x | Quando l'opzione è impostata su **Richiedi conferma**, se il certificato SSL localhost non è attendibile, Visual Studio richiederà ogni volta che viene eseguito il progetto. |

Nella tabella seguente vengono descritte le impostazioni di **singoli progetti** e **Docker compose** :

| nome | Impostazione predefinita | Si applica a | Descrizione |
| -----|:---------------:|:----------:| ----------- |
| Estrai le immagini Docker necessarie nel progetto aperto | True | Progetto singolo, Docker Compose | Per ottenere migliori prestazioni durante il caricamento dei progetti, Visual Studio avvierà un'operazione di pull automatico di Docker in modo che quando si è pronti per eseguire il codice l'immagine sia già stata scaricata o in fase di download. Se si stanno caricando solo progetti ed esplorando il codice, è possibile impostare su **false** per evitare di scaricare le immagini del contenitore non necessarie. |
| Esegui contenitori nel progetto aperto | True | Progetto singolo, Docker Compose | Per migliorare le prestazioni, Visual Studio crea un contenitore in anticipo in modo che sia pronto per la compilazione e l'esecuzione del contenitore. Se si vuole controllare quando viene creato il contenitore, impostare su **false**. |
| Arresta contenitori alla chiusura del progetto | True | Progetto singolo e Docker Compose | Impostare su **false** se si desidera che i contenitori della soluzione continuino a essere eseguiti dopo la chiusura della soluzione o la chiusura di Visual Studio. |

::: moniker-end
> [!WARNING]
> Se il certificato SSL localhost non è attendibile e si seleziona la casella per non visualizzare la richiesta, le richieste Web HTTPS potrebbero non riuscire in fase di esecuzione nell'app o nel servizio. In questo caso, deselezionare la casella di controllo **Non chiedere**, eseguire il progetto e indicare l'attendibilità al prompt.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sull'uso dei contenitori in Visual Studio, vedere questa [Panoramica](visual-studio-tools-for-docker.md).