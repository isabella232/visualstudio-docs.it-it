---
title: 'Procedura: utilizzare la ricerca in Progettazione del flusso di lavoro'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 63ad6f8b6d3afd1f30f2e9a02eaa4927fb3608d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817476"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Procedura: utilizzare la ricerca in Progettazione del flusso di lavoro

Per semplificare la creazione di flussi di lavoro più grandi e più complessi, è possibile eseguire ricerche all'interno del Progettazione flussi di lavoro per trovare gli elementi in base alla parola chiave. Notare che la finestra di progettazione non supporta la sostituzione.

## <a name="quick-find"></a>Ricerca veloce

La ricerca rapida trova quanto segue nella finestra di progettazione:

- Proprietà degli oggetti <xref:System.Activities.Activity>, <xref:System.Activities.Statements.FlowNode>, <xref:System.Activities.Statements.State>, transizioni, nonché altri elementi di controllo del flusso personalizzati.

- variables

- Argomenti

- Espressioni

### <a name="use-quick-find"></a>Usa ricerca veloce

1. Con progettazione flussi di lavoro aperto, premere **CTRL + F**oppure selezionare **modifica**  >  **trova e Sostituisci**  >  **ricerca veloce**.

2. Immettere il termine di ricerca nella casella di testo **trova** e fare clic su **Trova successivo**.

3. Il termine di ricerca si trova nel flusso di lavoro corrente. La figura seguente mostra un nome visualizzato dell'attività che si trova nella finestra di progettazione:

   ![Risultato della ricerca nella finestra di progettazione flussi di lavoro](../workflow-designer/media/designersearch.png)

## <a name="find-in-files"></a>Cercare nei file

Cerca nei file individua le stringhe nei file del flusso di lavoro, inclusi i file XAML.

### <a name="use-find-in-files"></a>USA Cerca nei file

1. In Visual Studio premere **CTRL** + **MAIUSC** + **F**oppure selezionare **Modifica**  >  **trova e Sostituisci**  >  **Cerca nei file**.

2. Immettere l'elemento di ricerca nella casella di testo **trova** e fare clic su **Trova tutti**.

3. Il risultato della ricerca viene visualizzato nella visualizzazione dei **Risultati della ricerca** . Facendo doppio clic su un elemento del risultato si passa all'attività che contiene la corrispondenza in Progettazione flussi di lavoro.