---
title: 'Procedura: utilizzare la ricerca in Progettazione del flusso di lavoro'
description: Informazioni su come eseguire ricerche all'interno Progettazione flussi di lavoro trovare elementi in base alla parola chiave in modo da facilitare la creazione di flussi di lavoro più grandi e complessi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 32cb7752ec79545055d6305ff4016613251730a21e255da6633cb1cc8ad4b882
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121314303"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Procedura: utilizzare la ricerca in Progettazione del flusso di lavoro

Per facilitare la creazione di flussi di lavoro più grandi e complessi, è possibile eseguire ricerche all'interno Progettazione flussi di lavoro trovare elementi in base alla parola chiave. Notare che la finestra di progettazione non supporta la sostituzione.

## <a name="quick-find"></a>Ricerca veloce

Ricerca rapida consente di trovare quanto segue nella finestra di progettazione:

- Proprietà degli oggetti <xref:System.Activities.Activity>, <xref:System.Activities.Statements.FlowNode>, <xref:System.Activities.Statements.State>, transizioni, nonché altri elementi di controllo del flusso personalizzati.

- Variabili

- Argomenti

- Espressioni

### <a name="use-quick-find"></a>Usare Ricerca rapida

1. Con la finestra di progettazione del flusso di lavoro aperta, **premere CTRL+F** oppure **selezionare** Modifica Trova e  >  **sostituisci**  >  **Ricerca veloce.**

2. Immettere il termine di ricerca nella casella **di testo Trova e** fare clic su Trova **successivo.**

3. Il termine di ricerca si trova nel flusso di lavoro corrente. L'immagine seguente mostra il nome visualizzato di un'attività che si trova nella finestra di progettazione:

   ![Risultato della ricerca nella finestra di progettazione flussi di lavoro](../workflow-designer/media/designersearch.png)

## <a name="find-in-files"></a>Cercare nei file

Trova in File individua le stringhe nei file del flusso di lavoro, inclusi i file XAML.

### <a name="use-find-in-files"></a>Usare Trova nei file

1. In Visual Studio premere **CTRL** MAIUSC F oppure selezionare Modifica Trova e +  +    >  **sostituisci**  >  **Trova nei file**.

2. Immettere l'elemento di ricerca nella **casella di testo Trova e** fare clic su Trova **tutto.**

3. Il risultato della ricerca viene visualizzato nella **visualizzazione Risultati** ricerca. Facendo doppio clic su un elemento del risultato si passa all'attività che contiene la corrispondenza nella finestra di progettazione del flusso di lavoro.