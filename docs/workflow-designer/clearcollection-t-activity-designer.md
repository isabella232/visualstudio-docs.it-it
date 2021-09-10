---
title: Progettazione flussi di lavoro - &lt; ActivityDesigner ClearCollection T &gt;
description: Informazioni su come usare l'ActivityDesigner ClearCollection <T> per creare e configurare un'attività <T> ClearCollection.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: cca2dad48095d6c6282f05c8b2dc6d257826fcef
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963306"
---
# <a name="clearcollectiont-activity-designer"></a>Activity Designer\<T> ClearCollection

**L'ActivityDesigner \<T> ClearCollection** viene usato per creare e configurare un'attività. <xref:System.Activities.Statements.ClearCollection%601>

## <a name="the-clearcollectiont-activity"></a>Attività \<T> ClearCollection

L'attività <xref:System.Activities.Statements.ClearCollection%601> cancella tutti gli elementi di una raccolta specificata.

### <a name="using-the-clearcollectiont-activity-designer"></a>Uso dell'ActivityDesigner ClearCollection \<T>

**L'ActivityDesigner \<T> ClearCollection** è disponibile nella categoria **Raccolta** della Casella degli strumenti **,** a cui si accede facendo clic sulla scheda **Casella** degli strumenti del Progettazione flussi di lavoro. In alternativa, scegliere **Casella degli** strumenti **dal** menu Visualizza o premere **CTRL** + **ALT** + **X.**

**L'ActivityDesigner \<T> ClearCollection** può essere  trascinato dalla casella degli strumenti e rilasciato sulla superficie Progettazione flussi di lavoro ogni volta che vengono inserite attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . L'eliminazione dell'ActivityDesigner crea <xref:System.Activities.Statements.ClearCollection%601> un'attività con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito ClearCollection<Int32. \> Per impostazione predefinita, *TypeArgument* è **Int32.** TypeArgument può essere modificato nella griglia delle proprietà. Il <xref:System.Activities.Activity.DisplayName%2A> valore può essere modificato nell'intestazione dell'ActivityDesigner **ClearCollection \><T** o nella casella **DisplayName** della griglia delle proprietà. Le altre proprietà devono essere modificate nella griglia delle proprietà.

### <a name="the-clearcollectiont-properties"></a>Proprietà \<T> clearCollection

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.ClearCollection%601> e ne viene descritta la modalità di uso nella finestra di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.ClearCollection%601>. Il valore predefinito è ClearCollection<\> Int32. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|Vero|Specifica la raccolta di cui cancellare tutti gli elementi. Questa raccolta è di tipo **\<TypeArgument> ICollection.** Per specificare la raccolta, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|*TypeArgument*|Vero|Specifica il tipo T degli elementi contenuti in <xref:System.Collections.Generic.ICollection%601>. Per impostazione predefinita, questo *tipo TypeArgument* è impostato su **Int32.** Per modificare il tipo, modificare il valore di *TypeArgument* nella casella combinata nella griglia delle proprietà.|

## <a name="see-also"></a>Vedi anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)