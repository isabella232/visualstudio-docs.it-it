---
title: ActivityDesigner T ExistsInCollection &lt; &gt;
description: Informazioni su come usare l'ActivityDesigner ExistsInCollection in Progettazione flussi di lavoro <T> creare e configurare un'attività <T> ExistsInCollection.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: ac03ddce895b18c95d74fd41a0ab2692fe92ccd750b95611fda0caf950384b8b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121408000"
---
# <a name="existsincollectiont-activity-designer"></a>Activity Designer\<T> ExistsInCollection

**L'ActivityDesigner \<T> ExistsInCollection** viene usato per creare e configurare un'attività. <xref:System.Activities.Statements.ExistsInCollection%601>

## <a name="the-existsincollectiont-activity"></a>Attività \<T> ExistsInCollection

L'attività <xref:System.Activities.Statements.ExistsInCollection%601> determina se in una particolare raccolta è presente un elemento specificato.

### <a name="using-the-existsincollectiont-activity-designer"></a>Uso dell'ActivityDesigner ExistsInCollection \<T>

**L'ActivityDesigner \<T> ExistsInCollection** è disponibile nella categoria **Raccolta** della Casella degli strumenti **,** a cui si accede facendo clic sulla scheda **Casella** degli strumenti Progettazione flussi di lavoro. In alternativa, selezionare **Casella degli** **strumenti** dal menu Visualizza o premere **CTRL** +  + **ALT+X.**

**L'ActivityDesigner \<T> ExistsInCollection** può essere  trascinato dalla casella degli strumenti e rilasciato sulla superficie di Progettazione flussi di lavoro ogni volta che vengono in genere inserite attività, ad esempio all'interno di <xref:System.Activities.Statements.Sequence> un oggetto . Verrà creata <xref:System.Activities.Statements.ExistsInCollection%601> un'attività con un valore <xref:System.Activities.Activity.DisplayName%2A> predefinito ExistsInCollection<Int32 \> . Per impostazione predefinita, *TypeArgument* è **Int32.** Può essere modificato nella griglia delle proprietà.  Il <xref:System.Activities.Activity.DisplayName%2A> valore può essere modificato nell'intestazione dell'activitydesigner **ExistsInCollection<\> T** o nella casella **DisplayName** della griglia delle proprietà. Le altre proprietà devono essere modificate nella griglia delle proprietà.

### <a name="the-existsincollectiont-properties"></a>Proprietà \<T> ExistsInCollection

La tabella seguente illustra <xref:System.Activities.Statements.ExistsInCollection%601> le proprietà e descrive come vengono usate nella finestra di progettazione:

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo dell'attività <xref:System.Activities.Statements.ExistsInCollection%601>. Il valore predefinito è ExistsInCollection<Int32 \> . Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|Vero|Elemento da cercare nell'insieme \<T> . Questo elemento è di tipo *T*, che è di tipo *TypeArgument*. Per specificare l'elemento, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|Vero|Raccolta in cui verificare se l'elemento esiste. Questa raccolta è di tipo **ICollection<TypeArgument \> .** Per specificare la raccolta, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|*TypeArgument*|Vero|Tipo T degli elementi contenuti in <xref:System.Collections.Generic.ICollection%601>. Per impostazione predefinita, questo *tipo TypeArgument* è impostato su **Int32.** Per modificare il tipo, modificare il valore di *TypeArgument* nella casella combinata nella griglia delle proprietà.|
|<xref:System.Activities.Activity%601.Result%2A>|Falso|Valore che indica se l'elemento specificato è presente nella raccolta. Per specificare una variabile da associare al risultato, digitare una variabile Visual Basic nella griglia delle proprietà.|

## <a name="see-also"></a>Vedi anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)