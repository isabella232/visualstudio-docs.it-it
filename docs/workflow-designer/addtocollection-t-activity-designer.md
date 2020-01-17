---
title: ActivityDesigner Progettazione flussi di lavoro-AddToCollection<T>
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
ms.openlocfilehash: eb00679001cc09b8fdfa68f898923ac208b32c4e
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115323"
---
# <a name="addtocollectiont-activity-designer"></a>ActivityDesigner AddToCollection\<T >

L'ActivityDesigner **AddToCollection\<t >** viene utilizzato per creare e configurare un'attività di <xref:System.Activities.Statements.AddToCollection%601>.

## <a name="the-addtocollectiont-activity"></a>Attività AddToCollection\<T >

L'attività <xref:System.Activities.Statements.AddToCollection%601> aggiunge un elemento a una raccolta.

### <a name="using-the-addtocollectiont-activity-designer"></a>Uso dell'ActivityDesigner AddToCollection\<T >

L'ActivityDesigner **AddToCollection\<t >** è disponibile nella categoria **raccolta** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** della progettazione flussi di lavoro. In alternativa, scegliere **casella degli strumenti** dal menu **Visualizza** oppure premere **CTRL**+**ALT**+**X**.

È possibile trascinare l'ActivityDesigner **AddToCollection\<t >** dalla **casella degli strumenti** e rilasciarlo nell'area di progettazione flussi di lavoro quando vengono inserite le attività, ad esempio all'interno di un <xref:System.Activities.Statements.Sequence>. Se si elimina l'ActivityDesigner **AddToCollection\<t >** , viene creata un'attività <xref:System.Activities.Statements.AddToCollection%601> con <xref:System.Activities.Activity.DisplayName%2A> predefinito AddToCollection < Int32\>. Per impostazione predefinita, *TypeArgument* è **Int32**. TypeArgument può essere modificato nella griglia delle proprietà. Il valore <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **AddToCollection < t\>** o nella casella **DisplayName** della griglia delle proprietà. Le altre proprietà devono essere modificate nella griglia delle proprietà.

### <a name="the-addtocollectiont-properties"></a>Proprietà di AddToCollection\<T >

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.AddToCollection%601> e ne viene descritta la modalità di uso nella finestra di progettazione.

|Nome proprietà:|Richiesto|Usage|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo dell'attività <xref:System.Activities.Statements.AddToCollection%601>. Il valore predefinito è AddToCollection < Int32\>. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|Elemento da aggiungere alla raccolta\<> T. Questo elemento è di tipo *T*, che è di tipo *TypeArgument*. Per specificare l'elemento, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|Raccolta alla quale aggiungere l'elemento. Questa raccolta è di tipo **ICollection < TypeArgument\>** . Per specificare la raccolta, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|*TypeArgument*|True|Tipo T degli elementi contenuti in <xref:System.Collections.Generic.ICollection%601>. Per impostazione predefinita, questo tipo di *TypeArgument* è impostato su **Int32**. Per modificare il tipo, modificare il valore di *TypeArgument* nella casella combinata della griglia delle proprietà.|

## <a name="see-also"></a>Vedere anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [ActivityDesigner AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)
