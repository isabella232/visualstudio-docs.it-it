---
title: Finestra di dialogo Seleziona operazione (legacy) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f2736db7e18733a9477238cafad21088eb135e89
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659166"
---
# <a name="choose-operation-dialog-box-legacy"></a>Finestra di dialogo Seleziona operazione (legacy)
In questo argomento viene descritto come utilizzare la finestra di dialogo **Scegli operazione** in legacy [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Usare la [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 La finestra di dialogo **Scegli operazione** viene utilizzata per selezionare un'operazione da associare a un'attività <xref:System.Workflow.Activities.ReceiveActivity> o a un' <xref:System.Workflow.Activities.SendActivity> attività. Per ulteriori informazioni sull'utilizzo di questa finestra di dialogo con tali attività, vedere [procedura: implementare un'operazione del contratto WCF (legacy)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) e [procedura: richiamare un'operazione del contratto WCF (legacy)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md).

 Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente della finestra di dialogo **Seleziona operazione** .

|Elemento dell'interfaccia utente|Descrizione|
|----------------|-----------------|
|**Aggiungi contratto**|Crea un nuovo contratto, in cui è possibile definire nuove operazioni. (Utilizzato solo con <xref:System.Workflow.Activities.ReceiveActivity>.)|
|**Operazione di aggiunta**|Aggiunge nuove operazioni a un nuovo contratto creato nella finestra di dialogo **Seleziona operazione** . **Nota:**  È possibile aggiungere nuove operazioni solo ai contratti creati tramite la finestra di dialogo **Seleziona operazione** . <br /><br /> (Utilizzato solo con <xref:System.Workflow.Activities.ReceiveActivity>.)|
|**Importa...**|Importa un contratto definito in precedenza e consente di selezionare un'operazione da tale contratto.|
|**Nome operazione**|Nome dell'operazione attualmente selezionata. Questa casella di testo è disponibile per la modifica solo se è stata creata un'operazione tramite la finestra di dialogo **Seleziona operazione** .|
|**Parametri**|Scheda contenente le definizioni di parametro per l'operazione attualmente selezionata. **Nota:**  Le definizioni dei parametri possono essere modificate solo se è stata creata un'operazione tramite la finestra di dialogo **Seleziona operazione** .|
|**Proprietà**|Scheda contenente le impostazioni di <xref:System.Net.Security.ProtectionLevel> per i messaggi scambiati fra il client e il servizio. **Nota:**  Questa scheda è abilitata solo se è stata creata un'operazione tramite la finestra di dialogo **Seleziona operazione** .|
|**Autorizzazioni**|Scheda contenente le proprietà <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> e <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> degli utenti autorizzati a chiamare tale operazione. Se, ad esempio, solo gli utenti del gruppo Administrators sono autorizzati a chiamare tale operazione, è necessario scrivere "Administrators" nella casella di testo **Role** .<br /><br /> Questa scheda è abilitata per entrambe le operazioni create tramite la finestra di dialogo **ChooseOperation** e le operazioni che sono state importate tramite il pulsante **Importa** .|

> [!NOTE]
> Nella finestra di dialogo **Scegli operazione** vengono visualizzati solo i contratti o le operazioni usati da altre <xref:System.Workflow.Activities.SendActivity> attività nel flusso di lavoro. Analogamente, nella finestra di dialogo **Scegli operazione** per le <xref:System.Workflow.Activities.ReceiveActivity> attività vengono visualizzati solo i contratti o le operazioni usati da altre attività **ReceiveActivity** nel flusso di lavoro.

## <a name="see-also"></a>Vedere anche
 [Procedura: implementare un'operazione del contratto WCF (legacy)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) [procedura: richiamare una finestra di progettazione legacy di un'operazione del contratto WCF (legacy)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) [per la guida dell'interfaccia utente di Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)