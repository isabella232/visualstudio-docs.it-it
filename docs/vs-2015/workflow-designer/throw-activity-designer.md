---
title: Activity Designer throw | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: db909618971eeab2d92506d1c29b06290aa9263b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976623"
---
# <a name="throw-activity-designer"></a>ActivityDesigner Throw
Il **Throw** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.Throw> attività.  
  
## <a name="the-throw-activity"></a>Attività Throw  
 L'attività <xref:System.Activities.Statements.Throw> genera un'eccezione.  
  
### <a name="using-the-throw-activity-designer"></a>Utilizzo dell'ActivityDesigner Throw  
 Il **Throw** ActivityDesigner è reperibile nella **Error Handling** categoria del **della casella degli strumenti**, accessibile facendo clic la **della casella degli strumenti**sul lato sinistro della scheda il [!INCLUDE[wfd2](../includes/wfd2-md.md)] (in alternativa, selezionare **sulla barra degli strumenti** dal **visualizzazione** menu oppure premere CTRL + ALT + X.)  
  
 Il **Throw** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie ovunque posizionate le attività vengono in genere, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. Ciò consente di creare un <xref:System.Activities.Statements.Throw> attività con un valore predefinito **DisplayName** throw. Il <xref:System.Activities.Activity.DisplayName%2A> possibile modificare il valore nell'intestazione del **Throw** ActivityDesigner o nel **DisplayName** finestra della griglia delle proprietà. La proprietà <xref:System.Activities.Statements.Throw.Exception%2A> deve essere modificata nella griglia delle proprietà.  
  
### <a name="the-throw-properties"></a>Proprietà di Throw  
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Throw> e ne viene descritta la modalità di uso nella finestra di progettazione.  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.Throw>. Il valore predefinito è Throw.|  
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|Eccezione da generare. Questa eccezione deve derivare da <xref:System.Exception>. Per specificare l'eccezione, digitare un'espressione Visual Basic nella griglia delle proprietà.|  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolta](../workflow-designer/collection-activity-designers.md)   
 [Rethrow](../workflow-designer/rethrow-activity-designer.md)   
 [Activity Designer throw](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)