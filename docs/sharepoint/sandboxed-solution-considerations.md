---
title: Considerazioni sulle soluzioni create mediante sandbox | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SandboxedSolutions
- VS.SharePointTools.Security.SandboxedSolutions
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 28bdf4e9b116522256606bc9fbbe6b05edb45114
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872976"
---
# <a name="sandboxed-solution-considerations"></a>Considerazioni sulle soluzioni create mediante sandbox
  *Soluzioni create mediante sandbox* sono una funzionalità di Microsoft SharePoint 2010 che consente agli utenti di raccolta siti caricare le proprie soluzioni di codice personalizzato. Una soluzione creata mediante sandbox comune è utenti di caricare le proprie Web part.  
  
 Un'applicazione in modalità sandbox di SharePoint viene eseguito in un processo sicuro e monitorato con accesso a una parte limitata di Web farm. Microsoft SharePoint 2010 Usa una combinazione di funzionalità, le raccolte di soluzioni, soluzioni di monitoraggio e un framework di convalida per abilitare soluzioni create mediante sandbox.  
  
## <a name="specify-project-trust-level"></a>Specificare il livello di attendibilità di progetto
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] supporta soluzioni create mediante sandbox tramite una proprietà del progetto booleano chiamate *soluzione creata mediante sandbox*. Questa proprietà può essere impostata in qualsiasi momento nel progetto, o può essere specificato quando si crea il progetto nel **Personalizzazione guidata SharePoint**.  
  
> [!NOTE]  
>  Modifica il *soluzione creata mediante sandbox* proprietà di un progetto dopo la creazione può causare errori di convalida.  
  
 La soluzione viene considerata una soluzione con ambito farm se la *soluzione creata mediante sandbox* è impostata su **false** o si sceglie il **Distribuisci come soluzione farm** opzione. Tuttavia, la soluzione viene trattata in modo diverso da una soluzione farm se la *soluzione creata mediante sandbox* è impostata su **true** o si sceglie il **Distribuisci come soluzione creata mediante sandbox** opzione della procedura guidata.  
  
## <a name="sharepoint-site-hierarchy"></a>Gerarchia dei siti di SharePoint
 Per comprendere come sandbox soluzioni, è opportuno sapere che siti di SharePoint sono gerarchici nell'ambito. L'elemento all'inizio è nota come Web farm e gli altri elementi sono subordinati a esso:  
  
 Web Farm  
  
 Applicazione Web A  
  
 Raccolta siti A1  
  
 Site A1a  
  
 Applicazione Web B  
  
 Raccolta siti B1  
  
 Site B1a  
  
 Site B1b  
  
 Raccolta siti B2  
  
 Site B2a  
  
 Come può notare, le Web farm può contenere uno o più applicazioni Web, che a sua volta possono contenere uno o più raccolte siti, che possono avere siti secondari e così via. Modifiche apportate a una raccolta siti influiscono solo tale raccolta e nessun altro. Tuttavia, le modifiche apportate a livello di farm Web influiscono su tutte le raccolte di siti nella farm.  
  
 Windows SharePoint Services (WSS) 3.0 consente di distribuire soluzioni solo a livello di farm, ma [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] consente di distribuire a livello di farm (soluzione farm) oppure a livello di raccolta siti (soluzione creata mediante sandbox).  
  
## <a name="why-sandboxed-solutions"></a>Il motivo per cui soluzioni create mediante sandbox?
 In WSS 3.0, soluzioni può essere distribuite solo a livello di farm. Questo significava che è stato possibile distribuire soluzioni potenzialmente dannose o destabilizzanti che interessata l'intera farm Web e tutte le altre raccolte siti e applicazioni in esecuzione sotto di esso. Tuttavia, usando le soluzioni create mediante sandbox, è possibile distribuire le soluzioni in un'area secondaria della farm, ovvero una raccolta siti. Per fornire protezione aggiuntiva, l'assembly della soluzione non viene caricato nel principale [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] processo (*w3wp.exe*). Al contrario, viene caricato in un processo separato (*SPUCWorkerProcess.exe*). Questo processo viene monitorato e implementa quote e limitazioni per proteggere la farm da soluzioni create mediante sandbox che eseguono attività dannose, ad esempio l'esecuzione di cicli rigidi cicli della CPU.  
  
