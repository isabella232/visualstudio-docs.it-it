---
title: 'Finestra di progettazione del flusso di lavoro - procedura: Usare l’editor espressioni'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 63fca3051ce50f728cf83976f6ef6a5204ad35b8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53956244"
---
# <a name="how-to-use-the-expression-editor"></a>Procedura: Usare l’editor espressioni

L'Editor espressioni è un controllo di finestra di progettazione del flusso di lavoro che viene usato in molte attività del flusso di lavoro per immettere e valutare le espressioni. L'Editor espressioni fornisce un IDE completa la modifica di esperienza, tra cui IntelliSense, colorazione, paraminfo, controllo ortografia durante la digitazione, errore tra le altre funzionalità. Il compilatore convalida l'espressione dopo che è stata immessa. Se l'espressione non è valida, viene visualizzata un'icona di errore. È possibile aprire l'editor anche come un **Editor di espressioni** nella finestra di dialogo.

Le espressioni sono valori letterali o codice Visual Basic associati ad argomenti o proprietà. Contengono elementi valore (ad esempio, le variabili, costanti, valori letterali, proprietà) che vengono combinati con le operazioni per produrre un nuovo valore. Le espressioni vengono scritte usando la sintassi VB.NET, anche se l'applicazione si trova in un programma che usa C#. Ciò significa che l'uso delle maiuscole non è rilevante, il confronto viene eseguito usando un singolo uguale ("=" anziché "= =") l'accesso, gli operatori booleani sono le parole "and" e "or" anziché i simboli "& &" e "| |", e **Nothing** viene utilizzato invece di **null**. Per altre informazioni sulle espressioni e operatori in Visual Basic e per alcuni esempi, vedere [gli operatori ed espressioni in Visual Basic](/previous-versions/visualstudio/visual-studio-2010/a1w3te48(v=vs.100)).

Il **Editor di espressioni** si comporta come segue:

- Se lo stato attivo non è sull'editor espressioni, si presenta come un controllo TextBlock normale.

- Quando lo stato attivo è sull'editor espressioni, si presenta e si comporta come un controllo dell'editor espressioni. Dopo aver perso lo stato attivo, l'Editor espressioni è simile anche in questo caso a un normale controllo TextBlock.

- Se si imposta lo stato attivo sull'editor espressioni in un oggetto progettazione flussi di lavoro riallocato, si comporta come oggetto TextBox. Quando nell'oggetto progettazione flussi di lavoro riallocato si perde lo stato attivo, l'editor espressioni si presenta nuovamente come un normale oggetto TextBlock.

> [!NOTE]
> IntelliSense per l'Editor espressioni è disponibile solo all'interno di Visual Studio. In Visual Studio e di scenari di riallocazione, il compilatore convalida l'espressione dopo che è stata immessa e l'editor espressioni viene visualizzata un'icona di errore se l'espressione non è valido.

## <a name="use-the-expression-editor"></a>Usare l'editor espressioni

1.  In Visual Studio, aprire un progetto di flusso di lavoro nuova o esistente.

2.  Aggiungere, ad esempio, l'attività <xref:System.Activities.Statements.Assign> al flusso di lavoro.

    > [!NOTE]
    > Più attività del flusso di lavoro presentano editor espressioni. Gli oggetti TextBlock vengono inoltre visualizzati nella finestra di progettazione variabili, nella finestra di progettazione argomenti e nella finestra di progettazione argomenti dinamici. L'attività <xref:System.Activities.Statements.Assign> viene usata come esempio.

3.  Fare clic sull'editor espressioni sinistro nell'ActivityDesigner per l'attività <xref:System.Activities.Statements.Assign>.

     Le stringhe con filigrana di colore grigio  **\<al >** e  **\<immettere un'espressione VB >** è il valore predefinito di stringhe di testo per gli editor di espressioni nel <xref:System.Activities.Statements.Assign> attività.

4.  Immettere l'espressione. Se si immette una stringa, assicurarsi di inserire la stringa tra virgolette. Se si sceglie di associare l'argomento dell'espressione a una variabile, non usare le virgolette.

     Al termine, selezionare una regione o area di fuori l'Editor di espressioni per spostare lo stato attivo a un'altra parte della finestra di progettazione. Spostando lo stato attivo, il compilatore convalida l'espressione, come descritto in precedenza.

     Un modo alternativo per immettere o modificare un'espressione è necessario fare clic sui puntini di sospensione accanto al nome della proprietà nella griglia delle proprietà. Selezionando i puntini di sospensione viene visualizzata la **Editor di espressioni** come una finestra di dialogo.

## <a name="see-also"></a>Vedere anche

- <xref:System.Activities.Presentation.View.ExpressionTextBox>