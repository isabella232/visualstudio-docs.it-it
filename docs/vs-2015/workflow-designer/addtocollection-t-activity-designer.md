---
title: ActivityDesigner AddToCollection &lt; T &gt; | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659198"
---
# <a name="addtocollectionlttgt-activity-designer"></a>ActivityDesigner AddToCollection &lt; T &gt;
L' **ActivityDesigner \<T> AddToCollection** viene usato per creare e configurare un' <xref:System.Activities.Statements.AddToCollection%601> attività.

## <a name="the-addtocollectiont-activity"></a>Attività AddToCollection \<T>
 L'attività <xref:System.Activities.Statements.AddToCollection%601> aggiunge un elemento a una raccolta.

### <a name="using-the-addtocollectiont-activity-designer"></a>Utilizzo dell'ActivityDesigner \<T> AddToCollection
 L' **ActivityDesigner \<T> AddToCollection** è disponibile nella categoria **raccolta** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** di [!INCLUDE[wfd2](../includes/wfd2-md.md)] . in alternativa, scegliere **barra degli** strumenti dal menu **Visualizza** o premere CTRL + ALT + X.

 È possibile trascinare l'ActivityDesigner **AddToCollection \<T> ** dalla **casella degli strumenti** e rilasciarlo nell'area in cui [!INCLUDE[wfd2](../includes/wfd2-md.md)] vengono in genere posizionate le attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . Viene creata un' <xref:System.Activities.Statements.AddToCollection%601> attività con il valore predefinito <xref:System.Activities.Activity.DisplayName%2A> AddToCollection \<Int32> . Per impostazione predefinita, *TypeArgument* è **Int32**. Questo può essere modificato nella griglia delle proprietà. Il <xref:System.Activities.Activity.DisplayName%2A> valore può essere modificato nell'intestazione dell'ActivityDesigner **AddToCollection \<T> ** o nella casella **DisplayName** della griglia delle proprietà. Le altre proprietà devono essere modificate nella griglia delle proprietà.

### <a name="the-addtocollectiont-properties"></a>Proprietà di AddToCollection \<T>
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.AddToCollection%601> e ne viene descritta la modalità di uso nella finestra di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo dell'attività <xref:System.Activities.Statements.AddToCollection%601>. Il valore predefinito è AddToCollection \<Int32> . Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|Vero|Elemento da aggiungere alla raccolta \<T> . Questo elemento è di tipo *T*, che è di tipo *TypeArgument*. Per specificare l'elemento, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|Vero|Raccolta alla quale aggiungere l'elemento. Questa raccolta è di tipo **ICollection \<TypeArgument> **. Per specificare la raccolta, digitare un'espressione Visual Basic nella griglia delle proprietà.|
|*TypeArgument*|Vero|Tipo T degli elementi contenuti in <xref:System.Collections.Generic.ICollection%601>. Per impostazione predefinita, questo tipo di *TypeArgument* è impostato su **Int32**. Per modificare il tipo, modificare il valore di *TypeArgument* nella casella combinata della griglia delle proprietà.|

## <a name="see-also"></a>Vedere anche
 [Collection](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T> Activity](../workflow-designer/addtocollection-t-activity-designer.md) [ \<T> ](../workflow-designer/existsincollection-t-activity-designer.md) [Designer \<T> ClearCollection](../workflow-designer/clearcollection-t-activity-designer.md) ActivityDesigner ExistsInCollection [ActivityDesigner RemoveFromCollection \<T> ](../workflow-designer/removefromcollection-t-activity-designer.md)