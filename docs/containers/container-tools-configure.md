---
title: Configurare Visual Studio Container Tools
description: Configurare gli strumenti disponibili in Visual Studio per l'uso dei contenitori Docker.
author: ghogen
ms.author: ghogen
ms.topic: how-to
ms.date: 03/20/2019
ms.technology: vs-container-tools
ms.openlocfilehash: 91ed17af9900c068af7e81ce3902e68063814d82
ms.sourcegitcommit: 8f8804b885c3a68f20bf0e9fe3729f2764145815
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2021
ms.locfileid: "123096919"
---
# <a name="how-to-configure-visual-studio-container-tools"></a>Come configurare Visual Studio Container Tools

Usando Visual Studio, è possibile controllare alcuni aspetti del funzionamento di Visual Studio con i contenitori Docker, incluse le impostazioni che influiscono sulle prestazioni e sull'utilizzo delle risorse quando si usano i contenitori Docker.

## <a name="container-tools-settings"></a>Impostazioni di Strumenti contenitore

Dal menu principale scegliere **Strumenti > Opzioni** ed espandere **Strumenti contenitore > Impostazioni**. Vengono visualizzate le impostazioni degli strumenti contenitore.

::: moniker range="vs-2017"

![Visual Studio Opzioni di Strumenti contenitore, che mostrano: Eseguire automaticamente il pull delle immagini Docker necessarie al caricamento del progetto, Avviare automaticamente i contenitori in background, Uccidi automaticamente i contenitori alla chiusura della soluzione e Non richiedere l'attendibilità del certificato SSL.](./media/overview/visual-studio-docker-tools-options.png)
::: moniker-end

::: moniker range=">=vs-2019"

Impostazioni **generali** di Strumenti contenitore:

![Visual Studio Opzioni di Strumenti contenitore, che mostrano: Installare Docker Desktop, se necessario, e Considerare attendibile ASP.NET Core certificato SSL.](./media/configure-container-tools/tools-options-1.png)

Impostazioni **Project** contenitore **Docker Compose** contenitori:

![Visual Studio Opzioni di Strumenti contenitore, che mostrano: Uccidi contenitori alla chiusura del progetto, Esegui il pull delle immagini Docker necessarie all'apertura del progetto e Esegui contenitori all'apertura del progetto.](./media/configure-container-tools/tools-options-2.png)
::: moniker-end

La tabella seguente può essere utile per decidere come impostare queste opzioni.

::: moniker range="vs-2017"
| Nome | Impostazione predefinita | Si applica a | Descrizione |
| -----|:---------------:|:----------:| ----------- |
| Pull automatico delle immagini Docker richieste al caricamento del progetto | On | Modello di Docker Compose | Per ottenere migliori prestazioni durante il caricamento dei progetti, Visual Studio avvierà un'operazione di pull automatico di Docker in modo che quando si è pronti per eseguire il codice l'immagine sia già stata scaricata o in fase di download. Se si stanno semplicemente caricando progetti ed esplorando codice, è possibile disattivare questa opzione per evitare che vengano scaricate immagini del contenitore non necessarie. |
| Avvia automaticamente i contenitori in background | On | Modello di Docker Compose | Sempre per ottenere migliori prestazioni, Visual Studio crea un contenitore con punti di montaggio di volume pronti per quando viene compilato ed eseguito il contenitore. Se si vuole controllare quando viene creato il contenitore, disattivare questa opzione. |
| Termina automaticamente i contenitori alla chiusura della soluzione | On | Modello di Docker Compose | Disattivare questa opzione se si vuole che i contenitori della soluzione continuino a essere eseguiti dopo la chiusura della soluzione o di Visual Studio. |
| Non chiedere di considerare attendibile il certificato SSL per localhost | Off | ASP.NET Core 2.1 | Se il certificato SSL per localhost non è attendibile, Visual Studio lo richiederà ogni volta che si eseguirà il progetto, a meno che questa casella di controllo non sia selezionata. |
::: moniker-end

::: moniker range=">=vs-2019"

Nella tabella seguente vengono descritte **le impostazioni** generali:

| Nome | Impostazione predefinita | Si applica a | Descrizione |
| -----|:---------------:|:----------:| ----------- |
| Installare Docker Desktop, se necessario | Richiedi conferma | Singolo Project, Docker Compose | Scegliere se si vuole che venga richiesto se Docker Desktop non è installato. |
| Considerare attendibile ASP.NET Core certificato SSL | Richiedi conferma | ASP.NET Core Progetti 2.x | Se l'opzione **è impostata** su Richiedi conferma, se il certificato SSL localhost non è attendibile, Visual Studio ogni volta che si esegue il progetto. |

Nella tabella seguente vengono descritte **le Project** e **Docker Compose** seguenti:

| Nome | Impostazione predefinita | Si applica a | Descrizione |
| -----|:---------------:|:----------:| ----------- |
| Eseguire il pull delle immagini Docker necessarie all'apertura del progetto | Vero | Singolo Project, Docker Compose | Per ottenere migliori prestazioni durante il caricamento dei progetti, Visual Studio avvierà un'operazione di pull automatico di Docker in modo che quando si è pronti per eseguire il codice l'immagine sia già stata scaricata o in fase di download. Se si caricano solo progetti e si esplora il codice, è possibile impostare su **False** per evitare il download di immagini del contenitore non necessarie. |
| Eseguire il pull di immagini Docker aggiornate all'apertura del progetto | Progetti .NET Core | Singolo Project, Docker Compose | Quando si apre un progetto, verificare la disponibilità di aggiornamenti per le immagini e scaricarli, se disponibili. |
| Eseguire contenitori all'apertura del progetto | Vero | Singolo Project, Docker Compose | Anche in questo caso, Visual Studio un contenitore in anticipo in modo che sia pronto per la compilazione e l'esecuzione del contenitore. Se si vuole controllare quando viene creato il contenitore, impostare su **False**. |
| Rimuovere contenitori alla chiusura del progetto | Vero | Singolo Project, Docker Compose | Impostare su **False** se si desidera che i contenitori per la soluzione siano conservati dopo la chiusura della soluzione o la Visual Studio. |

Le **impostazioni della finestra degli strumenti** Contenitori controllano le impostazioni che si applicano alla finestra degli strumenti Contenitori, che mostra informazioni sui contenitori e sulle immagini Docker.  Vedere [Usare la finestra Contenitori](view-and-diagnose-containers.md)

![Visual Studio Opzioni di Strumenti contenitore, che mostra le impostazioni disponibili per la finestra degli strumenti Contenitori](media/configure-container-tools/tools-options-3.png)

La tabella seguente descrive le impostazioni **della finestra** Contenitori:


| NOME | Impostazione predefinita | Descrizione |
| -----|:---------------:| ----------- |
| Confermare prima di eliminare i contenitori | Always | Controlla se viene richiesto di eliminare i contenitori inutilizzati. |
| Confermare prima di eliminare le immagini | Always | Controlla se viene richiesto di eliminare le immagini inutilizzate. |
| Confermare prima di rimuovere un contenitore | Always | Controlla se viene richiesto quando si rimuove un contenitore. |
| Confermare prima di rimuovere un'immagine | Always | Controlla se viene richiesto quando si rimuove un'immagine. |
| Confermare prima di eseguire un numero elevato di immagini | Always | Controlla se viene richiesto prima di avviare i contenitori da più di 10 immagini alla volta. |

::: moniker-end
> [!WARNING]
> Se il certificato SSL localhost non è attendibile e si seleziona la casella per eliminare la richiesta, le richieste Web HTTPS potrebbero non riuscire in fase di esecuzione nell'app o nel servizio. In questo caso, deselezionare la casella di controllo **Non chiedere**, eseguire il progetto e indicare l'attendibilità al prompt.

## <a name="next-steps"></a>Passaggi successivi

Altre informazioni sull'uso dei contenitori in Visual Studio in questa [panoramica.](overview.md)