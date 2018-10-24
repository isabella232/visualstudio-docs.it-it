---
title: Finestra di progettazione del flusso di lavoro - ExistsInCollection&lt;T&gt; ActivityDesigner
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 59ec7e9df4088c21820fa5fec319ab3e4ac10f78
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853259"
---
# <a name="existsincollectiont-activity-designer"></a>ExistsInCollection\<T > ActivityDesigner

Il **ExistsInCollection\<T >** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.ExistsInCollection%601> attività.

## <a name="the-existsincollectiont-activity"></a>ExistsInCollection\<T > attività

L'attività <xref:System.Activities.Statements.ExistsInCollection%601> determina se in una particolare raccolta è presente un elemento specificato.

### <a name="using-the-existsincollectiont-activity-designer"></a>Usando ExistsInCollection\<T > ActivityDesigner

Il **ExistsInCollection\<T >** ActivityDesigner è reperibile nella **raccolta** categoria del **casella degli strumenti**, accessibile facendo clic di  **Casella degli strumenti** scheda della finestra di progettazione del flusso di lavoro. In alternativa, selezionare **della casella degli strumenti** dal **View** dal menu oppure premere **Ctrl**+**Alt** + **X**.

Il **ExistsInCollection\<T >** ActivityDesigner può essere trascinato dal **casella degli strumenti** e rilasciate sull'area di progettazione del flusso di lavoro ogni volta che le attività vengono in genere posizionate, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. Ciò consente di creare un <xref:System.Activities.Statements.ExistsInCollection%601> attività con un valore predefinito <xref:System.Activities.Activity.DisplayName%2A> existsincollection < Int32\>. (Per impostazione predefinita, il *TypeArgument* viene **Int32**. Tale valore può essere modificato nella griglia delle proprietà.  Il <xref:System.Activities.Activity.DisplayName%2A> possibile modificare il valore nell'intestazione del **ExistsInCollection < T\>**  ActivityDesigner o nel **DisplayName** finestra della griglia delle proprietà. Le altre proprietà devono essere modificate nella griglia delle proprietà.

### <a name="the-existsincollectiont-properties"></a>ExistsInCollection\<T > proprietà

La tabella seguente illustra il <xref:System.Activities.Statements.ExistsInCollection%601> proprietà e viene descritto come usarle nella finestra di progettazione:

|Nome proprietà|Obbligatorio|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.ExistsInCollection%601>. L'impostazione predefinita è ExistsInCollection < Int32\>. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|True|L'elemento da cercare nella raccolta\<T >. Questo elemento è di tipo *T*, che è di tipo *TypeArgument*. Per specificare l'elemento, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|True|Raccolta in cui si desidera controllare se l'elemento esiste. Questa raccolta è di tipo **ICollection < TypeArgument\>.** Per specificare la raccolta, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|*TypeArgument*|True|Tipo T degli elementi contenuti in <xref:System.Collections.Generic.ICollection%601>. Per impostazione predefinita, ciò *TypeArgument* è impostato su **Int32**. Per modificare il tipo, modificare il valore della *TypeArgument* nella casella combinata nella griglia delle proprietà.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Valore che indica se l'elemento specificato è presente nella raccolta. Per specificare una variabile da associare al risultato, digitare una variabile Visual Basic nella griglia delle proprietà.|

## <a name="see-also"></a>Vedere anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T >](../workflow-designer/removefromcollection-t-activity-designer.md)