## <a name="site-collection-solution-gallery"></a>Soluzioni della raccolta siti
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 dispone di una funzionalità nota come "raccolta di soluzioni della raccolta siti". È possibile accedere a questa funzionalità dalla pagina di amministrazione centrale SharePoint 2010 o aprendo il **Azioni sito** menu, scegliendo **le impostazioni del sito**e quindi scegliendo il **soluzioni** collegamento sotto **Galleries** nel sito di SharePoint. Le raccolte di soluzioni sono repository delle soluzioni che consentono agli amministratori raccolta siti gestire le soluzioni nelle proprie raccolte siti.  
  
 La raccolta di soluzioni è una raccolta di documenti archiviata nella radice Web del sito di SharePoint. La raccolta di soluzioni sostituisce i modelli di sito e supporta i pacchetti della soluzione. Quando un pacchetto della soluzione SharePoint (*wsp*) file viene caricato, viene elaborato come soluzione creata mediante sandbox.  
  
## <a name="sandboxed-solution-limitations"></a>Limitazioni delle soluzioni create mediante sandbox
 Quando si distribuisce una soluzione creata mediante sandbox, la matrice delle funzionalità di SharePoint disponibili per il processo è limitata per ridurre qualsiasi vulnerabilità della sicurezza che può avere. Alcune di queste limitazioni includono quanto segue:  
  
- Le soluzioni create mediante sandbox hanno un subset limitato di elementi di soluzione da distribuire a loro disposizione. Modelli di progetto SharePoint potenzialmente vulnerabili, ad esempio le definizioni di sito e i flussi di lavoro, non sono disponibili.  
  
- SharePoint viene eseguito il codice della soluzione creata mediante sandbox in un processo (*SPUCWorkerProcess.exe*) separata dalla pagina principale [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] pool di applicazioni (*w3wp.exe*) processo.  
  
- Cartelle mappate non possono essere aggiunto al progetto.  
  
- Tipi di [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] assembly Microsoft.Office.Server non possono essere utilizzati in soluzioni create mediante sandbox. Inoltre, solo i tipi nel [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] assembly Microsoft. SharePoint possono essere utilizzati in soluzioni create mediante sandbox.  
  
  È importante notare che se si specifica una soluzione di SharePoint come una soluzione creata mediante sandbox non ha alcun effetto su SharePoint server. solo determina come viene distribuito il progetto di SharePoint a SharePoint da [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e gli assembly associati a. Non interessa generato *wsp* file e il *wsp* file non contiene dati che è direttamente correlata al *soluzione creata mediante sandbox* proprietà.  
  
## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>Funzionalità e gli elementi in soluzioni create mediante sandbox
 Soluzioni create mediante sandbox supportano le funzionalità e gli elementi seguenti:  
  
- Campi di tipi di contenuto  
  
- Azioni personalizzate  
  
- Flussi di lavoro dichiarativi  
  
- Ricevitori di eventi  
  
- Callout di funzionalità  
  
- Definizioni di elenco  
  
- Istanze di elenco  
  
- Modulo/file  
  
- Navigazione  
  
- *Onet.xml*  
  
- SPItemEventReceiver  
  
- SPListEventReceiver  
  
- SPWebEventReceiver  
  
- Supporto per tutte le Web part che derivano da `System.Web.UI.WebControls.WebParts.WebPart`  
  
- Web part  
  
- Funzionalità webtemplate (invece di *webtemp*)  
  
- Web part visive  
  
  Soluzioni create mediante sandbox non supportano le funzionalità e gli elementi seguenti:  
  
- Pagine dell'applicazione  
  
- Gruppo di azione personalizzato  
  
- Funzionalità con ambito farm  
  
- elemento `HideCustomAction`  
  
- Funzionalità con ambito di applicazione Web  
  
- Flussi di lavoro con codice  
  
## <a name="see-also"></a>Vedere anche
 [Differenze tra modalità sandbox e soluzioni farm](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)   
 [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
