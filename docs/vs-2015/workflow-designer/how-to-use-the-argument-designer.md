---
title: 'Procedura: usare la finestra di progettazione degli argomenti | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a436d33bbb7c791f3f192357fded779fa77d148d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659107"
---
# <a name="how-to-use-the-argument-designer"></a>Procedura: utilizzare la finestra di progettazione argomenti
Se confrontata con le versioni precedenti di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], la finestra di progettazione argomenti semplifica il flusso di dati da e verso un'attività. Per accedere alla finestra di progettazione, fare clic sul pulsante **argomenti** nell'angolo inferiore sinistro dell'area di disegno. La finestra di progettazione contiene un elenco di argomenti che vengono visualizzati in un formato tabulare e possono essere ordinati in base a ognuna delle intestazioni di colonna, ad eccezione della colonna **valore predefinito** . Ogni argomento include un nome, una direzione per la proprietà in/out/in-out, un tipo e un valore di espressione predefinito (se presente). Il nome e il valore di espressione predefinito sono campi di testo modificabili, mentre il tipo e la direzione sono elenchi a discesa. [!INCLUDE[crabout](../includes/crabout-md.md)] argomenti, vedere [variabili e argomenti](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8).

### <a name="to-create-a-new-argument"></a>Per creare un nuovo argomento

1. Aprire una soluzione per flusso di lavoro o attività in [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. Aprire la finestra di progettazione degli argomenti facendo clic sul pulsante **argomenti** nell'angolo inferiore sinistro dell'area di progettazione. Verrà visualizzata la finestra di progettazione argomenti.

3. Fare clic sulla riga vuota con etichetta **Crea argomento**. Verrà aggiunta una nuova riga con un nuovo argomento usando i valori predefiniti seguenti: argomentox per il **nome** dove x è un numero intero con un valore iniziale pari a 1 che viene incrementato automaticamente per creare nomi di argomento univoci, **in** per la **direzione**e **stringa** per il **tipo di argomento**. Per il **valore predefinito**non viene aggiunto alcun valore. Tali valori possono essere modificati in qualsiasi momento durante il processo di progettazione del flusso di lavoro.

    > [!NOTE]
    > Per eliminare un argomento, selezionarlo facendo clic su di esso e quindi premere il tasto **Canc** .

## <a name="see-also"></a>Vedere anche
 [Uso di](../workflow-designer/using-the-workflow-designer.md) [variabili e argomenti](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8) progettazione flussi di lavoro