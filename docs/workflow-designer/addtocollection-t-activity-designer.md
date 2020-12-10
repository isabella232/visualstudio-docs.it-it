---
title: ActivityDesigner AddToCollection &lt; T &gt;
description: Informazioni sul modo <T> in cui viene usato l'ActivityDesigner AddToCollection per creare e configurare un' <T> attività AddToCollection in Progettazione flussi di lavoro.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1592eab528f2312a9ad90dec02354814d6a81c3
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993250"
---
# <a name="addtocollectiont-activity-designer"></a>Activity Designer\<T> AddToCollection

L' **ActivityDesigner \<T> AddToCollection** viene usato per creare e configurare un' <xref:System.Activities.Statements.AddToCollection%601> attività.

## <a name="the-addtocollectiont-activity"></a>Attività AddToCollection \<T>

L'attività <xref:System.Activities.Statements.AddToCollection%601> aggiunge un elemento a una raccolta.

### <a name="using-the-addtocollectiont-activity-designer"></a>Utilizzo dell'ActivityDesigner \<T> AddToCollection

L' **ActivityDesigner \<T> AddToCollection** è disponibile nella categoria **raccolta** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** della progettazione flussi di lavoro. In alternativa, scegliere **casella degli strumenti** dal menu **Visualizza** o premere **CTRL** + **ALT** + **X**.

È possibile trascinare l'ActivityDesigner **AddToCollection \<T>** dalla **casella degli strumenti** e rilasciarlo nell'area Progettazione flussi di lavoro ogni volta che vengono inserite le attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . Se si elimina l'ActivityDesigner **AddToCollection \<T>** , viene creata un' <xref:System.Activities.Statements.AddToCollection%601> attività con il valore predefinito <xref:System.Activities.Activity.DisplayName%2A> AddToCollection<Int32 \> . Per impostazione predefinita, *TypeArgument* è **Int32**. TypeArgument può essere modificato nella griglia delle proprietà. Il <xref:System.Activities.Activity.DisplayName%2A> valore può essere modificato nell'intestazione dell'ActivityDesigner **AddToCollection<T \>** o nella casella **DisplayName** della griglia delle proprietà. Le altre proprietà devono essere modificate nella griglia delle proprietà.

### <a name="the-addtocollectiont-properties"></a>Proprietà di AddToCollection \<T>

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.AddToCollection%601> e ne viene descritta la modalità di uso nella finestra di progettazione.

|Nome proprietà|Obbligatoria|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo dell'attività <xref:System.Activities.Statements.AddToCollection%601>. Il valore predefinito è AddToCollection<Int32 \> . Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|Elemento da aggiungere alla raccolta \<T> . Questo elemento è di tipo *T*, che è di tipo *TypeArgument*. Per specificare l'elemento, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|Raccolta alla quale aggiungere l'elemento. Questa raccolta è di tipo **ICollection<TypeArgument \>**. Per specificare la raccolta, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|*TypeArgument*|True|Tipo T degli elementi contenuti in <xref:System.Collections.Generic.ICollection%601>. Per impostazione predefinita, questo tipo di *TypeArgument* è impostato su **Int32**. Per modificare il tipo, modificare il valore di *TypeArgument* nella casella combinata della griglia delle proprietà.|

## <a name="see-also"></a>Vedere anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [Activity Designer\<T> AddToCollection ](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)
