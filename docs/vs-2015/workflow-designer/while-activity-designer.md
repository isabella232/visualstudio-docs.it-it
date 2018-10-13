---
title: Activity Designer while | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 529978a9303892aed74a5d490a19b542357303f9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263159"
---
# <a name="while-activity-designer"></a>ActivityDesigner While

Il <xref:System.Activities.Statements.While> attività viene eseguita l'attività contenuta nel relativo <xref:System.Activities.Statements.While.Body%2A> mentre la condizione specificata restituisce **true**. L'attività contenuta potrebbe non essere mai eseguita. Se si desidera eseguirla almeno una volta, usare l'attività <xref:System.Activities.Statements.DoWhile>.

## <a name="while-properties-in-workflow-designer"></a>Proprietà di While in Progettazione flussi di lavoro

Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.While> e ne viene descritta la modalità di utilizzo nella finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.While> nell'intestazione. Il valore predefinito è While. Il valore può essere modificato nel **proprietà** finestra o direttamente nell'intestazione dell'ActivityDesigner.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.While.Body%2A>|False|Contiene l'attività da eseguire durante la <xref:System.Activities.Statements.While.Condition%2A> restituisca **true**.|
|<xref:System.Activities.Statements.While.Condition%2A>|True|Contiene l'espressione [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] valutata per determinare se è necessario eseguire l'attività contenuta in <xref:System.Activities.Statements.While.Body%2A>.|

## <a name="see-also"></a>Vedere anche

- [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)