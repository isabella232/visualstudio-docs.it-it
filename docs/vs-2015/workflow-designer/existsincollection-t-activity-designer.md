---
title: ExistsInCollection&lt;T&gt; ActivityDesigner | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 263bbf16c72bab5a42dc0ba1465d4c7062333071
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965491"
---
# <a name="existsincollectionlttgt-activity-designer"></a>ExistsInCollection&lt;T&gt; ActivityDesigner
Il **ExistsInCollection\<T >** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.ExistsInCollection%601> attività.  
  
## <a name="the-existsincollectiont-activity"></a>ExistsInCollection\<T > attività  
 L'attività <xref:System.Activities.Statements.ExistsInCollection%601> determina se in una particolare raccolta è presente un elemento specificato.  
  
### <a name="using-the-existsincollectiont-activity-designer"></a>Usando ExistsInCollection\<T > ActivityDesigner  
 Il **ExistsInCollection\<T >** ActivityDesigner è reperibile nella **raccolta** categoria del **casella degli strumenti**, accessibile facendo clic di  **Casella degli strumenti** scheda della finestra [!INCLUDE[wfd2](../includes/wfd2-md.md)] (in alternativa, selezionare **sulla barra degli strumenti** dal **visualizzazione** menu o CTRL + ALT + X.)  
  
 Il **ExistsInCollection\<T >** ActivityDesigner può essere trascinato dal **casella degli strumenti** e rilasciarlo al [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie ovunque posizionate le attività vengono in genere, ad esempio all'interno di un <xref:System.Activities.Statements.Sequence>. Ciò consente di creare un <xref:System.Activities.Statements.ExistsInCollection%601> attività con un valore predefinito <xref:System.Activities.Activity.DisplayName%2A> existsincollection\<Int32 >. (Per impostazione predefinita, il *TypeArgument* viene **Int32**. Tale valore può essere modificato nella griglia delle proprietà.  Il <xref:System.Activities.Activity.DisplayName%2A> possibile modificare il valore nell'intestazione del **ExistsInCollection\<T >** ActivityDesigner o nel **DisplayName** finestra della griglia delle proprietà. Le altre proprietà devono essere modificate nella griglia delle proprietà.  
  
### <a name="the-existsincollectiont-properties"></a>ExistsInCollection\<T > proprietà  
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.ExistsInCollection%601> e ne viene descritta la modalità di uso nella finestra di progettazione.  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.ExistsInCollection%601>. L'impostazione predefinita è ExistsInCollection\<Int32 >. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|  
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|True|L'elemento da aggiungere alla raccolta\<T >. Questo elemento è di tipo *T* JE typu *TypeArgument*. Per specificare l'elemento, digitare un'espressione Visual Basic nella griglia delle proprietà.|  
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|True|Raccolta alla quale aggiungere l'elemento. Questa raccolta è di tipo **ICollection\<TypeArgument >.** Per specificare la raccolta, digitare un'espressione Visual Basic nella griglia delle proprietà.|  
|*TypeArgument*|True|Tipo T degli elementi contenuti in <xref:System.Collections.Generic.ICollection%601>. Per impostazione predefinita, ciò *TypeArgument* è impostato su **Int32**. Per modificare il tipo, modificare il valore della *TypeArgument* nella casella combinata nella griglia delle proprietà.|  
|<xref:System.Activities.Activity%601.Result%2A>|False|Valore che indica se l'elemento specificato è presente nella raccolta. Per specificare una variabile da associare al risultato, digitare una variabile Visual Basic nella griglia delle proprietà.|  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolta](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)   
 [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)