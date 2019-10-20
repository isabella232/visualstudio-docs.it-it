---
title: ActivityDesigner AddToCollection &lt;T &gt; | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 50deab447b3dcb93d352e73fc4765d913b4d24bf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659198"
---
# <a name="addtocollectionlttgt-activity-designer"></a>ActivityDesigner AddToCollection &lt;T &gt;
L'ActivityDesigner **AddToCollection \<T >** viene utilizzato per creare e configurare un'attività di <xref:System.Activities.Statements.AddToCollection%601>.

## <a name="the-addtocollectiont-activity"></a>Attività AddToCollection \<T >
 L'attività <xref:System.Activities.Statements.AddToCollection%601> aggiunge un elemento a una raccolta.

### <a name="using-the-addtocollectiont-activity-designer"></a>Uso di AddToCollection \<T > Activity Designer
 **AddToCollection \<T >** Activity Designer è disponibile nella categoria **raccolta** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** del [!INCLUDE[wfd2](../includes/wfd2-md.md)] (in alternativa, selezionare **barra degli** strumenti dal Menu **Visualizza** o CTRL + ALT + X.

 È possibile trascinare l'ActivityDesigner **AddToCollection \<T >** dalla **casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../includes/wfd2-md.md)] quando vengono in genere posizionate le attività, ad esempio all'interno di un <xref:System.Activities.Statements.Sequence>. Viene creata un'attività <xref:System.Activities.Statements.AddToCollection%601> con una <xref:System.Activities.Activity.DisplayName%2A> predefinita di AddToCollection \<Int32 >. Per impostazione predefinita, *TypeArgument* è **Int32**. Questo può essere modificato nella griglia delle proprietà. Il valore di <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **AddToCollection \<T >** o nella casella **DisplayName** della griglia delle proprietà. Le altre proprietà devono essere modificate nella griglia delle proprietà.

### <a name="the-addtocollectiont-properties"></a>Proprietà di > \<T AddToCollection
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.AddToCollection%601> e ne viene descritta la modalità di uso nella finestra di progettazione.

|Nome proprietà|Richiesto|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.AddToCollection%601>. Il valore predefinito è AddToCollection \<Int32 >. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|Elemento da aggiungere alla raccolta \<T >. Questo elemento è di tipo *T*, che è di tipo *TypeArgument*. Per specificare l'elemento, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|Raccolta alla quale aggiungere l'elemento. Questa raccolta è di tipo **ICollection \<TypeArgument >** . Per specificare la raccolta, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|*TypeArgument*|True|Tipo T degli elementi contenuti in <xref:System.Collections.Generic.ICollection%601>. Per impostazione predefinita, questo tipo di *TypeArgument* è impostato su **Int32**. Per modificare il tipo, modificare il valore di *TypeArgument* nella casella combinata della griglia delle proprietà.|

## <a name="see-also"></a>Vedere anche
 [Raccolta](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T >](../workflow-designer/addtocollection-t-activity-designer.md) activitydesigner [clearcollection \<T >](../workflow-designer/clearcollection-t-activity-designer.md) [ActivityDesigner ExistsInCollection \<T >](../workflow-designer/existsincollection-t-activity-designer.md) [ActivityDesigner RemoveFromCollection](../workflow-designer/removefromcollection-t-activity-designer.md) \<T >