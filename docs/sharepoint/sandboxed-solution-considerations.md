---
title: Considerazioni sulla soluzione sandbox | Microsoft Docs
description: Esplora le soluzioni sandbox, una funzionalità di Microsoft SharePoint che consente agli utenti della raccolta siti di caricare le proprie soluzioni di codice personalizzate.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 17b310a3f992f80b04ad14bb6e038e05b009a4af
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2020
ms.locfileid: "95970469"
---
# <a name="sandboxed-solution-considerations"></a>Considerazioni sulla soluzione sandbox
  Le *soluzioni in modalità sandbox* sono una funzionalità di Microsoft SharePoint 2010 che consente agli utenti della raccolta siti di caricare le proprie soluzioni di codice personalizzate. Una soluzione sandbox comune è rappresentata dagli utenti che caricano i propri Web part.

 Un'applicazione SharePoint in modalità sandbox viene eseguita in un processo protetto e monitorato che ha accesso a una parte limitata della Web farm. Microsoft SharePoint 2010 utilizza una combinazione di funzionalità, raccolte di soluzioni, monitoraggio delle soluzioni e un Framework di convalida per abilitare le soluzioni create mediante sandbox.

## <a name="specify-project-trust-level"></a>Specificare il livello di attendibilità del progetto
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] supporta le soluzioni create mediante sandbox tramite una proprietà di progetto booleana denominata *soluzione creata mediante sandbox*. Questa proprietà può essere impostata in qualsiasi momento nel progetto oppure può essere specificata quando si crea il progetto nella **procedura guidata di personalizzazione di SharePoint**.

> [!NOTE]
> La modifica della proprietà della *soluzione creata mediante sandbox* di un progetto dopo che è stata creata può causare errori di convalida.

 La soluzione è considerata una soluzione con ambito farm se la proprietà della *soluzione creata mediante sandbox* è impostata su **false** o si sceglie l'opzione **Distribuisci come soluzione farm** . Tuttavia, la soluzione viene trattata in modo diverso rispetto a una soluzione farm se la proprietà della *soluzione creata mediante sandbox* è impostata su **true** o se si sceglie l'opzione **Distribuisci come soluzione creata mediante sandbox** nella procedura guidata.

## <a name="sharepoint-site-hierarchy"></a>Gerarchia del sito di SharePoint
 Per comprendere il funzionamento delle soluzioni sandbox, è utile sapere che i siti di SharePoint sono gerarchici nell'ambito. L'elemento top è noto come Web farm e altri elementi sono subordinati:

 Web Farm

 Applicazione Web A

 Raccolta siti a1

 A1A sito

 Applicazione Web B

 Raccolta siti B1

 B1a sito

 B1b sito

 Raccolta siti B2

 B2A sito

 Come si può notare, le Web farm possono contenere una o più applicazioni Web, che a loro volta possono contenere una o più raccolte siti, che possono avere siti secondari e così via. Le modifiche apportate a una raccolta siti hanno effetto solo su tale raccolta siti e nessun altro. Tuttavia, le modifiche apportate a livello di Web farm hanno effetto su tutte le raccolte siti nella farm.

 Windows SharePoint Services (WSS) 3,0 consente di distribuire soluzioni solo a livello di farm, ma consente di eseguire [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] la distribuzione a livello di farm (soluzione farm) o a livello di raccolta siti (soluzione creata mediante sandbox).

## <a name="why-sandboxed-solutions"></a>Perché le soluzioni in modalità sandbox?
 In WSS 3,0, le soluzioni potrebbero essere distribuite solo a livello di farm. Ciò significava che potrebbero essere distribuite soluzioni potenzialmente dannose o destabilite che hanno interessato l'intera Web farm e tutte le altre raccolte siti e applicazioni in esecuzione. Tuttavia, usando le soluzioni create mediante sandbox, è possibile distribuire le soluzioni in una sottoarea della farm, una raccolta di siti specifica. Per garantire una protezione aggiuntiva, l'assembly della soluzione non viene caricato nel [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] processo principale (*w3wp.exe*). Viene invece caricato in un processo separato (*SPUCWorkerProcess.exe*). Questo processo viene monitorato e implementa quote e limitazioni per proteggere la farm da soluzioni create mediante sandbox che eseguono attività dannose, ad esempio l'esecuzione di cicli rigidi che utilizzano i cicli della CPU.

