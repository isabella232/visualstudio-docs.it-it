---
title: ActivityDesigner Progettazione flussi di lavoro-ClearCollection &lt; T &gt;
description: Informazioni su come usare l'ActivityDesigner ClearCollection <T> per creare e configurare un'attività ClearCollection <T> .
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ec1820df3a12a729d534d4c07e56bb48bb46e70
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435886"
---
# <a name="clearcollectiont-activity-designer"></a>Activity Designer\<T> ClearCollection

L'ActivityDesigner **ClearCollection \<T>** viene utilizzato per creare e configurare un' <xref:System.Activities.Statements.ClearCollection%601> attività.

## <a name="the-clearcollectiont-activity"></a>Attività ClearCollection \<T>

L'attività <xref:System.Activities.Statements.ClearCollection%601> cancella tutti gli elementi di una raccolta specificata.

### <a name="using-the-clearcollectiont-activity-designer"></a>Utilizzo \<T> dell'ActivityDesigner ClearCollection

L' **ActivityDesigner ClearCollection \<T>** è disponibile nella categoria **raccolta** della **casella degli strumenti** , a cui è possibile accedere facendo clic sulla scheda casella degli **strumenti** della progettazione flussi di lavoro. In alternativa, scegliere **casella degli strumenti** dal menu **Visualizza** o premere **CTRL** + **ALT** + **X**.

È possibile trascinare l'ActivityDesigner **ClearCollection \<T>** dalla **casella degli strumenti** e rilasciarlo nell'area Progettazione flussi di lavoro ogni volta che vengono posizionate le attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . Se si elimina l'ActivityDesigner, viene creata un' <xref:System.Activities.Statements.ClearCollection%601> attività con il valore predefinito <xref:System.Activities.Activity.DisplayName%2A> clearcollection<Int32 \> . Per impostazione predefinita, *TypeArgument* è **Int32**. TypeArgument può essere modificato nella griglia delle proprietà. Il <xref:System.Activities.Activity.DisplayName%2A> valore può essere modificato nell'intestazione dell'ActivityDesigner **clearcollection<T \>** o nella casella **DisplayName** della griglia delle proprietà. Le altre proprietà devono essere modificate nella griglia delle proprietà.

### <a name="the-clearcollectiont-properties"></a>Proprietà ClearCollection \<T>

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.ClearCollection%601> e ne viene descritta la modalità di uso nella finestra di progettazione.

|Nome proprietà|Obbligatoria|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.ClearCollection%601>. Il valore predefinito è ClearCollection<Int32 \> . Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|Vero|Specifica la raccolta di cui cancellare tutti gli elementi. Questa raccolta è di tipo **ICollection \<TypeArgument> .** Per specificare la raccolta, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|*TypeArgument*|Vero|Specifica il tipo T degli elementi contenuti in <xref:System.Collections.Generic.ICollection%601>. Per impostazione predefinita, questo tipo di *TypeArgument* è impostato su **Int32**. Per modificare il tipo, modificare il valore di *TypeArgument* nella casella combinata della griglia delle proprietà.|

## <a name="see-also"></a>Vedere anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)