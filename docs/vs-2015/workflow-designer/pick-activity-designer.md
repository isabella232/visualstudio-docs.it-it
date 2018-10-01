---
title: Activity Designer Pick | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: d5bf361d2217c199fa2818a94c441e1d2b105e7f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518466"
---
# <a name="pick-activity-designer"></a>ActivityDesigner Pick
Nell'attività <xref:System.Activities.Statements.Pick> è disponibile il flusso di controllo basato sugli eventi. L'attività esegue uno di diversi rami in risposta a un evento di attivazione.  
  
## <a name="the-pick-activity"></a>Attività Pick  
 Un'attività <xref:System.Activities.Statements.Pick> contiene una raccolta di oggetti <xref:System.Activities.Statements.PickBranch>, uno dei quali può essere eseguito dall'attività <xref:System.Activities.Statements.Pick> per effetto di un evento in entrata che funge da trigger. In questo modo [!INCLUDE[wfd1](../includes/wfd1-md.md)] consente la modellazione di un flusso di controllo basato sugli eventi. Ciascun oggetto <xref:System.Activities.Statements.PickBranch> contiene una proprietà <xref:System.Activities.Statements.PickBranch.Trigger%2A> e una proprietà <xref:System.Activities.Statements.PickBranch.Action%2A>. All'inizio dell'esecuzione di un'attività <xref:System.Activities.Statements.Pick>, tutte le attività del trigger degli elementi <xref:System.Activities.Statements.PickBranch> sono pianificate. Quando la prima attività viene completata, l'attività dell'azione corrispondente è pianificata e tutte le altre attività del trigger sono annullate.  
  
### <a name="how-to-use-the-pick-activity-designer"></a>Modalità di utilizzo dell'ActivityDesigner Pick  
 Il **seleziona** ActivityDesigner è reperibile nel **flusso di controllo** categoria del **della casella degli strumenti**, accessibile facendo clic il **della casella degli strumenti**scheda [!INCLUDE[wfd2](../includes/wfd2-md.md)] (in alternativa, selezionare **sulla barra degli strumenti** dal **visualizzazione** menu o CTRL + ALT + X.)  
  
 Il **Scegli** ActivityDesigner può essere trascinato dal **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie ovunque gli ActivityDesigner sono normalmente posizionati, ad esempio all'interno di un  **Sequenza** ActivityDesigner. Dopo averlo rilasciato in [!INCLUDE[wfd2](../includes/wfd2-md.md)], viene creata un'attività <xref:System.Activities.Statements.Pick> che per impostazione predefinita contiene due attività <xref:System.Activities.Statements.PickBranch> vuote come elementi i cui nomi visualizzati sono Branch1 e Branch2. I rispettivi <xref:System.Activities.Statements.PickBranch.DisplayName%2A> i valori delle proprietà possono essere modificati nella **PickBranch** intestazione ActivityDesigner o all'interno di **proprietà** finestra per ogni ramo.  
  
 Esistono due modi per aggiungere <xref:System.Activities.Statements.PickBranch> attività alla raccolta di un <xref:System.Activities.Statements.Pick> oggetto: trascinando la **PickBranch** della finestra di progettazione dal **della casella degli strumenti** o tramite il menu di scelta rapida da all'interno di **prelievo** nell'area di progettazione. Per informazioni dettagliate, vedere la [PickBranch](../workflow-designer/pickbranch-activity-designer.md) argomento. Si noti che l'unico elemento che possono essere inserito in una **prelievo** ActivityDesigner è un **PickBranch** ActivityDesigner.  
  
### <a name="pick-activity-properties-in-the-workflow-designer"></a>Proprietà dell'attività di prelievo in Progettazione flussi di lavoro  
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Pick> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area della finestra di progettazione.  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.Pick> nell'intestazione. Il valore predefinito è Pick. Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'uso.|  
  
## <a name="see-also"></a>Vedere anche  
 [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)   
 [Attività di selezione](http://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e)   
 [Uso dell'attività Pick](http://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)