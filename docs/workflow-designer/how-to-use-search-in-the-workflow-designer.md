---
title: 'Procedura: Usare la ricerca in Progettazione flussi di lavoro'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 52adbded9f570689cd5749cc620ca8f74222e308
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854672"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Procedura: Usare la ricerca in Progettazione flussi di lavoro

Per facilitare la creazione di flussi di lavoro più grandi e complesse, è possibile cercare all'interno di progettazione del flusso di lavoro per trovare gli elementi dalla parola chiave. Notare che la finestra di progettazione non supporta la sostituzione.

## <a name="quick-find"></a>Ricerca veloce

Ricerca veloce consente di trovare quanto segue nella finestra di progettazione:

-   Proprietà degli oggetti <xref:System.Activities.Activity>, <xref:System.Activities.Statements.FlowNode>, <xref:System.Activities.Statements.State>, transizioni, nonché altri elementi di controllo del flusso personalizzati.

-   Variabili

-   Argomenti

-   Espressioni

### <a name="use-quick-find"></a>Usare la ricerca veloce

1. Con Progettazione flussi di lavoro aperta, premere **Ctrl + F**, o selezionare **Edit** > **Trova e sostituisci** > **ricerca veloce**.

2. Immettere il termine di ricerca nel **Find what** nella casella di testo e fare clic su **Trova successivo**.

3. Al termine di ricerca si trova nel flusso di lavoro corrente. L'immagine seguente mostra un nome visualizzato dell'attività che si trova nella finestra di progettazione:

   ![Risultato della ricerca nella finestra di progettazione flussi di lavoro](../workflow-designer/media/designersearch.png)

## <a name="find-in-files"></a>Cercare nei file

Cerca nei file individua le stringhe nei file del flusso di lavoro, inclusi i file XAML.

### <a name="use-find-in-files"></a>Usare Cerca nei file

1.  In Visual Studio, premere **Ctrl**+**MAIUSC**+**F**, o selezionare **modifica**  >   **Trova e sostituisci** > **Cerca nei file**.

2.  Immettere l'elemento cercato nel **Find what** nella casella di testo e fare clic su **Trova tutto**.

3.  Il risultato di ricerca viene visualizzato nei **risultati di ricerca** visualizzazione. Fare doppio clic su un elemento del risultato consente di passare all'attività che contiene la corrispondenza nella finestra di progettazione del flusso di lavoro.