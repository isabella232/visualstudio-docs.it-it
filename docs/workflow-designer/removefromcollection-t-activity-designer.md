---
title: ActivityDesigner Progettazione flussi di lavoro ActivityDesigner RemoveFromCollection &lt; T &gt;
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8af0a0bf8bdf60c8ae9911ef0926cb9e395989a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "86875579"
---
# <a name="removefromcollectiont-activity-designer"></a>Activity Designer\<T> RemoveFromCollection

L' **ActivityDesigner \<T> ActivityDesigner RemoveFromCollection** viene usato per creare e configurare un' <xref:System.Activities.Statements.RemoveFromCollection%601> attività.

## <a name="the-removefromcollectiontactivity"></a>Attività ActivityDesigner RemoveFromCollection \<T>

L'attività <xref:System.Activities.Statements.RemoveFromCollection%601> rimuove un determinato elemento da una raccolta specifica.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Utilizzo dell'ActivityDesigner \<T> ActivityDesigner RemoveFromCollection

Accedere all' **ActivityDesigner \<T> ActivityDesigner RemoveFromCollection** nella categoria **raccolta** della **casella degli strumenti**.
È possibile trascinare l'ActivityDesigner **ActivityDesigner RemoveFromCollection \<T> ** dalla **casella degli strumenti** e rilasciarlo nell'area Progettazione flussi di lavoro quando vengono in genere posizionate le attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . Viene creata un' <xref:System.Activities.Statements.RemoveFromCollection%601> attività con il valore predefinito <xref:System.Activities.Activity.DisplayName%2A> ActivityDesigner RemoveFromCollection<Int32 \> . Il <xref:System.Activities.Activity.DisplayName%2A> valore può essere modificato nell'intestazione dell'ActivityDesigner **ActivityDesigner RemoveFromCollection<T \> ** o nella casella **DisplayName** della griglia delle proprietà. Le altre proprietà devono essere modificate nella griglia delle proprietà.

### <a name="the-removefromcollectiont-properties"></a>Proprietà di ActivityDesigner RemoveFromCollection<T \>

Nella tabella seguente vengono illustrate le <xref:System.Activities.Statements.RemoveFromCollection%601> proprietà e viene descritto il modo in cui vengono utilizzate nella finestra di progettazione:

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.RemoveFromCollection%601>. Il valore predefinito è ActivityDesigner RemoveFromCollection<Int32 \> .<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|Vero|Elemento da rimuovere dalla **raccolta \<T> **. Questo elemento è di tipo *T*, che è di tipo *TypeArgument*. Per specificare l'elemento, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|Vero|Raccolta da cui rimuovere l'elemento. Questa raccolta è di tipo **ICollection<TypeArgument \> .** Per specificare la raccolta, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|*TypeArgument*|Vero|Tipo T degli elementi contenuti in <xref:System.Collections.Generic.ICollection%601>. Per impostazione predefinita, questo tipo di *TypeArgument* è impostato su **Int32**. Per modificare il tipo, modificare il valore di *TypeArgument* nella casella combinata della griglia delle proprietà.|
|<xref:System.Activities.Activity%601.Result%2A>|Falso|Valore che indica se l'elemento specificato è stato rimosso dalla raccolta. Per specificare una variabile da associare al risultato, digitare una variabile Visual Basic nella griglia delle proprietà.|

## <a name="see-also"></a>Vedere anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)