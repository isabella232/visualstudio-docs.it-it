---
title: ActivityDesigner AddToCollection &lt; T &gt;
description: Informazioni sull'uso dell'ActivityDesigner AddToCollection per creare e <T> configurare un'attività AddToCollection <T> in Progettazione flussi di lavoro.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: a204e6147b18938d20a94c0a41c06e8983d4026e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122068151"
---
# <a name="addtocollectiont-activity-designer"></a>Activity Designer\<T> AddToCollection

**L'ActivityDesigner \<T> AddToCollection** viene usato per creare e configurare un'attività. <xref:System.Activities.Statements.AddToCollection%601>

## <a name="the-addtocollectiont-activity"></a>Attività \<T> AddToCollection

L'attività <xref:System.Activities.Statements.AddToCollection%601> aggiunge un elemento a una raccolta.

### <a name="using-the-addtocollectiont-activity-designer"></a>Utilizzo dell'ActivityDesigner AddToCollection \<T>

**L'ActivityDesigner \<T> AddToCollection** è disponibile nella categoria **Raccolta** della Casella degli strumenti **,** a cui si accede facendo clic sulla scheda **Casella** degli strumenti del Progettazione flussi di lavoro. In alternativa, scegliere **Casella degli** strumenti **dal** menu Visualizza o premere **CTRL** + **ALT** + **X.**

**L'ActivityDesigner \<T> AddToCollection** può essere  trascinato dalla casella degli strumenti e rilasciato sulla superficie Progettazione flussi di lavoro ogni volta che vengono inserite attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . L'eliminazione **dell'ActivityDesigner AddToCollection \<T>** crea un'attività con l'impostazione predefinita <xref:System.Activities.Statements.AddToCollection%601> <xref:System.Activities.Activity.DisplayName%2A> AddToCollection<Int32. \> Per impostazione predefinita, *TypeArgument* è **Int32.** TypeArgument può essere modificato nella griglia delle proprietà. Il <xref:System.Activities.Activity.DisplayName%2A> valore può essere modificato nell'intestazione dell'ActivityDesigner **AddToCollection<\> T** o nella casella **DisplayName** della griglia delle proprietà. Le altre proprietà devono essere modificate nella griglia delle proprietà.

### <a name="the-addtocollectiont-properties"></a>Proprietà \<T> AddToCollection

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.AddToCollection%601> e ne viene descritta la modalità di uso nella finestra di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo dell'attività <xref:System.Activities.Statements.AddToCollection%601>. Il valore predefinito è AddToCollection<Int32 \> . Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|Vero|Elemento da aggiungere all'insieme \<T> . Questo elemento è di tipo *T*, che è di *tipo TypeArgument*. Per specificare l'elemento, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|Vero|Raccolta alla quale aggiungere l'elemento. Questa raccolta è di tipo **ICollection \><TypeArgument**. Per specificare la raccolta, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|*TypeArgument*|Vero|Tipo T degli elementi contenuti in <xref:System.Collections.Generic.ICollection%601>. Per impostazione predefinita, questo *tipo TypeArgument* è impostato su **Int32.** Per modificare il tipo, modificare il valore di *TypeArgument* nella casella combinata nella griglia delle proprietà.|

## <a name="see-also"></a>Vedi anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [Activity Designer\<T> AddToCollection ](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)
