---
title: Dialogo Seleziona operazione (Legacy) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 75b553bd79936db7b6d8aa2f8fe361650d4ef03e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189628"
---
# <a name="choose-operation-dialog-box-legacy"></a>Finestra di dialogo Seleziona operazione (legacy)
Questo argomento viene descritto come usare il **Seleziona operazione** nella finestra di dialogo legacy [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Usare la [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Il **Seleziona operazione** finestra di dialogo consente di selezionare un'operazione da associare a un <xref:System.Workflow.Activities.ReceiveActivity> attività o un <xref:System.Workflow.Activities.SendActivity> attività. Per altre informazioni sull'uso di questa finestra di dialogo con tali attività, vedere [procedura: implementare un'operazione del contratto WCF (Legacy)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) e [procedura: richiamare un'operazione del contratto WCF (Legacy)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md).  
  
 La tabella seguente descrive gli elementi dell'interfaccia utente di **Seleziona operazione** nella finestra di dialogo.  
  
|Elemento dell'interfaccia utente|Descrizione|  
|----------------|-----------------|  
|**Aggiungi contratto**|Crea un nuovo contratto, in cui è possibile definire nuove operazioni. (Utilizzato solo con <xref:System.Workflow.Activities.ReceiveActivity>.)|  
|**L'operazione di aggiunta**|Aggiunge nuove operazioni a un nuovo contratto creato nella **Seleziona operazione** nella finestra di dialogo. **Nota:** è possibile aggiungere nuove operazioni solo ai contratti creati tramite il **Seleziona operazione** nella finestra di dialogo. <br /><br /> (Utilizzato solo con <xref:System.Workflow.Activities.ReceiveActivity>.)|  
|**Importa...**|Importa un contratto definito in precedenza e consente di selezionare un'operazione da tale contratto.|  
|**Nome dell'operazione**|Nome dell'operazione attualmente selezionata. Questa casella di testo è disponibile per la modifica solo se è stata creata un'operazione tramite il **Seleziona operazione** nella finestra di dialogo.|  
|**Parametri**|Scheda contenente le definizioni di parametro per l'operazione attualmente selezionata. **Nota:** le definizioni di parametro possono essere modificate solo se è stata creata un'operazione tramite il **Seleziona operazione** nella finestra di dialogo.|  
|**Proprietà**|Scheda contenente le impostazioni di <xref:System.Net.Security.ProtectionLevel> per i messaggi scambiati fra il client e il servizio. **Nota:** questa scheda è abilitata solo se è stata creata un'operazione tramite il **Seleziona operazione** nella finestra di dialogo.|  
|**Autorizzazioni**|Scheda contenente le proprietà <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> e <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> degli utenti autorizzati a chiamare tale operazione. Ad esempio, se solo gli utenti dal gruppo Administrators sono autorizzati a chiamare tale operazione, quindi si scriverebbe "Administrators" **ruolo** casella di testo.<br /><br /> Questa scheda è abilitata per le operazioni create tramite il **ChooseOperation** finestra di dialogo e le operazioni che sono state importate tramite il **importazione** pulsante.|  
  
> [!NOTE]
>  Il **Seleziona operazione** finestra di dialogo vengono visualizzati solo i contratti o operazioni che vengono usate da altre <xref:System.Workflow.Activities.SendActivity> attività nel flusso di lavoro. Allo stesso modo, il **Seleziona operazione** finestra di dialogo <xref:System.Workflow.Activities.ReceiveActivity> le attività vengono visualizzati solo i contratti o operazioni che vengono usate da altre **ReceiveActivity** attività nel flusso di lavoro.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: implementare un'operazione del contratto WCF (Legacy)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Procedura: richiamare un'operazione del contratto WCF (Legacy)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Finestra di progettazione legacy per la Guida interfaccia utente di Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)