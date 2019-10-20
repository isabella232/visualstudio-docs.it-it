---
title: 'Procedura: utilizzare la ricerca nella Progettazione flussi di lavoro | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
caps.latest.revision: 3
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 84f74b4718a7f976b386197a79692256ab49caa4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659129"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Procedura: utilizzare la ricerca in Progettazione del flusso di lavoro
Per facilitare la creazione di flussi di lavoro più ampi e complessi, è possibile usare la ricerca in Progettazione flussi di lavoro per trovare gli elementi per parola chiave. Notare che la finestra di progettazione non supporta la sostituzione. La ricerca nella finestra di progettazione verrà trovato quanto segue:

## <a name="quick-find"></a>Ricerca veloce
 La ricerca rapida troverà nella finestra di progettazione quanto segue:

- Proprietà degli oggetti <xref:System.Activities.Activity>, <xref:System.Activities.Statements.FlowNode>, <xref:System.Activities.Statements.State>, transizioni, nonché altri elementi di controllo del flusso personalizzati.

- Variabili

- argomenti

- Espressioni

#### <a name="using-quick-find"></a>Uso di Ricerca veloce

1. Con progettazione flussi di lavoro aperto, premere **CTRL + F**oppure selezionare **modifica**, **trova e Sostituisci**, **ricerca veloce**.

2. Immettere il termine di ricerca nella casella di testo **trova** e fare clic su **Trova successivo**.

3. Il termine di ricerca è posizionato nel flusso di lavoro corrente. Nella schermata seguente viene illustrato un nome visualizzato dell'attività che si trova nella finestra di progettazione.

     ![Risultato della ricerca nella Progettazione flussi di lavoro](../workflow-designer/media/designersearch.png "DesignerSearch")

## <a name="find-in-files"></a>Cercare nei file
 Tramite l'uso di Cerca nei file è possibile trovare le stringhe nei file del flusso di lavoro, inclusi i file XAML.

#### <a name="using-find-in-files"></a>Uso di Cerca nei file

1. In Visual Studio, premere **CTRL + MAIUSC + F**oppure selezionare **modifica**, **trova e Sostituisci**, **Cerca nei file** .

2. Immettere l'elemento di ricerca nella casella di testo **trova** e fare clic su **trova tutto**

3. Il risultato della ricerca verrà visualizzato nella visualizzazione dei**Risultati della ricerca** [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Facendo doppio clic su un elemento del risultato verrà visualizzata l'attività contenente la corrispondenza nella finestra di progettazione del flusso di lavoro.