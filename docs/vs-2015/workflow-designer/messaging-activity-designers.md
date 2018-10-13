---
title: Activity Designer Messaging | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 897e63cf-a42f-4edd-876f-c4ccfffaf6d6
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 254b8d819da8cd1d06d21699940c3b118aa75119
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49274755"
---
# <a name="messaging-activity-designers"></a>ActivityDesigner Messaggistica
Gli ActivityDesigner Messaging vengono usati per creare e configurare attività di messaggistica che comportano l'invio e la ricezione di messaggi [!INCLUDE[indigo1](../includes/indigo1-md.md)] in un'applicazione [!INCLUDE[wf](../includes/wf-md.md)]. [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] include cinque attività di messaggistica e in [!INCLUDE[wfd1](../includes/wfd1-md.md)] sono disponibili due nuove finestre di progettazione dei modelli che consentono di gestire la messaggistica all'interno di un flusso di lavoro. Gli argomenti contenuti in questa sezione, ed elencati nella tabella seguente, forniscono materiale sussidiario sull'utilizzo degli ActivityDesigner e dei modelli di progettazione in [!INCLUDE[wfd2](../includes/wfd2-md.md)].  
  
## <a name="in-this-section"></a>In questa sezione  
  
|Attività Messaggio|Descrizione|  
|----------------------|-----------------|  
|[CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)|Crea e configura un'attività <xref:System.ServiceModel.Activities.CorrelationScope> che consente la gestione implicita delle attività di messaggistica figlio con un oggetto <xref:System.ServiceModel.Activities.CorrelationHandle>.|  
|[InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)|Crea e configura un'attività <xref:System.ServiceModel.Activities.InitializeCorrelation> che viene usata per inizializzare la correlazione senza inviare o ricevere un messaggio.|  
|[Receive](../workflow-designer/receive-activity-designer.md)|Crea e configura un'attività <xref:System.ServiceModel.Activities.Receive> che riceve un messaggio da un servizio.|  
|[ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)|Crea una coppia preconfigurata delle attività <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply> all'interno di un'attività <xref:System.Activities.Statements.Sequence>.|  
|[Send](../workflow-designer/send-activity-designer.md)|Crea e configura un'attività <xref:System.ServiceModel.Activities.Send> che invia un messaggio a un servizio.|  
|[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)|Crea una coppia preconfigurata delle attività <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply> all'interno di un'attività <xref:System.Activities.Statements.Sequence>.|  
|[TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)|Crea e configura un'attività <xref:System.ServiceModel.Activities.TransactedReceiveScope> che consente il flusso di transazioni in un flusso di lavoro.|  
  
## <a name="reference"></a>Riferimenti  
 <xref:System.Activities.Activity>  
  
 <xref:System.ServiceModel.Activities.CorrelationScope>  
  
 <xref:System.ServiceModel.Activities.Receive>  
  
 <xref:System.ServiceModel.Activities.Send>  
  
 <xref:System.ServiceModel.Activities.ReceiveReply>  
  
 <xref:System.ServiceModel.Activities.SendReply>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope>  
  
## <a name="related-sections"></a>Sezioni correlate  
 Per gli altri tipi di ActivityDesigner, vedere gli argomenti seguenti.  
  
 [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)  
  
 [Uso degli Activity Designer](../workflow-designer/using-the-activity-designers.md)  
  
 [Diagramma di flusso](../workflow-designer/flowchart-activity-designers.md)  
  
 [Runtime](../workflow-designer/runtime-activity-designers.md)  
  
 [Primitive](../workflow-designer/primitives-activity-designers.md)  
  
 [Transazione](../workflow-designer/transaction-activity-designers.md)  
  
 [Raccolta](../workflow-designer/collection-activity-designers.md)  
  
 [Gestione degli errori](../workflow-designer/error-handling-activity-designers.md)  
  
## <a name="external-resources"></a>Risorse esterne  
 [Uso degli Activity Designer](../workflow-designer/using-the-activity-designers.md)