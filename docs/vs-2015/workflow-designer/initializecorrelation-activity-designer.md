---
title: Activity Designer InitializeCorrelation | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 314b5de716017d4c5c40653eed678626f00c20ba
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540739"
---
# <a name="initializecorrelation-activity-designer"></a>ActivityDesigner InitializeCorrelation
Il **InitializeCorrelation** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.ServiceModel.Activities.InitializeCorrelation> attività che viene usato per stabilire una correlazione tra i messaggi prima dell'invio o riceverli.  
  
## <a name="the-initializecorrelation-activity"></a>Attività InitializeCorrelation  
 Un'attività <xref:System.ServiceModel.Activities.InitializeCorrelation> viene usata per inizializzare le correlazioni senza inviare o ricevere un messaggio. La correlazione viene in genere inizializzata quando si invia o riceve un messaggio. Se è necessario stabilire la correlazione prima che un messaggio venga inviato o ricevuto, usare <xref:System.ServiceModel.Activities.InitializeCorrelation> per inizializzarla.  
  
### <a name="using-the-initializecorrelation-activity-designer"></a>Utilizzo dell'ActivityDesigner InitializeCorrelation  
 Il **InitializeCorrelation** ActivityDesigner è reperibile nel **messaggistica** categoria del **della casella degli strumenti**, accessibile facendo clic di **della casella degli strumenti**  scheda il [!INCLUDE[wfd2](../includes/wfd2-md.md)] (in alternativa, selezionare **sulla barra degli strumenti** dal **visualizzazione** menu o CTRL + ALT + X.)  
  
 Il **InitializeCorrelation** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie. Ciò consente di creare un <xref:System.ServiceModel.Activities.InitializeCorrelation> attività con un valore predefinito <xref:System.Activities.Activity.DisplayName%2A> di InitializeCorrelation.The <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **InitializeCorrelation** ActivityDesigner o nel  **DisplayName** finestra di **proprietà** finestra.  
  
 Il <xref:System.ServiceModel.Activities.CorrelationHandle> può essere specifica nel **correlazione** campo **delle proprietà** finestra nel **InitializeCorrelation** superficie dell'ActivityDesigner.  
  
 Facendo clic sul pulsante ellisse oltre il **CorrelationData** campo **proprietà** finestra o la "visualizzazione..." Suggerimento di testo sul **InitializeCorrelation** superficie dell'ActivityDesigner viene visualizzato il **Inizializza correlazione** finestra di dialogo in cui è possibile specificare l'handle di correlazione e le coppie chiave-valore utilizzate per inizializzarlo. [!INCLUDE[crabout](../includes/crabout-md.md)] tramite questa finestra di dialogo, vedere la [finestra di dialogo Editor raccolta di tipo](../workflow-designer/type-collection-editor-dialog-box.md) argomento.  
  
### <a name="the-initializecorrelation-properties"></a>Proprietà di InitializeCorrelation  
 Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.InitializeCorrelation> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Queste proprietà possono essere modificate nella **delle proprietà** finestra o scegliere [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie.  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.ServiceModel.Activities.InitializeCorrelation>. Il valore predefinito è InitializeCorrelation.<br /><br /> Sebbene non sia obbligatorio specificare un valore non predefinito per la proprietà descrittiva <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> usato per associare le attività del flusso di lavoro nella correlazione.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Dizionario dei dati di correlazione che mette in correlazione i messaggi all'istanza del flusso di lavoro.<br /><br /> Usare la **Inizializza correlazione** finestra di dialogo per configurare il <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. [!INCLUDE[crabout](../includes/crabout-md.md)] Utilizzare questa finestra di dialogo, vedere la [finestra di dialogo Editor raccolta di tipo](../workflow-designer/type-collection-editor-dialog-box.md) argomento.|  
  
## <a name="see-also"></a>Vedere anche  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [Ricezione](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Invia](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)