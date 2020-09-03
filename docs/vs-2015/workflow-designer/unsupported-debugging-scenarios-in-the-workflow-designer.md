---
title: Scenari di debug non supportati nel Progettazione flussi di lavoro | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
caps.latest.revision: 4
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fdbe68b416560b85580e3dd30e5f8138b7cd08fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72606932"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Scenari di debug non supportati in Progettazione flussi di lavoro
In Progettazione flussi di lavoro in [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] sono state aggiunte numerose e nuove funzionalità, ma sono ancora presenti alcuni scenari di debug non supportati. In questo documento vengono indicati gli scenari di debug non supportati in Progettazione flussi di lavoro.

- Impossibile continuare l'esecuzione dopo che il codice è stato modificato.

- Impossibile continuare l'esecuzione da un punto arbitrario nel flusso di lavoro (Imposta istruzione successiva).

- Impossibile continuare l'esecuzione fino a quando non si raggiunge il cursore (Esegui fino al cursore).

- Impossibile usare Progettazione flussi di lavoro per eseguire debug di flussi di lavoro creati in codice senza l'uso della finestra di progettazione.

- Impossibile eseguire il debug di flussi di lavoro creati in versioni precedenti di [!INCLUDE[wf](../includes/wf-md.md)] nella finestra di progettazione di [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)].

- Impossibile definire i punti di interruzione nei collegamenti tra attività o nodi <xref:System.Activities.Statements.Flowchart>.

- Gli Appunti non sono disponibili durante l'esecuzione del debug.

- I punti di interruzione non vengono mantenuti quando le attività vengono copiate o incollate.

- Impossibile impostare i punti di interruzione del flusso di lavoro nella finestra dello stack di chiamate.

- Quando si creano punti di interruzione nella finestra di progettazione, le impostazioni di **riga** e **carattere** nella finestra di dialogo nuovo punto di **interruzione** non vengono utilizzate.

- La finestra Punto di interruzione o il menu di scelta rapida non supporta le colonne o le opzioni seguenti per il debug del flusso di lavoro:

  - Condizione

  - Passaggi

  - Quando raggiunto

  - Funzione

  - Dati

  - Process

  - Vai a disassembly
