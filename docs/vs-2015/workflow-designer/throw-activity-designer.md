---
title: ActivityDesigner Throw | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1855daa5016241fb6eb04f05d7218e02083fc0a8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655155"
---
# <a name="throw-activity-designer"></a>ActivityDesigner Throw
L'ActivityDesigner **throw** viene usato per creare e configurare un'attività <xref:System.Activities.Statements.Throw>.

## <a name="the-throw-activity"></a>Attività Throw
 L'attività <xref:System.Activities.Statements.Throw> genera un'eccezione.

### <a name="using-the-throw-activity-designer"></a>Utilizzo dell'ActivityDesigner Throw
 L'ActivityDesigner **throw** è disponibile nella categoria **Gestione errori** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** sul lato sinistro del [!INCLUDE[wfd2](../includes/wfd2-md.md)]. in alternativa, selezionare **barra degli** strumenti nella **visualizzazione.** oppure premere CTRL + ALT + X.

 È possibile trascinare l'ActivityDesigner **throw** dalla **casella degli strumenti** e rilasciarlo nell'area [!INCLUDE[wfd2](../includes/wfd2-md.md)] quando vengono in genere posizionate le attività, ad esempio all'interno di un <xref:System.Activities.Statements.Sequence>. Viene creata un'attività di <xref:System.Activities.Statements.Throw> con un valore **DisplayName** predefinito Throw. Il valore <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **throw** o nella casella **DisplayName** della griglia delle proprietà. La proprietà <xref:System.Activities.Statements.Throw.Exception%2A> deve essere modificata nella griglia delle proprietà.

### <a name="the-throw-properties"></a>Proprietà di Throw
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Throw> e ne viene descritta la modalità di uso nella finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.Throw>. Il valore predefinito è Throw.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|Eccezione da generare. Questa eccezione deve derivare da <xref:System.Exception>. Per specificare l'eccezione, digitare un'espressione Visual Basic nella griglia delle proprietà.|

## <a name="see-also"></a>Vedere anche
 [Raccolta](../workflow-designer/collection-activity-designers.md) [Rethrow](../workflow-designer/rethrow-activity-designer.md) [ActivityDesigner Throw](../workflow-designer/throw-activity-designer.md) [TryCatch](../workflow-designer/trycatch-activity-designer.md)