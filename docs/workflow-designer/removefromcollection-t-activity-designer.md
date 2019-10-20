---
title: ActivityDesigner Progettazione flussi di lavoro-ActivityDesigner RemoveFromCollection &lt;T &gt;
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a8885505607d654327ad9dc36ab88708ab708c3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649994"
---
# <a name="removefromcollectiont-activity-designer"></a>ActivityDesigner ActivityDesigner RemoveFromCollection \<T >

L'ActivityDesigner **activitydesigner removefromcollection \<T >** viene utilizzato per creare e configurare un'attività di <xref:System.Activities.Statements.RemoveFromCollection%601>.

## <a name="the-removefromcollectiontactivity"></a>Attività ActivityDesigner RemoveFromCollection \<T >

L'attività <xref:System.Activities.Statements.RemoveFromCollection%601> rimuove un determinato elemento da una raccolta specifica.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Uso di ActivityDesigner RemoveFromCollection \<T > Activity Designer

Accedere all'ActivityDesigner **activitydesigner removefromcollection \<T >** nella categoria **raccolta** della **casella degli strumenti**.
È possibile trascinare l'ActivityDesigner **activitydesigner removefromcollection \<T >** dalla **casella degli strumenti** e rilasciarlo nell'area di progettazione flussi di lavoro quando vengono in genere posizionate le attività, ad esempio all'interno di un <xref:System.Activities.Statements.Sequence>. Viene creata un'attività <xref:System.Activities.Statements.RemoveFromCollection%601> con una <xref:System.Activities.Activity.DisplayName%2A> predefinita di ActivityDesigner RemoveFromCollection < Int32 \>. Il valore <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **activitydesigner removefromcollection < t \>** o nella casella **DisplayName** della griglia delle proprietà. Le altre proprietà devono essere modificate nella griglia delle proprietà.

### <a name="the-removefromcollectiont-properties"></a>Proprietà di ActivityDesigner RemoveFromCollection < T \>

Nella tabella seguente vengono illustrate le proprietà <xref:System.Activities.Statements.RemoveFromCollection%601> e viene descritto il modo in cui vengono utilizzate nella finestra di progettazione:

|Nome proprietà|Richiesto|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.RemoveFromCollection%601>. Il valore predefinito è ActivityDesigner RemoveFromCollection < Int32 \>.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|True|Elemento da rimuovere dalla **raccolta \<T >** . Questo elemento è di tipo *T*, che è di tipo *TypeArgument*. Per specificare l'elemento, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|True|Raccolta da cui rimuovere l'elemento. Questa raccolta è di tipo **ICollection < TypeArgument \>.** Per specificare la raccolta, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|*TypeArgument*|True|Tipo T degli elementi contenuti in <xref:System.Collections.Generic.ICollection%601>. Per impostazione predefinita, questo tipo di *TypeArgument* è impostato su **Int32**. Per modificare il tipo, modificare il valore di *TypeArgument* nella casella combinata della griglia delle proprietà.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Valore che indica se l'elemento specificato è stato rimosso dalla raccolta. Per specificare una variabile da associare al risultato, digitare una variabile Visual Basic nella griglia delle proprietà.|

## <a name="see-also"></a>Vedere anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)