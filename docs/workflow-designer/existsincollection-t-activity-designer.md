---
title: ActivityDesigner Progettazione flussi di lavoro-ActivityDesigner ExistsInCollection &lt;T &gt;
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a9dc1f6a3694b6164fe4f2187fa4c6e2b42751e7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650484"
---
# <a name="existsincollectiont-activity-designer"></a>ActivityDesigner ActivityDesigner ExistsInCollection \<T >

L'ActivityDesigner **activitydesigner existsincollection \<T >** viene utilizzato per creare e configurare un'attività di <xref:System.Activities.Statements.ExistsInCollection%601>.

## <a name="the-existsincollectiont-activity"></a>Attività ActivityDesigner ExistsInCollection \<T >

L'attività <xref:System.Activities.Statements.ExistsInCollection%601> determina se in una particolare raccolta è presente un elemento specificato.

### <a name="using-the-existsincollectiont-activity-designer"></a>Uso di ActivityDesigner ExistsInCollection \<T > Activity Designer

L'ActivityDesigner **activitydesigner existsincollection \<T >** è disponibile nella categoria **raccolta** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** di progettazione flussi di lavoro. In alternativa, scegliere **casella degli strumenti** dal menu **Visualizza** oppure premere **CTRL** +**ALT** +**X**.

È possibile trascinare l'ActivityDesigner **activitydesigner existsincollection \<T >** dalla **casella degli strumenti** e rilasciarlo nell'area di progettazione flussi di lavoro quando vengono in genere posizionate le attività, ad esempio all'interno di un <xref:System.Activities.Statements.Sequence>. Viene creata un'attività <xref:System.Activities.Statements.ExistsInCollection%601> con una <xref:System.Activities.Activity.DisplayName%2A> predefinita di ActivityDesigner ExistsInCollection < Int32 \>. Per impostazione predefinita, *TypeArgument* è **Int32**. Può essere modificato nella griglia delle proprietà.  Il valore <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **activitydesigner existsincollection < t \>** o nella casella **DisplayName** della griglia delle proprietà. Le altre proprietà devono essere modificate nella griglia delle proprietà.

### <a name="the-existsincollectiont-properties"></a>Proprietà di > \<T ActivityDesigner ExistsInCollection

Nella tabella seguente vengono illustrate le proprietà <xref:System.Activities.Statements.ExistsInCollection%601> e viene descritto il modo in cui vengono utilizzate nella finestra di progettazione:

|Nome proprietà|Richiesto|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.ExistsInCollection%601>. Il valore predefinito è ActivityDesigner ExistsInCollection < Int32 \>. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|True|Elemento da cercare nella raccolta \<T >. Questo elemento è di tipo *T*, che è di tipo *TypeArgument*. Per specificare l'elemento, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|True|Raccolta in cui verificare se l'elemento esiste. Questa raccolta è di tipo **ICollection < TypeArgument \>.** Per specificare la raccolta, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|*TypeArgument*|True|Tipo T degli elementi contenuti in <xref:System.Collections.Generic.ICollection%601>. Per impostazione predefinita, questo tipo di *TypeArgument* è impostato su **Int32**. Per modificare il tipo, modificare il valore di *TypeArgument* nella casella combinata della griglia delle proprietà.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Valore che indica se l'elemento specificato è presente nella raccolta. Per specificare una variabile da associare al risultato, digitare una variabile Visual Basic nella griglia delle proprietà.|

## <a name="see-also"></a>Vedere anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)