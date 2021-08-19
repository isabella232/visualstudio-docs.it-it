---
title: Scenari di debug non supportati
description: Informazioni sugli scenari di debug non supportati nel Progettazione flussi di lavoro, ad esempio "L'esecuzione non può essere continuata dopo la modifica del codice".
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: fbc2e7c2c465196bfc4781bf7cda7e3d0bd9dd8d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122098931"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Scenari di debug non supportati in Progettazione flussi di lavoro

Il Progettazione flussi di lavoro non supporta gli scenari di debug seguenti:

- Impossibile continuare l'esecuzione dopo che il codice è stato modificato.

- Impossibile continuare l'esecuzione da un punto arbitrario nel flusso di lavoro (Imposta istruzione successiva).

- Impossibile continuare l'esecuzione fino a quando non si raggiunge il cursore (Esegui fino al cursore).

- Impossibile usare Progettazione flussi di lavoro per eseguire debug di flussi di lavoro creati in codice senza l'uso della finestra di progettazione.

- Non è possibile eseguire il debug dei flussi di lavoro creati nelle versioni precedenti di Windows Workflow Foundation (WF) in .NET Framework 4 o versioni successive.

- Impossibile definire i punti di interruzione nei collegamenti tra attività o nodi <xref:System.Activities.Statements.Flowchart>.

- Gli Appunti non sono disponibili durante l'esecuzione del debug.

- I punti di interruzione non vengono mantenuti quando le attività vengono copiate o incollate.

- Impossibile impostare i punti di interruzione del flusso di lavoro nella finestra dello stack di chiamate.

- Quando si creano punti di interruzione nella finestra di progettazione, **le impostazioni Riga** e Carattere nella finestra **di** dialogo Nuovo punto di interruzione non vengono usate. 

- La finestra Punto di interruzione o il menu di scelta rapida non supporta le colonne o le opzioni seguenti per il debug del flusso di lavoro:

  - Condition

  - Passaggi

  - Quando raggiunto

  - Funzione

  - Dati

  - Processo

  - Vai a disassembly
