---
title: Scenari di debug non supportati in Progettazione flussi di lavoro
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 9cda710a3a2f4945e96e706479996da0a1fa7e12
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825739"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Scenari di debug non supportati in Progettazione flussi di lavoro

La finestra di progettazione del flusso di lavoro non supporta i seguenti scenari di debug:

- Impossibile continuare l'esecuzione dopo che il codice è stato modificato.

- Impossibile continuare l'esecuzione da un punto arbitrario nel flusso di lavoro (Imposta istruzione successiva).

- Impossibile continuare l'esecuzione fino a quando non si raggiunge il cursore (Esegui fino al cursore).

- Impossibile usare Progettazione flussi di lavoro per eseguire debug di flussi di lavoro creati in codice senza l'uso della finestra di progettazione.

- I flussi di lavoro creati in versioni precedenti di Windows Workflow Foundation (WF) non è possibile eseguire il debug in .NET Framework 4 o versione successiva.

- Impossibile definire i punti di interruzione nei collegamenti tra attività o nodi <xref:System.Activities.Statements.Flowchart>.

- Gli Appunti non sono disponibili durante l'esecuzione del debug.

- I punti di interruzione non vengono mantenuti quando le attività vengono copiate o incollate.

- Impossibile impostare i punti di interruzione del flusso di lavoro nella finestra dello stack di chiamate.

- Durante la creazione di punti di interruzione nella finestra di progettazione, il **Line** e **carattere** impostazioni nel **nuovo punto di interruzione** finestra di dialogo non vengono usati.

- La finestra Punto di interruzione o il menu di scelta rapida non supporta le colonne o le opzioni seguenti per il debug del flusso di lavoro:

  - Condizione

  - Numero di passaggi

  - Quando raggiunto

  - Funzione

  - Data

  - Process

  - Vai a disassembly
