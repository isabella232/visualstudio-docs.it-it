---
title: ActivityDesigner T RemoveFromCollection &lt; &gt;
description: In Progettazione flussi di lavoro informazioni su come usare l'ActivityDesigner RemoveFromCollection <T> per creare e configurare un'attività RemoveFromCollection. <T>
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: bcf44bbb8db921307137b2d953ecbc085b666e3d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135334"
---
# <a name="removefromcollectiont-activity-designer"></a>Activity Designer\<T> RemoveFromCollection

**L'ActivityDesigner \<T> RemoveFromCollection** viene usato per creare e configurare un'attività. <xref:System.Activities.Statements.RemoveFromCollection%601>

## <a name="the-removefromcollectiontactivity"></a>Attività \<T> RemoveFromCollection

L'attività <xref:System.Activities.Statements.RemoveFromCollection%601> rimuove un determinato elemento da una raccolta specifica.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Uso \<T> dell'ActivityDesigner RemoveFromCollection

Accedere **all'ActivityDesigner RemoveFromCollection \<T>** nella **categoria Raccolta** della casella degli **strumenti**.
**L'ActivityDesigner \<T> RemoveFromCollection** può essere  trascinato dalla casella degli strumenti e rilasciato sulla superficie di Progettazione flussi di lavoro ogni volta che vengono in genere inserite attività, ad esempio all'interno di <xref:System.Activities.Statements.Sequence> un oggetto . Verrà creata <xref:System.Activities.Statements.RemoveFromCollection%601> un'attività con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito RemoveFromCollection<Int32 \> . Il <xref:System.Activities.Activity.DisplayName%2A> valore può essere modificato nell'intestazione dell'activitydesigner **RemoveFromCollection<T \>** o nella casella **DisplayName** della griglia delle proprietà. Le altre proprietà devono essere modificate nella griglia delle proprietà.

### <a name="the-removefromcollectiont-properties"></a>Proprietà removeFromCollection<\> T

La tabella seguente illustra <xref:System.Activities.Statements.RemoveFromCollection%601> le proprietà e descrive come vengono usate nella finestra di progettazione:

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.RemoveFromCollection%601>. Il valore predefinito è RemoveFromCollection<Int32 \> .<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|Vero|Elemento da rimuovere **dall'insieme \<T>**. Questo elemento è di tipo *T*, che è di tipo *TypeArgument*. Per specificare l'elemento, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|Vero|Raccolta da cui rimuovere l'elemento. Questa raccolta è di tipo **ICollection<TypeArgument \> .** Per specificare la raccolta, digitare un'Visual Basic nella griglia delle proprietà.|
|*TypeArgument*|Vero|Tipo T degli elementi contenuti in <xref:System.Collections.Generic.ICollection%601>. Per impostazione predefinita, questo *tipo TypeArgument* è impostato su **Int32.** Per modificare il tipo, modificare il valore di *TypeArgument* nella casella combinata nella griglia delle proprietà.|
|<xref:System.Activities.Activity%601.Result%2A>|Falso|Valore che indica se l'elemento specificato è stato rimosso dalla raccolta. Per specificare una variabile da associare al risultato, digitare una variabile Visual Basic nella griglia delle proprietà.|

## <a name="see-also"></a>Vedi anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)