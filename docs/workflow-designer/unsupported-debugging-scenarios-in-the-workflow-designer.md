---
title: Scenari di debug non supportati in Progettazione flussi di lavoro
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 2b876df1b7d997f3999c119d02abd593a88e6d5e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31973070"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Scenari di debug non supportati in Progettazione flussi di lavoro

La finestra di progettazione del flusso di lavoro in .NET Framework 4 aggiunto numerose nuove funzionalità, ma sono ancora presenti alcuni scenari di debug non supportati.

Finestra di progettazione del flusso di lavoro non supportati gli scenari di debug sono i seguenti:

-   Impossibile continuare l'esecuzione dopo che il codice è stato modificato.

-   Impossibile continuare l'esecuzione da un punto arbitrario nel flusso di lavoro (Imposta istruzione successiva).

-   Impossibile continuare l'esecuzione fino a quando non si raggiunge il cursore (Esegui fino al cursore).

-   Impossibile usare Progettazione flussi di lavoro per eseguire debug di flussi di lavoro creati in codice senza l'uso della finestra di progettazione.

-   Impossibile eseguire il debug di flussi di lavoro creati in versioni precedenti di Windows Workflow Foundation (WF) nella finestra di progettazione di .NET Framework 4.

-   Impossibile definire i punti di interruzione nei collegamenti tra attività o nodi <xref:System.Activities.Statements.Flowchart>.

-   Gli Appunti non sono disponibili durante l'esecuzione del debug.

-   I punti di interruzione non vengono mantenuti quando le attività vengono copiate o incollate.

-   Impossibile impostare i punti di interruzione del flusso di lavoro nella finestra dello stack di chiamate.

-   Durante la creazione di punti di interruzione nella finestra di progettazione, il **riga** e **carattere** impostazioni di **nuovo punto di interruzione** finestra di dialogo non vengono utilizzati.

-   La finestra Punto di interruzione o il menu di scelta rapida non supporta le colonne o le opzioni seguenti per il debug del flusso di lavoro:

    -   Condizione

    -   Passaggi

    -   Quando raggiunto

    -   Funzione

    -   Dati

    -   Processo

    -   Vai a disassembly