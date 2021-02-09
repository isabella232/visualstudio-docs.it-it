---
title: Scenari di debug non supportati
description: Informazioni sugli scenari di debug non supportati nel Progettazione flussi di lavoro, ad esempio, "Impossibile continuare l'esecuzione dopo che il codice è stato modificato".
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 70620528bd3e2d50b85d67eef5990d9843ea5178
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875133"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Scenari di debug non supportati in Progettazione flussi di lavoro

Il Progettazione flussi di lavoro non supporta gli scenari di debug seguenti:

- Impossibile continuare l'esecuzione dopo che il codice è stato modificato.

- Impossibile continuare l'esecuzione da un punto arbitrario nel flusso di lavoro (Imposta istruzione successiva).

- Impossibile continuare l'esecuzione fino a quando non si raggiunge il cursore (Esegui fino al cursore).

- Impossibile usare Progettazione flussi di lavoro per eseguire debug di flussi di lavoro creati in codice senza l'uso della finestra di progettazione.

- Non è possibile eseguire il debug di flussi di lavoro creati in versioni precedenti di Windows Workflow Foundation (WF) in .NET Framework 4 o versione successiva.

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

  - Data

  - Processo

  - Vai a disassembly
