---
title: AddToCollection&lt;T&gt; ActivityDesigner | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4e63486ca7e057fdd1bfe0de73e44dc4951462e2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977211"
---
# <a name="addtocollectionlttgt-activity-designer"></a>AddToCollection&lt;T&gt; ActivityDesigner
Il **AddToCollection\<T >** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.AddToCollection%601> attività.  
  
## <a name="the-addtocollectiont-activity"></a>L'AddToCollection\<T > attività  
 L'attività <xref:System.Activities.Statements.AddToCollection%601> aggiunge un elemento a una raccolta.  
  
### <a name="using-the-addtocollectiont-activity-designer"></a>Usando l'AddToCollection\<T > ActivityDesigner  
 Il **AddToCollection\<T >** ActivityDesigner è reperibile nella **raccolta** categoria del **casella degli strumenti**, accessibile facendo clic di  **Casella degli strumenti** scheda della finestra di [!INCLUDE[wfd2](../includes/wfd2-md.md)] (in alternativa, selezionare **sulla barra degli strumenti** dal **visualizzazione** menu o CTRL + ALT + X.)  
  
 Il **AddToCollection\<T >** ActivityDesigner può essere trascinato dal **casella degli strumenti** e rilasciarlo al [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie ovunque posizionate le attività vengono in genere, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. Ciò consente di creare un <xref:System.Activities.Statements.AddToCollection%601> attività con un valore predefinito <xref:System.Activities.Activity.DisplayName%2A> AddToCollection\<Int32 >. (Per impostazione predefinita, il *TypeArgument* viene **Int32**. Tale valore può essere modificato nella griglia delle proprietà. Il <xref:System.Activities.Activity.DisplayName%2A> possibile modificare il valore nell'intestazione del **AddToCollection\<T >** ActivityDesigner o nel **DisplayName** finestra della griglia delle proprietà. Le altre proprietà devono essere modificate nella griglia delle proprietà.  
  
### <a name="the-addtocollectiont-properties"></a>L'AddToCollection\<T > proprietà  
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.AddToCollection%601> e ne viene descritta la modalità di uso nella finestra di progettazione.  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.AddToCollection%601>. Il valore predefinito è l'AddToCollection\<Int32 >. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|  
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|L'elemento da aggiungere alla raccolta\<T >. Questo elemento è di tipo *T*, che è di tipo *TypeArgument*. Per specificare l'elemento, digitare un'espressione Visual Basic nella griglia delle proprietà.|  
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|Raccolta alla quale aggiungere l'elemento. Questa raccolta è di tipo **ICollection\<TypeArgument >**. Per specificare la raccolta, digitare un'espressione Visual Basic nella griglia delle proprietà.|  
|*TypeArgument*|True|Tipo T degli elementi contenuti in <xref:System.Collections.Generic.ICollection%601>. Per impostazione predefinita, ciò *TypeArgument* è impostato su **Int32**. Per modificare il tipo, modificare il valore della *TypeArgument* nella casella combinata nella griglia delle proprietà.|  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolta](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T > ActivityDesigner](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)   
 [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)