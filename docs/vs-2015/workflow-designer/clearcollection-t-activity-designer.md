---
title: '@No__t_1 ActivityDesigner ClearCollection &lt;T | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8c2f1e0264d39c65601a70e8c24b51c7eceadf4a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657014"
---
# <a name="clearcollectionlttgt-activity-designer"></a>ActivityDesigner &lt;T &gt; ClearCollection
Per creare e configurare un'attività <xref:System.Activities.Statements.ClearCollection%601>, viene utilizzato l'ActivityDesigner **clearcollection \<T >** .

## <a name="the-clearcollectiont-activity"></a>Attività \<T > ClearCollection
 L'attività <xref:System.Activities.Statements.ClearCollection%601> cancella tutti gli elementi di una raccolta specificata.

### <a name="using-the-clearcollectiont-activity-designer"></a>Uso di ClearCollection \<T > Activity Designer
 L'ActivityDesigner **clearcollection \<T >** è disponibile nella categoria **raccolta** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** del [!INCLUDE[wfd2](../includes/wfd2-md.md)] (in alternativa, selezionare **barra degli** strumenti dal Menu **Visualizza** o CTRL + ALT + X.

 È possibile trascinare l'ActivityDesigner **clearcollection \<T >** dalla **casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../includes/wfd2-md.md)] quando vengono in genere posizionate le attività, ad esempio all'interno di un <xref:System.Activities.Statements.Sequence>. Viene creata un'attività di <xref:System.Activities.Statements.ClearCollection%601> con un <xref:System.Activities.Activity.DisplayName%2A> predefinito di ClearCollection \<Int32 >. Per impostazione predefinita, *TypeArgument* è **Int32**. Questo può essere modificato nella griglia delle proprietà. Il valore di <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **clearcollection \<T >** o nella casella **DisplayName** della griglia delle proprietà. Le altre proprietà devono essere modificate nella griglia delle proprietà.

### <a name="the-clearcollectiont-properties"></a>Proprietà > \<T ClearCollection
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.ClearCollection%601> e ne viene descritta la modalità di uso nella finestra di progettazione.

|Nome proprietà|Richiesto|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.ClearCollection%601>. Il valore predefinito è ClearCollection \<Int32 >. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|Specifica la raccolta di cui cancellare tutti gli elementi. Questa raccolta è di tipo **ICollection \<TypeArgument >.** Per specificare la raccolta, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|*TypeArgument*|True|Specifica il tipo T degli elementi contenuti in <xref:System.Collections.Generic.ICollection%601>. Per impostazione predefinita, questo tipo di *TypeArgument* è impostato su **Int32**. Per modificare il tipo, modificare il valore di *TypeArgument* nella casella combinata della griglia delle proprietà.|

## <a name="see-also"></a>Vedere anche
 [Collection](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T >](../workflow-designer/addtocollection-t-activity-designer.md) [activitydesigner existsincollection \<T >](../workflow-designer/existsincollection-t-activity-designer.md) [ActivityDesigner RemoveFromCollection \<T >](../workflow-designer/removefromcollection-t-activity-designer.md)