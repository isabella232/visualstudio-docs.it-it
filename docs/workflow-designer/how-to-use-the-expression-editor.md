---
title: "Progettazione flussi di lavoro-procedura: utilizzare l'editor espressioni"
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aff5654214809cf2f57767005153ba557df487c1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75584543"
---
# <a name="how-to-use-the-expression-editor"></a>Procedura: utilizzare l'editor espressioni

L'editor espressioni è un controllo Progettazione flussi di lavoro usato in molte attività del flusso di lavoro per immettere e valutare le espressioni. L'editor di espressioni fornisce un'esperienza di modifica dell'IDE completa, tra cui IntelliSense, colorazione, ParamInfo, errore controllo ortografia durante, tra le altre funzionalità. Il compilatore convalida l'espressione dopo che è stata immessa. Se l'espressione non è valida, viene visualizzata un'icona di errore. L'editor può essere aperto anche come finestra di dialogo **Editor espressioni** .

Le espressioni sono valori letterali o codice Visual Basic associati ad argomenti o proprietà. Contengono elementi valore, ad esempio variabili, costanti, valori letterali, proprietà, combinati con le operazioni per produrre un nuovo valore. Le espressioni vengono scritte usando la sintassi VB.NET, anche se l'applicazione si trova in un programma che usa C#. Ciò significa che l'uso delle maiuscole non è rilevante, il confronto viene eseguito usando un solo segno di uguale ("=" anziché "= ="), gli operatori booleani sono le parole "and" e "or" invece dei simboli "& &" e "| |" e non viene usato **alcun** **valore anziché null**. Per ulteriori informazioni su espressioni e operatori in Visual Basic e per alcuni esempi, vedere [operatori ed espressioni in Visual Basic](/previous-versions/visualstudio/visual-studio-2010/a1w3te48(v=vs.100)).

L' **Editor espressioni** si comporta come segue:

- Se lo stato attivo non è sull'editor espressioni, si presenta come un controllo TextBlock normale.

- Quando lo stato attivo è sull'editor espressioni, si presenta e si comporta come un controllo dell'editor espressioni. Dopo aver perso lo stato attivo, l'editor espressioni riguarderà di nuovo un normale TextBlock.

- Se si imposta lo stato attivo sull'editor espressioni in un oggetto progettazione flussi di lavoro riallocato, si comporta come oggetto TextBox. Quando nell'oggetto progettazione flussi di lavoro riallocato si perde lo stato attivo, l'editor espressioni si presenta nuovamente come un normale oggetto TextBlock.

> [!NOTE]
> IntelliSense per l'editor espressioni è disponibile solo all'interno di Visual Studio. In Visual Studio e negli scenari riallocati, il compilatore convalida l'espressione dopo che è stata immessa e l'editor espressioni Visualizza un'icona di errore se l'espressione non è valida.

## <a name="use-the-expression-editor"></a>Usare l'editor espressioni

1. In Visual Studio aprire un progetto flusso di lavoro nuovo o esistente.

2. Aggiungere, ad esempio, l'attività <xref:System.Activities.Statements.Assign> al flusso di lavoro.

    > [!NOTE]
    > Più attività del flusso di lavoro presentano editor espressioni. Gli oggetti TextBlock vengono inoltre visualizzati nella finestra di progettazione variabili, nella finestra di progettazione argomenti e nella finestra di progettazione argomenti dinamici. L'attività <xref:System.Activities.Statements.Assign> viene usata come esempio.

3. Fare clic sull'editor espressioni sinistro nell'ActivityDesigner per l'attività <xref:System.Activities.Statements.Assign>.

     Le stringhe di filigrana grigie **\<** e **\<immettere un'espressione VB >** sono le stringhe di testo predefinite per gli editor espressioni nell'attività <xref:System.Activities.Statements.Assign>.

4. Immettere l'espressione. Se si immette una stringa, assicurarsi di inserire la stringa tra virgolette. Se si sceglie di associare l'argomento dell'espressione a una variabile, non usare le virgolette.

     Al termine, selezionare un'area o un'area all'esterno dell'editor espressioni per spostare lo stato attivo su un'altra parte della finestra di progettazione. Se si sposta lo stato attivo, il compilatore convaliderà l'espressione come descritto in precedenza.

     Un metodo alternativo per inserire o modificare un'espressione consiste nel fare clic sui puntini di sospensione accanto al nome della proprietà nella griglia delle proprietà. Selezionando i puntini di sospensione si apre l' **Editor espressioni** come finestra di dialogo.

## <a name="see-also"></a>Vedere anche

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
