---
title: ActivityDesigner While | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fae1b4905d66a5162591fd7c720ba81ed7ffda82
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72606613"
---
# <a name="while-activity-designer"></a>ActivityDesigner While

L' <xref:System.Activities.Statements.While> attività esegue l'attività contenuta in <xref:System.Activities.Statements.While.Body%2A> mentre la condizione specificata restituisce **true**. L'attività contenuta potrebbe non essere mai eseguita. Se si desidera eseguirla almeno una volta, usare l'attività <xref:System.Activities.Statements.DoWhile>.

## <a name="while-properties-in-workflow-designer"></a>Proprietà di While in Progettazione flussi di lavoro

Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.While> e ne viene descritta la modalità di utilizzo nella finestra di progettazione.

|Nome proprietà|Obbligatoria|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.While> nell'intestazione. Il valore predefinito è While. Il valore può essere modificato nella finestra **Proprietà** o direttamente nell'intestazione Activity Designer.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.While.Body%2A>|Falso|Contiene l'attività da eseguire mentre l'oggetto <xref:System.Activities.Statements.While.Condition%2A> restituisce **true**.|
|<xref:System.Activities.Statements.While.Condition%2A>|Vero|Contiene l'espressione [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] valutata per determinare se è necessario eseguire l'attività contenuta in <xref:System.Activities.Statements.While.Body%2A>.|

## <a name="see-also"></a>Vedere anche

- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)