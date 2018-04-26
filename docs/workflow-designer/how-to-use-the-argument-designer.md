---
title: 'Finestra di progettazione del flusso di lavoro - procedura: utilizzare la finestra di progettazione argomenti'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b94656c7242c4bc6bc1dd1430230dac62a5322f1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-use-the-argument-designer"></a>Procedura: utilizzare la finestra di progettazione argomenti

Rispetto alle versioni precedenti di .NET Framework, la finestra di progettazione argomenti semplifica dati da e verso un'attività del flusso. Viene visualizzata la finestra di progettazione facendo il **argomenti** pulsante nell'angolo inferiore sinistro dell'area di progettazione. La finestra di progettazione contiene un elenco di argomenti che vengono visualizzati in formato tabulare e possono essere ordinati da ciascuna delle intestazioni di colonna, ad eccezione di **il valore predefinito** colonna. Ogni argomento include un nome, una direzione per la proprietà in/out/in-out, un tipo e un valore di espressione predefinito (se presente). Il nome e il valore di espressione predefinito sono campi di testo modificabili, mentre il tipo e la direzione sono elenchi a discesa. Per ulteriori informazioni, vedere [variabili e argomenti (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

## <a name="to-create-a-new-argument"></a>Per creare un nuovo argomento

1.  Aprire una soluzione del flusso di lavoro o attività in Visual Studio 2010.

2.  Aprire la finestra di progettazione facendo clic di **argomenti** pulsante nell'angolo inferiore sinistro dell'area di progettazione. Verrà visualizzata la finestra di progettazione argomenti.

3.  Fare clic sulla riga vuota denominata **Crea argomento**. Verrà aggiunta una nuova riga con un nuovo argomento utilizzando i valori predefiniti seguenti: argumentx per il **nome** dove x è un intero con un valore iniziale pari a 1 che viene incrementato automaticamente per creare nomi di argomenti univoci, **In**  per il **direzione**, e **stringa** per il **tipo di argomento**. Viene aggiunto alcun valore per **il valore predefinito**. Tali valori possono essere modificati in qualsiasi momento durante il processo di progettazione del flusso di lavoro.

    > [!NOTE]
    > Per eliminare un argomento, selezionare l'argomento facendovi clic sopra e quindi premere il **eliminare** chiave.

## <a name="see-also"></a>Vedere anche

- [Uso di Progettazione flussi di lavoro](../workflow-designer/using-the-workflow-designer.md)
- [Variabili e argomenti](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)