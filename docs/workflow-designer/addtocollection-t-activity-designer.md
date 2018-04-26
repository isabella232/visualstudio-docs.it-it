---
title: Finestra di progettazione del flusso di lavoro - AddToCollection<T> ActivityDesigner
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b32df48f79d60500cb23a40c5273ceeedfc9c56
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="addtocollectiont-activity-designer"></a>AddToCollection\<T > ActivityDesigner

Il **AddToCollection\<T >** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.AddToCollection%601> attività.

## <a name="the-addtocollectiont-activity"></a>Il AddToCollection\<T > attività

L'attività <xref:System.Activities.Statements.AddToCollection%601> aggiunge un elemento a una raccolta.

### <a name="using-the-addtocollectiont-activity-designer"></a>Utilizzo di AddToCollection\<T > ActivityDesigner

Il **AddToCollection\<T >** ActivityDesigner è reperibile nella **raccolta** categoria del **casella degli strumenti**, accessibile facendo clic il  **Casella degli strumenti** scheda della finestra di progettazione del flusso di lavoro (in alternativa, selezionare **sulla barra degli strumenti** dal **vista** menu o premere CTRL + ALT + X.)

Il **AddToCollection\<T >** ActivityDesigner può essere trascinato dal **casella degli strumenti** e rilasciate sull'area di progettazione flussi di lavoro ogni volta che vengono posizionate le attività, ad esempio all'interno di un <xref:System.Activities.Statements.Sequence>. Eliminazione di **AddToCollection\<T >** ActivityDesigner crea un <xref:System.Activities.Statements.AddToCollection%601> attività con un valore predefinito <xref:System.Activities.Activity.DisplayName%2A> di AddToCollection < Int32\>. (Per impostazione predefinita, il *TypeArgument* è **Int32**. TypeArgument può essere modificato nella griglia delle proprietà.) Il <xref:System.Activities.Activity.DisplayName%2A> possibile modificare il valore nell'intestazione del **AddToCollection < T\>**  ActivityDesigner o nel **DisplayName** casella della griglia delle proprietà. Le altre proprietà devono essere modificate nella griglia delle proprietà.

### <a name="the-addtocollectiont-properties"></a>Il AddToCollection\<T > proprietà

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.AddToCollection%601> e ne viene descritta la modalità di utilizzo nella finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.AddToCollection%601>. Il valore predefinito è AddToCollection < Int32\>. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|Elemento da aggiungere alla raccolta\<T >. Questo elemento è di tipo *T*, che è di tipo *TypeArgument*. Per specificare l'elemento, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|Raccolta alla quale aggiungere l'elemento. Questa raccolta è di tipo **ICollection < TypeArgument\>**. Per specificare la raccolta, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|*TypeArgument*|True|Tipo T degli elementi contenuti in <xref:System.Collections.Generic.ICollection%601>. Per impostazione predefinita, questo *TypeArgument* tipo è impostato su **Int32**. Per modificare il tipo, modificare il valore di *TypeArgument* nella casella combinata nella griglia delle proprietà.|

## <a name="see-also"></a>Vedere anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T > ActivityDesigner](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T >](../workflow-designer/removefromcollection-t-activity-designer.md)