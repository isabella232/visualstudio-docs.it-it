---
title: Activity Designer TryCatch | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 74b54ef6b82e4f98ab94972b5d9b0155c16060a9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49240994"
---
# <a name="trycatch-activity-designer"></a>ActivityDesigner TryCatch
Il **TryCatch** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.TryCatch> attività.  
  
## <a name="the-trycatch-activity"></a>Attività TryCatch  
 Il <xref:System.Activities.Statements.TryCatch> attività contiene un <xref:System.Activities.Statements.TryCatch.Try%2A> attività, una raccolta di **Catch\<TException >** e un <xref:System.Activities.Statements.TryCatch.Finally%2A> attività. Oggetto <xref:System.Activities.Statements.Catch%601> typu **TException** contiene un' <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> e un <xref:System.Activities.Statements.Catch%601.Action%2A>. che vengono usate insieme per implementare un meccanismo tipico di gestione degli errori basato sulle eccezioni. Un'attività <xref:System.Activities.Statements.TryCatch> tenta di eseguire la relativa attività <xref:System.Activities.Statements.TryCatch.Try%2A>. Se il <xref:System.Activities.Statements.TryCatch.Try%2A> attività genera un'eccezione, il <xref:System.Activities.Statements.TryCatch> utilizza attività relativo **intercettare < TException\>**  insieme in corrispondenza dell'eccezione. Se non esiste una corrispondenza, il <xref:System.Activities.Statements.Catch%601.Action%2A> dell'oggetto corrispondente **Catch\<TException >** viene eseguita, che funge dalla logica per l'eccezione di gestione degli errori. Se le attività nella sezione di <xref:System.Activities.Statements.TryCatch.Try%2A> o le attività in <xref:System.Activities.Statements.TryCatch.Catches%2A> terminano in modo corretto, l'attività di <xref:System.Activities.Statements.TryCatch> esegue la relativa attività di <xref:System.Activities.Statements.TryCatch.Finally%2A>. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Le eccezioni](http://msdn.microsoft.com/library/065205cc-52dd-4f30-9578-b17d8d113136).  
  
### <a name="using-the-trycatch-activity-designer"></a>Utilizzo dell'ActivityDesigner TryCatch  
 Il **TryCatch** ActivityDesigner è reperibile nel **Error Handling** categoria del **della casella degli strumenti**, accessibile facendo clic di **dellacaselladeglistrumenti** sul lato sinistro della scheda il [!INCLUDE[wfd2](../includes/wfd2-md.md)] (in alternativa, selezionare **sulla barra degli strumenti** dal **visualizzazione** menu o CTRL + ALT + X.)  
  
 Il **TryCatch** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie ovunque posizionate le attività vengono in genere, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. In questo modo viene creata un'attività <xref:System.Activities.Statements.TryCatch> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito TryCatch. Il <xref:System.Activities.Activity.DisplayName%2A> possibile modificare il valore nell'intestazione del **TryCatch** ActivityDesigner o nel **DisplayName** finestra della griglia delle proprietà. Le altre proprietà devono essere modificate nell'area della **TryCatch** ActivityDesigner.  
  
 Fare clic sul pulsante di espansione nell'angolo superiore destro della **TryCatch** finestra di progettazione per visualizzare i **provare**, **intercetta**, e **infine** finestre nel visualizzazione espansa. Per aggiungere un blocco catch, fare clic sui **Aggiungi nuovo catch** sul pulsante **TryCatch** finestra di progettazione. Il pulsante diventa una casella combinata del tipo. Selezionare un tipo di eccezione e premere INVIO per aggiungere il catch. Dopo l'aggiunta di un **Catch**, l'area catch si espande e può rilasciare un'attività nel catch per definire la logica di esecuzione per il catch. Si noti la presenza di una casella di testo a destra dell'area dei catch espansa. Questa casella consente di assegnare un nome alla variabile dell'eccezione. La variabile dell'eccezione può essere utilizzata solo per le attività all'interno della stessa **Catch**.  
  
 Il **TryCatch** finestra di progettazione non supporta la modifica **Catch**. Se si desidera modificare il tipo di eccezione, è necessario eliminare il **Catch** e aggiungerne uno nuovo. Oggetto **intercettare** può essere eliminato selezionandolo e l'eliminazione o tramite il **eliminare** menu nel menu di scelta rapida accessibile facendo clic con il pulsante destro.  
  
### <a name="the-trycatch-properties"></a>Proprietà di TryCatch  
 La tabella seguente illustra il <xref:System.Activities.Statements.TryCatch>proprietà e viene descritto come usarle nella finestra di progettazione.  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.TryCatch>. Il percorso predefinito è TryCatch.|  
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|L'attività è stata eseguita per prima quando viene eseguito <xref:System.Activities.Statements.TryCatch>.|  
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|La raccolta di **intercettare** gli elementi da controllare quando i <xref:System.Activities.Statements.TryCatch.Try%2A> attività genera un'eccezione.<br /><br /> È necessario aggiungere almeno un'attività in <xref:System.Activities.Statements.TryCatch.Catches%2A> o un'attività nel blocco <xref:System.Activities.Statements.TryCatch.Finally%2A>.|  
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|L'attività da eseguire quando <xref:System.Activities.Statements.TryCatch.Try%2A> e qualsiasi attività necessaria nella raccolta <xref:System.Activities.Statements.TryCatch.Catches%2A> completano l'esecuzione.<br /><br /> È necessario aggiungere almeno un'attività in <xref:System.Activities.Statements.TryCatch.Catches%2A> o un'attività nel blocco <xref:System.Activities.Statements.TryCatch.Finally%2A>.|  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolta](../workflow-designer/collection-activity-designers.md)   
 [Rethrow](../workflow-designer/rethrow-activity-designer.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)