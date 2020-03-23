---
title: Configurare gli strumenti contenitore di Visual StudioConfigure Visual Studio Container Tools
description: Configurare gli strumenti disponibili in Visual Studio per l'utilizzo dei contenitori Docker.Configure the tools available in Visual Studio for working with Docker containers.
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: 0ae81ed19a7fa8a967a3f9c3fe83c9f0d9e3ae51
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "73188781"
---
# <a name="how-to-configure-visual-studio-container-tools"></a>Come configurare Visual Studio Container Tools

Utilizzando le impostazioni di Visual Studio, è possibile controllare alcuni aspetti del funzionamento di Visual Studio con i contenitori Docker, incluse le impostazioni che influiscono sulle prestazioni e sull'utilizzo delle risorse quando si utilizzano i contenitori Docker.Using Visual Studio settings, you can control some aspects of how Visual Studio works with Docker containers, including settings that affect performance and resource usage when working with Docker containers.

## <a name="container-tools-settings"></a>Impostazioni degli strumenti contenitore

Dal menu principale scegliere **Strumenti > Opzioni** ed espandere **Strumenti contenitore > Impostazioni**. Vengono visualizzate le impostazioni degli strumenti contenitore.

::: moniker range="vs-2017"

![Opzioni di Visual Studio Container Tools, che mostrano: estrai automaticamente le immagini Docker necessarie al caricamento del progetto, avvia automaticamente i contenitori in background, uccidi automaticamente i contenitori alla chiusura della soluzione e Non richiedere l'attendibilità del certificato SSL.](./media/overview/visual-studio-docker-tools-options.png)
::: moniker-end

::: moniker range=">=vs-2019"

Impostazioni generali di Strumenti **contenitore:**

![Opzioni di Visual Studio Container Tools, che mostrano: Installa Docker Desktop se necessario e Attendibilità ASP.NET certificato SSL di base.](./media/configure-container-tools/tools-options-1.png)

Impostazioni **di** composizione progetto singolo e Docker di Strumenti contenitore:Container Tools Single Project and **Docker Compose** settings:

![Opzioni di Visual Studio Container Tools, mostrando: Elimina contenitori alla chiusura del progetto, Pull richiesto Docker immagini all'apertura del progetto e Esegui contenitori all'apertura del progetto.](./media/configure-container-tools/tools-options-2.png)
::: moniker-end

La tabella seguente può essere utile per decidere come impostare queste opzioni.

::: moniker range="vs-2017"
| Nome | Impostazione predefinita | Si applica a | Descrizione |
| -----|:---------------:|:----------:| ----------- |
| Pull automatico delle immagini Docker richieste al caricamento del progetto | Attivato | Modello di Docker Compose | Per ottenere migliori prestazioni durante il caricamento dei progetti, Visual Studio avvierà un'operazione di pull automatico di Docker in modo che quando si è pronti per eseguire il codice l'immagine sia già stata scaricata o in fase di download. Se si stanno semplicemente caricando progetti ed esplorando codice, è possibile disattivare questa opzione per evitare che vengano scaricate immagini del contenitore non necessarie. |
| Avvia automaticamente i contenitori in background | Attivato | Modello di Docker Compose | Sempre per ottenere migliori prestazioni, Visual Studio crea un contenitore con punti di montaggio di volume pronti per quando viene compilato ed eseguito il contenitore. Se si vuole controllare quando viene creato il contenitore, disattivare questa opzione. |
| Termina automaticamente i contenitori alla chiusura della soluzione | Attivato | Modello di Docker Compose | Disattivare questa opzione se si vuole che i contenitori della soluzione continuino a essere eseguiti dopo la chiusura della soluzione o di Visual Studio. |
| Non chiedere di considerare attendibile il certificato SSL per localhost | Disattivato | progetti ASP.NET Core 2.1 | Se il certificato SSL per localhost non è attendibile, Visual Studio lo richiederà ogni volta che si eseguirà il progetto, a meno che questa casella di controllo non sia selezionata. |
::: moniker-end

::: moniker range=">=vs-2019"

Nella tabella seguente vengono descritte le impostazioni **generali:**

| Nome | Impostazione predefinita | Si applica a | Descrizione |
| -----|:---------------:|:----------:| ----------- |
| Installare Docker Desktop se necessario | Chiedi conferma | Progetto singolo, Docker Compose | Scegliere se si desidera che venga richiesto se Docker Desktop non è installato. |
| Attendibilità ASP.NET certificato SSL di base | Chiedi conferma | ASP.NET core 2.x | Se è impostata su **Chiedi conferma**, se il certificato SSL localhost non è attendibile, Visual Studio ogni volta che si esegue il progetto. |

Nella tabella seguente vengono descritte le impostazioni **Progetto singolo** e **Composizione Docker:**

| Nome | Impostazione predefinita | Si applica a | Descrizione |
| -----|:---------------:|:----------:| ----------- |
| Estrarre le immagini Docker necessarie all'apertura del progetto | True  | Progetto singolo, Docker Compose | Per ottenere migliori prestazioni durante il caricamento dei progetti, Visual Studio avvierà un'operazione di pull automatico di Docker in modo che quando si è pronti per eseguire il codice l'immagine sia già stata scaricata o in fase di download. Se stai solo caricando progetti e sfogliando il codice, puoi impostare **su False** per evitare di scaricare le immagini del contenitore che non ti servono. |
| Eseguire contenitori all'apertura del progettoRun containers on project open | True  | Progetto singolo, Docker Compose | Anche in questo caso per migliorare le prestazioni, Visual Studio crea un contenitore in anticipo in modo che sia pronto per quando si compila ed esegue il contenitore. Se si desidera controllare quando viene creato il contenitore, impostare **su False**. |
| Interrompere i contenitori alla chiusura del progettoStop containers on project close | True  | Singolo progetto e Docker Compose | Impostare **su False** se si desidera che i contenitori per la soluzione continuino a essere eseguiti dopo la chiusura della soluzione o la chiusura di Visual Studio. |

::: moniker-end
> [!WARNING]
> Se il certificato SSL localhost non è attendibile e si seleziona la casella per eliminare i messaggi di richiesta, le richieste Web HTTPS potrebbero non riuscire in fase di esecuzione nell'app o nel servizio. In questo caso, deselezionare la casella di controllo **Non chiedere**, eseguire il progetto e indicare l'attendibilità al prompt.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sull'uso dei contenitori in Visual Studio, vedere questa [panoramica.](overview.md)