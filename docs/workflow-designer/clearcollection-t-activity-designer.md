---
title: Finestra di progettazione del flusso di lavoro - ClearCollection<T> ActivityDesigner
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b3d9d246fa6bad55e47ddff73c888906f2979695
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="clearcollectiont-activity-designer"></a>ClearCollection\<T > ActivityDesigner

Il **ClearCollection\<T >** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.ClearCollection%601> attività.

## <a name="the-clearcollectiont-activity"></a>Il ClearCollection\<T > attività
 L'attività <xref:System.Activities.Statements.ClearCollection%601> cancella tutti gli elementi di una raccolta specificata.

### <a name="using-the-clearcollectiont-activity-designer"></a>Utilizzo di ClearCollection\<T > ActivityDesigner
 Il **ClearCollection\<T >** ActivityDesigner è reperibile nella **raccolta** categoria del **casella degli strumenti**, accessibile facendo clic il  **Casella degli strumenti** scheda della finestra di progettazione del flusso di lavoro (in alternativa, selezionare **sulla barra degli strumenti** dal **vista** menu o premere CTRL + ALT + X.)

 Il **ClearCollection\<T >** ActivityDesigner può essere trascinato dal **casella degli strumenti** e rilasciate sull'area di progettazione flussi di lavoro ogni volta che vengono posizionate le attività, ad esempio all'interno di un <xref:System.Activities.Statements.Sequence>. Rilascio dell'ActivityDesigner crea un <xref:System.Activities.Statements.ClearCollection%601> attività con un valore predefinito <xref:System.Activities.Activity.DisplayName%2A> di ClearCollection < Int32\>. (Per impostazione predefinita, il *TypeArgument* è **Int32**. TypeArgument può essere modificato nella griglia delle proprietà.) Il <xref:System.Activities.Activity.DisplayName%2A> possibile modificare il valore nell'intestazione del **ClearCollection < T\>**  ActivityDesigner o nel **DisplayName** casella della griglia delle proprietà. Le altre proprietà devono essere modificate nella griglia delle proprietà.

### <a name="the-clearcollectiont-properties"></a>Il ClearCollection\<T > proprietà
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.ClearCollection%601> e ne viene descritta la modalità di utilizzo nella finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.ClearCollection%601>. Il valore predefinito è ClearCollection < Int32\>. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|Specifica la raccolta di cui cancellare tutti gli elementi. Questa raccolta è di tipo **ICollection\<TypeArgument >.** Per specificare la raccolta, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|*TypeArgument*|True|Specifica il tipo T degli elementi contenuti in <xref:System.Collections.Generic.ICollection%601>. Per impostazione predefinita, questo *TypeArgument* tipo è impostato su **Int32**. Per modificare il tipo, modificare il valore di *TypeArgument* nella casella combinata nella griglia delle proprietà.|

## <a name="see-also"></a>Vedere anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T >](../workflow-designer/removefromcollection-t-activity-designer.md)