## <a name="site-collection-solution-gallery"></a>Raccolta di soluzioni della raccolta siti
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 dispone di una funzionalità nota come "raccolta di soluzioni della raccolta siti". È possibile accedere a questa funzionalità dalla pagina Amministrazione centrale SharePoint 2010 o aprendo il menu **Azioni sito** , scegliendo **Impostazioni sito**, quindi scegliere il collegamento **soluzioni** in  **raccolte** nel sito di SharePoint. Le raccolte di soluzioni sono repository di soluzioni che consentono agli amministratori della raccolta siti di gestire le soluzioni nelle raccolte siti.

 La raccolta soluzioni è una raccolta documenti archiviata nel Web radice del sito di SharePoint. La raccolta soluzioni sostituisce i modelli di sito e supporta i pacchetti della soluzione. Quando viene caricato un file del pacchetto della soluzione SharePoint (con *estensione wsp*), questo viene elaborato come una soluzione creata mediante sandbox.

## <a name="sandboxed-solution-limitations"></a>Limitazioni della soluzione sandbox
 Quando viene distribuita una soluzione in modalità sandbox, la matrice di funzionalità di SharePoint disponibile è limitata per ridurre le vulnerabilità di sicurezza che può avere. Di seguito sono riportate alcune di queste limitazioni:

- Le soluzioni create mediante sandbox hanno un subset limitato di elementi della soluzione distribuibile disponibili. I modelli di progetto SharePoint potenzialmente vulnerabili, ad esempio le definizioni dei siti e i flussi di lavoro, non sono disponibili.

- SharePoint esegue codice della soluzione sandbox in un processo (*SPUCWorkerProcess.exe*) separato dal processo principale del [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] pool di applicazioni (*w3wp.exe*).

- Non è possibile aggiungere cartelle mappate al progetto.

- I tipi nell' [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] assembly Microsoft. Office. Server non possono essere utilizzati nelle soluzioni create mediante sandbox. Inoltre, solo i tipi nell' [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] assembly Microsoft. SharePoint possono essere utilizzati nelle soluzioni create mediante sandbox.

  È importante tenere presente che la specifica di una soluzione SharePoint come soluzione creata mediante sandbox non ha alcun effetto su SharePoint Server. determina solo il modo in cui il progetto SharePoint viene distribuito in SharePoint da [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e gli assembly a cui viene eseguita l'associazione. Non influisce sul file con *estensione wsp* generato e il file con estensione *WSP* non contiene dati direttamente correlati alla proprietà della *soluzione creata mediante sandbox* .

## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>Funzionalità ed elementi nelle soluzioni create mediante sandbox
 Le soluzioni in modalità sandbox supportano le funzionalità e gli elementi seguenti:

- Tipi di contenuto/campi

- Azioni personalizzate

- Flussi di lavoro dichiarativi

- Ricevitori di eventi

- Callout delle funzionalità

- Elencare le definizioni

- Elencare le istanze

- Modulo/file

- Spostamento

- *Onet.xml*

- SPItemEventReceiver

- SPListEventReceiver

- SPWebEventReceiver

- Supporto per tutti i Web part che derivano da `System.Web.UI.WebControls.WebParts.WebPart`

- web part

- Elementi della funzionalità WebTemplate (anziché *Webtemp.xml*)

- Web part Visual

  Le soluzioni create mediante sandbox non supportano le funzionalità e gli elementi seguenti:

- Pagine applicazione

- Gruppo di azione personalizzato

- Funzionalità con ambito farm

- Elemento `HideCustomAction`

- Funzionalità con ambito applicazione Web

- Flussi di lavoro con codice

## <a name="see-also"></a>Vedi anche
- [Differenze tra soluzioni create mediante sandbox e farm](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)
- [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
