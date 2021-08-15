---
title: "Progettazione flussi di lavoro - Procedura: Usare l'editor espressioni"
description: Informazioni sul modo in cui l'editor espressioni è Progettazione flussi di lavoro controllo che è possibile usare in molte attività del flusso di lavoro per immettere e valutare espressioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: d24776551e54ad83b780bd58d6a4a2d354acd4d83768d8cb62ad903fab70bc21
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121314264"
---
# <a name="how-to-use-the-expression-editor"></a>Procedura: utilizzare l'editor espressioni

L'editor espressioni è un controllo Progettazione flussi di lavoro utilizzato in molte attività del flusso di lavoro per immettere e valutare espressioni. L'editor espressioni offre un'esperienza completa di modifica dell'IDE, tra cui IntelliSense, colorazione, ParamInfo, controllo asimgrafie degli errori, tra le altre funzionalità. Il compilatore convalida l'espressione dopo l'immissione. Se l'espressione non è valida, viene visualizzata un'icona di errore. L'editor può essere aperto anche come finestra **di dialogo Editor** espressioni.

Le espressioni sono valori letterali o codice Visual Basic associati ad argomenti o proprietà. Contengono elementi valore (ad esempio variabili, costanti, valori letterali, proprietà) combinati con operazioni per produrre un nuovo valore. Le espressioni vengono scritte usando la sintassi VB.NET, anche se l'applicazione si trova in un programma che usa C#. Ciò significa che l'uso delle maiuscole non è importante, il confronto viene eseguito usando un singolo segno di uguale ("=" anziché "=="), gli operatori booleani sono le parole "and" e "or" anziché i simboli "&&" e "||" e **Nothing** viene usato al posto di **null.** Per altre informazioni su espressioni e operatori in Visual Basic e per alcuni esempi, vedere Operatori ed [espressioni in Visual Basic](/previous-versions/visualstudio/visual-studio-2010/a1w3te48(v=vs.100)).

**L'editor espressioni** si comporta come segue:

- Se lo stato attivo non è sull'editor espressioni, si presenta come un controllo TextBlock normale.

- Quando lo stato attivo è sull'editor espressioni, si presenta e si comporta come un controllo dell'editor espressioni. Dopo aver perso lo stato attivo, l'editor espressioni ha di nuovo l'aspetto di un normale controllo TextBlock.

- Se si imposta lo stato attivo sull'editor espressioni in un oggetto progettazione flussi di lavoro riallocato, si comporta come oggetto TextBox. Quando nell'oggetto progettazione flussi di lavoro riallocato si perde lo stato attivo, l'editor espressioni si presenta nuovamente come un normale oggetto TextBlock.

> [!NOTE]
> IntelliSense per l'editor espressioni è disponibile solo all'interno di Visual Studio. In entrambi gli scenari Visual Studio e rihosting, il compilatore convalida l'espressione dopo l'immissione e l'editor di espressioni visualizza un'icona di errore se l'espressione non è valida.

## <a name="use-the-expression-editor"></a>Usare l'editor espressioni

1. In Visual Studio aprire un progetto flusso di lavoro nuovo o esistente.

2. Aggiungere, ad esempio, l'attività <xref:System.Activities.Statements.Assign> al flusso di lavoro.

    > [!NOTE]
    > Più attività del flusso di lavoro presentano editor espressioni. Gli oggetti TextBlock vengono inoltre visualizzati nella finestra di progettazione variabili, nella finestra di progettazione argomenti e nella finestra di progettazione argomenti dinamici. L'attività <xref:System.Activities.Statements.Assign> viene usata come esempio.

3. Fare clic sull'editor espressioni sinistro nell'ActivityDesigner per l'attività <xref:System.Activities.Statements.Assign>.

     Le stringhe del limite **\<To>** grigio e sono le stringhe di testo predefinite per gli editor di espressioni **\<Enter a VB Expression>** <xref:System.Activities.Statements.Assign> nell'attività .

4. Immettere l'espressione. Se si immette una stringa, assicurarsi di inserire la stringa tra virgolette. Se si sceglie di associare l'argomento dell'espressione a una variabile, non usare le virgolette.

     Al termine, selezionare un'area all'esterno dell'Editor espressioni per spostare lo stato attivo su un'altra parte della finestra di progettazione. Spostando lo stato attivo, il compilatore convalida l'espressione come descritto in precedenza.

     Un modo alternativo per immettere o modificare un'espressione consiste nel fare clic sui puntini di sospensione accanto al nome della proprietà nella griglia delle proprietà. Se si selezionano i puntini di sospensione, **l'Editor espressioni viene** aperto come finestra di dialogo.

## <a name="see-also"></a>Vedere anche

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
