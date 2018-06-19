---
title: Finestra di progettazione del flusso di lavoro - debug dei flussi di lavoro Legacy
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 33a8358c5d62b938fc64d608c9b4546ab1745aaa
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970377"
---
# <a name="debugging-legacy-workflows"></a>Debug dei flussi di lavoro legacy

Se si utilizza Progettazione flussi di lavoro Windows legacy in Visual Studio per compilare le applicazioni di Windows Workflow Foundation (WF) che scegliere.NET Framework 3.0 o 3.5, è possibile eseguire il debug dei flussi di lavoro come con qualsiasi altro programma impostando punti di interruzione, connessione a processi, ed esaminando i thread e lo stack di chiamate. È inoltre possibile eseguire il debug in modalità remota.

> [!NOTE]
> Se più versioni di Visual Studio vengono installate e disinstallate sul computer, il debug WF3 potrebbe non riuscire per una delle due seguenti cause:
>
> -   I punti di interruzione non vengono rilevati.
> -   Viene visualizzato il seguente messaggio:
>
> **Impossibile avviare il debug sul server web. Il debugger non è installato correttamente.  Impossibile eseguire il debug del tipo di codice richiesto.  Eseguire il programma di installazione per installare o ripristinare il debugger.**
>
> Se uno di questi scenari si verifica durante il debug dei flussi di lavoro .NET Framework 3.0 o 3.5, eseguire un ripristino dell'installazione di Visual Studio.

 Windows Workflow Foundation si integra con le finestre di debug di Visual Studio standard seguenti:

-   **Punto di interruzione**: funziona come previsto, ma si specifica un'attività per il nome della funzione.

-   **Stack di chiamate**: modificato per fornire una struttura delle attività eseguite in un'istanza del flusso di lavoro. Le voci di **Stack di chiamate** finestra sono una ricerca approfondita di attività in esecuzione. È possibile fare doppio clic su una voce per selezionare l’attività desiderata.

-   **Thread**: fornisce l'ID istanza dell'istanza del flusso di lavoro che viene eseguito il debug.

 Visual Studio per Windows Workflow Foundation non supporta le funzionalità di debug seguenti:

-   Punti di interruzione condizionali nell'area di progettazione.

-   Controllo immediato.

-   Imposta istruzione successiva.

-   Esegui fino al cursore.

-   Modifica e continuazione.

-   Debug JIT.

-   Debug in modalità mista.