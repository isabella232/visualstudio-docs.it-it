---
title: ActivityDesigner ActivityDesigner ExistsInCollection &lt; T &gt; | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 08aabbcb7dbef2df9a3affa8589a9c6d4205ac58
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656728"
---
# <a name="existsincollectionlttgt-activity-designer"></a>ActivityDesigner ActivityDesigner ExistsInCollection &lt; T &gt;
L' **ActivityDesigner \<T> ActivityDesigner ExistsInCollection** viene usato per creare e configurare un' <xref:System.Activities.Statements.ExistsInCollection%601> attività.

## <a name="the-existsincollectiont-activity"></a>Attività ActivityDesigner ExistsInCollection \<T>
 L'attività <xref:System.Activities.Statements.ExistsInCollection%601> determina se in una particolare raccolta è presente un elemento specificato.

### <a name="using-the-existsincollectiont-activity-designer"></a>Utilizzo dell'ActivityDesigner \<T> ActivityDesigner ExistsInCollection
 L' **ActivityDesigner \<T> ActivityDesigner ExistsInCollection** è disponibile nella categoria **raccolta** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** di. [!INCLUDE[wfd2](../includes/wfd2-md.md)] in alternativa, scegliere **barra degli** strumenti dal menu **Visualizza** o premere CTRL + ALT + X.

 È possibile trascinare l'ActivityDesigner **ActivityDesigner ExistsInCollection \<T> ** dalla **casella degli strumenti** e rilasciarlo nell'area in cui [!INCLUDE[wfd2](../includes/wfd2-md.md)] vengono in genere posizionate le attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . Viene creata un' <xref:System.Activities.Statements.ExistsInCollection%601> attività con il valore predefinito <xref:System.Activities.Activity.DisplayName%2A> ActivityDesigner ExistsInCollection \<Int32> . Per impostazione predefinita, *TypeArgument* è **Int32**. Può essere modificato nella griglia delle proprietà.  Il <xref:System.Activities.Activity.DisplayName%2A> valore può essere modificato nell'intestazione dell'ActivityDesigner **ActivityDesigner ExistsInCollection \<T> ** o nella casella **DisplayName** della griglia delle proprietà. Le altre proprietà devono essere modificate nella griglia delle proprietà.

### <a name="the-existsincollectiont-properties"></a>Proprietà di ActivityDesigner ExistsInCollection \<T>
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.ExistsInCollection%601> e ne viene descritta la modalità di uso nella finestra di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo dell'attività <xref:System.Activities.Statements.ExistsInCollection%601>. Il valore predefinito è ActivityDesigner ExistsInCollection \<Int32> . Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|Vero|Elemento da aggiungere alla raccolta \<T> . Questo elemento è di tipo *T* è di tipo *TypeArgument*. Per specificare l'elemento, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|Vero|Raccolta alla quale aggiungere l'elemento. Questa raccolta è di tipo **ICollection \<TypeArgument> .** Per specificare la raccolta, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|*TypeArgument*|Vero|Tipo T degli elementi contenuti in <xref:System.Collections.Generic.ICollection%601>. Per impostazione predefinita, questo tipo di *TypeArgument* è impostato su **Int32**. Per modificare il tipo, modificare il valore di *TypeArgument* nella casella combinata della griglia delle proprietà.|
|<xref:System.Activities.Activity%601.Result%2A>|Falso|Valore che indica se l'elemento specificato è presente nella raccolta. Per specificare una variabile da associare al risultato, digitare una variabile Visual Basic nella griglia delle proprietà.|

## <a name="see-also"></a>Vedere anche
 [Raccolta](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T> ](../workflow-designer/addtocollection-t-activity-designer.md) [ClearCollection \<T> ](../workflow-designer/clearcollection-t-activity-designer.md) [ActivityDesigner RemoveFromCollection \<T> ](../workflow-designer/removefromcollection-t-activity-designer.md)