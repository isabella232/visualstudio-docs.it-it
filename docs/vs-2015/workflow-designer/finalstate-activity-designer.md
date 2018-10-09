---
title: Activity Designer FinalState | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
caps.latest.revision: 5
author: steved0x
ms.author: gewarren
manager: erikre
ms.openlocfilehash: ecbbded923645a1b2bf6eafe9bbe038e0cb3b29c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528130"
---
# <a name="finalstate-activity-designer"></a>ActivityDesigner FinalState
La finestra di progettazione di <xref:System.Activities.Core.Presentation.FinalState> viene usata per creare un <xref:System.Activities.Statements.State> che termina un'istanza della macchina a stati.  
  
## <a name="using-the-finalstate-activity-designer"></a>Uso di ActivityDesigner FinalState  
 Il **FinalState** designer viene utilizzato per creare un <xref:System.Activities.Statements.State> preconfigurato come stato finale in una macchina a stati. Oggetto <xref:System.Activities.Statements.State> che viene creato utilizzando il <xref:System.Activities.Core.Presentation.FinalState> ActivityDesigner ha relativo <xref:System.Activities.Statements.State.IsFinal%2A> proprietà impostata su **true**, non ha alcun <xref:System.Activities.Statements.State.Exit%2A> attività e Nessuna transizione che abbia origine da quest'ultimo. Usare la <xref:System.Activities.Core.Presentation.FinalState> ActivityDesigner di aggiungere un <xref:System.Activities.Statements.State> attività preconfigurata come stato finale in una macchina a stati, trascinare il **FinalState** ActivityDesigner dal **macchina a stati**sezione il **casella degli strumenti** e rilasciarlo nella finestra di progettazione del flusso di lavoro. Un ActivityDesigner di <xref:System.Activities.Core.Presentation.FinalState> può essere rilasciato in <xref:System.Activities.Statements.StateMachine> e le transizioni possono essere aggiunte successivamente, o una transizione può essere creata quando viene rilasciato un ActivityDesigner di <xref:System.Activities.Core.Presentation.FinalState>. Per altre informazioni sulla creazione delle transizioni, vedere [transizione](../workflow-designer/transition-activity-designer.md).  
  
### <a name="state-activity-properties-in-the-workflow-designer"></a>Proprietà dell'attività di stato in Progettazione flussi di lavoro   
 Nella tabella seguente vengono elencate le proprietà di <xref:System.Activities.Core.Presentation.FinalState> che possono essere impostate usando la finestra di progettazione e viene descritta la modalità di utilizzo nella finestra di progettazione. Alcune di queste proprietà possono essere modificate nella griglia delle proprietà, mentre altre possono essere modificate nell'area di progettazione.  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.State> nell'intestazione. Il valore predefinito è **stato**. Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner. <xref:System.Activities.Statements.State.DisplayName%2A> è usato per l'esplorazione tramite la barra di navigazione visualizzata nella parte superiore della Progettazione flussi di lavoro.<br /><br /> Sebbene la proprietà <xref:System.Activities.Statements.State.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|  
|<xref:System.Activities.Statements.State.Entry%2A>|False|Specifica l'azione che si verifica quando viene eseguita la transizione di questo stato. Questo valore può essere impostato trascinando un'attività dal **casella degli strumenti** e rilasciandola il <xref:System.Activities.Statements.State.Entry%2A> sezione dello stato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Istanza di StateMachine](../workflow-designer/statemachine-activity-designer.md)   
 [Stato](../workflow-designer/state-activity-designer.md)   
 [Transition](../workflow-designer/transition-activity-designer.md)