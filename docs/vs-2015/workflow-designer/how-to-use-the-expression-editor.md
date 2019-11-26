---
title: "Procedura: utilizzare l'editor espressioni | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7d40cefc3dd47f7f4ad7e8255d8bdc06bc5f1651
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300943"
---
# <a name="how-to-use-the-expression-editor"></a>Procedura: utilizzare l'editor espressioni
L'editor espressioni è un controllo di [!INCLUDE[wfd1](../includes/wfd1-md.md)] usato in molte attività del flusso di lavoro per immettere e valutare queste espressioni. L'editor espressioni fornisce un'esperienza di modifica IDE completa che include, tra le altre funzionalità, IntelliSense, colorazione, ParamInfo, controllo errori di ortografia durante la digitazione. Il compilatore convalida l'espressione dopo che è stata immessa. Se l'espressione non è valida, viene visualizzata un'icona di errore. L'editor può essere aperto anche come finestra di dialogo **Editor espressioni** .

 Le espressioni sono valori letterali o codice [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] associati ad argomenti o proprietà. Contengono elementi valore, ad esempio variabili, costanti, valori letterali, proprietà, che vengono combinati con le operazioni per produrre un nuovo valore. Le espressioni vengono scritte usando la sintassi VB.NET, anche se l'applicazione si trova in un programma che usa C#. Ciò significa che la capitalizzazione non è rilevante, il confronto viene eseguito usando un singolo segno di uguale ("=") anziché ("= ="), gli operatori booleani sono le parole "and" e "or" invece dei simboli "& &" e&#124;&#124;"" e **non** viene usato alcun **valore anziché null**. Per ulteriori informazioni su espressioni e operatori in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] e per alcuni esempi, vedere [operatori ed espressioni in Visual Basic](https://go.microsoft.com/fwlink/?LinkId=186818).

 L' **Editor espressioni** si comporta come segue:

- Se lo stato attivo non è sull'editor espressioni, si presenta come un controllo TextBlock normale.

- Quando lo stato attivo è sull'editor espressioni, si presenta e si comporta come un controllo dell'editor espressioni. Dopo aver perso lo stato attivo, si presenta nuovamente come un normale controllo TextBlock.

- Se si imposta lo stato attivo sull'editor espressioni in un oggetto progettazione flussi di lavoro riallocato, si comporta come oggetto TextBox. Quando nell'oggetto progettazione flussi di lavoro riallocato si perde lo stato attivo, l'editor espressioni si presenta nuovamente come un normale oggetto TextBlock.

> [!NOTE]
> IntelliSense per l'editor espressioni e disponibile solo in [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Sia in [!INCLUDE[vs2010](../includes/vs2010-md.md)] che nel caso di scenari di riallocazione, il compilatore convalida l'espressione dopo che è stata immessa e nell'editor espressioni viene visualizzata un'icona di errore se l'espressione non è valida.

### <a name="using-the-expression-editor"></a>Uso dell’editor espressioni

1. In [!INCLUDE[vs2010](../includes/vs2010-md.md)] aprire un progetto flusso di lavoro nuovo o esistente.

2. Aggiungere, ad esempio, l'attività <xref:System.Activities.Statements.Assign> al flusso di lavoro.

    > [!NOTE]
    > Più attività del flusso di lavoro presentano editor espressioni. Gli oggetti TextBlock vengono inoltre visualizzati nella finestra di progettazione variabili, nella finestra di progettazione argomenti e nella finestra di progettazione argomenti dinamici. L'attività <xref:System.Activities.Statements.Assign> viene usata come esempio.

3. Fare clic sull'editor espressioni sinistro nell'ActivityDesigner per l'attività <xref:System.Activities.Statements.Assign>.

     Le stringhe di filigrana grigie **\<>** e **\<immettere un'espressione VB >** sono le stringhe di testo predefinite per gli editor espressioni nell'attività <xref:System.Activities.Statements.Assign>.

4. Immettere l'espressione. Se si immette una stringa, assicurarsi di inserire la stringa tra virgolette. Se si sceglie di associare l'argomento dell'espressione a una variabile, non usare le virgolette.

     Al termine, selezionare un'area esterna all'editor espressioni per trasferire lo stato attivo in un'altra parte della finestra di progettazione. In questo modo il compilatore convalida l'espressione, come descritto precedentemente.

     Una modalità alternativa per immettere/modificare un'espressione consiste nel fare clic sul pulsante con i puntini sospensivi accanto al nome della proprietà nella griglia delle proprietà. Verrà visualizzata la finestra di dialogo **Editor espressioni** come.

## <a name="see-also"></a>Vedere anche
 <xref:System.Activities.Presentation.View.ExpressionTextBox>