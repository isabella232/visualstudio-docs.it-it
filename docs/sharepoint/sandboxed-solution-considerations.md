---
title: Considerazioni sulle soluzioni in modalità sandbox | Microsoft Docs
description: Esplorare le soluzioni in modalità sandbox, una funzionalità di Microsoft SharePoint che consente agli utenti della raccolta siti di caricare soluzioni di codice personalizzate.
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 156ebc7fa17d53fd56cb8b069698f0bdf4b9a43c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092813"
---
# <a name="sandboxed-solution-considerations"></a>Considerazioni sulle soluzioni in modalità sandbox
  *Le soluzioni sandbox* sono una funzionalità di Microsoft SharePoint 2010 che consente agli utenti della raccolta siti di caricare soluzioni di codice personalizzate. Una soluzione comune in modalità sandbox è che gli utenti caricano i propri Web part.

 Un'applicazione SharePoint sandbox viene eseguita in un processo protetto e monitorato che ha accesso a una parte limitata del Web farm. Microsoft SharePoint 2010 usa una combinazione di funzionalità, raccolte di soluzioni, monitoraggio delle soluzioni e un framework di convalida per abilitare soluzioni sandbox.

## <a name="specify-project-trust-level"></a>Specificare il livello di attendibilità del progetto
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]supporta soluzioni sandbox tramite una proprietà di progetto booleana denominata *Soluzione sandbox.* Questa proprietà può essere impostata in qualsiasi momento nel progetto oppure può essere specificata quando si crea il progetto nella SharePoint **personalizzazione guidata**.

> [!NOTE]
> La modifica *della proprietà Soluzione sandbox* di un progetto dopo la creazione può causare errori di convalida.

 La soluzione viene considerata una soluzione con ambito farm se la proprietà Soluzione in modalità *sandbox* è impostata su **false** o se si sceglie l'opzione Distribuisci come **soluzione farm.** Tuttavia, la soluzione viene trattata in modo diverso da una soluzione farm se la proprietà Soluzione in modalità *sandbox* è impostata su **true** o se si sceglie l'opzione Distribuisci come soluzione in **modalità sandbox** nella procedura guidata.

## <a name="sharepoint-site-hierarchy"></a>SharePoint gerarchia del sito
 Per comprendere il funzionamento delle soluzioni sandbox, è utile sapere che i SharePoint sono gerarchici nell'ambito. L'elemento superiore è noto come Web farm e altri elementi sono subordinati:

 Web Farm

 Applicazione Web A

 Raccolta siti A1

 Sito A1a

 Applicazione Web B

 Raccolta siti B1

 Sito B1a

 Sito B1b

 Raccolta siti B2

 Sito B2a

 Come si può vedere, le Web farm possono contenere una o più applicazioni Web, che a loro volta possono contenere una o più raccolte siti, che possono avere siti secondari e così via. Le modifiche apportate a una raccolta siti influiscono solo su tale raccolta siti e non su altre. Tuttavia, le modifiche apportate a Web farm livello di sito influiscono su tutte le raccolte siti nella farm.

 Windows SharePoint Services (WSS) 3.0 consente di distribuire soluzioni solo a livello di farm, ma consente di eseguire la distribuzione a livello di farm (soluzione farm) o a livello di raccolta siti [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] (soluzione sandbox).

## <a name="why-sandboxed-solutions"></a>Perché le soluzioni in modalità sandbox?
 In WSS 3.0 le soluzioni possono essere distribuite solo a livello di farm. Ciò significa che è possibile distribuire soluzioni potenzialmente dannose o destabilizzanti che hanno interessato l'intero Web farm e tutte le altre raccolte siti e tutte le altre applicazioni eseguite in esso. Tuttavia, usando soluzioni sandbox, è possibile distribuire le soluzioni in un'area secondaria della farm, una raccolta siti specifica. Per fornire protezione aggiuntiva, l'assembly della soluzione non viene caricato nel processo [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] principale (*w3wp.exe*). Viene invece caricato in un processo separato (*SPUCWorkerProcess.exe*). Questo processo viene monitorato e implementa quote e limitazioni per proteggere la farm da soluzioni sandbox che eseguono attività dannose, ad esempio l'esecuzione di cicli rigidi che utilizzano cicli della CPU.

## <a name="site-collection-solution-gallery"></a>Raccolta soluzioni raccolta siti
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 dispone di una funzionalità nota come "raccolta di soluzioni della raccolta siti". È possibile accedere a questa funzionalità dalla pagina Amministrazione centrale di SharePoint 2010 o aprendo il **menu**  Azioni sito, scegliendo **Impostazioni** sito e quindi scegliendo il collegamento Soluzioni in **Raccolte** nel sito di SharePoint. Le raccolte soluzioni sono repository di soluzioni che consentono agli amministratori delle raccolte siti di gestire le soluzioni nelle raccolte siti.

 La raccolta di soluzioni è una raccolta documenti archiviata nel Web radice del SharePoint sito. La raccolta di soluzioni sostituisce i modelli di sito e supporta i pacchetti della soluzione. Quando viene caricato SharePoint file del pacchetto della soluzione (con estensione *wsp),* questo viene elaborato come soluzione in modalità sandbox.

## <a name="sandboxed-solution-limitations"></a>Limitazioni delle soluzioni in modalità sandbox
 Quando viene distribuita una soluzione in modalità sandbox, la gamma di funzionalità SharePoint disponibili è limitata per ridurre eventuali vulnerabilità di sicurezza. Di seguito sono riportate alcune di queste limitazioni:

- Le soluzioni sandbox hanno a disposizione un subset limitato di elementi di soluzioni distribuibili. I modelli di SharePoint, ad esempio le definizioni del sito e i flussi di lavoro, non sono disponibili.

- SharePoint esegue il codice della soluzione sandbox in un processo (*SPUCWorkerProcess.exe*) separato dal processo del pool di applicazioni principale [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] (*w3wp.exe*).

- Le cartelle mappate non possono essere aggiunte al progetto.

- Tipi [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] nell'assembly Microsoft.Office. Il server non può essere usato nelle soluzioni sandbox. Inoltre, solo i tipi [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] nell'assembly Microsoft.SharePoint possono essere usati nelle soluzioni sandbox.

  È importante notare che la specifica di una soluzione SharePoint come soluzione sandbox non ha alcun effetto sul server SharePoint; determina solo il modo in cui SharePoint progetto viene distribuito in SharePoint da e gli assembly a [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] cui viene associato. Non influisce sul file con estensione *wsp* generato e il file con estensione *wsp* non contiene dati direttamente correlati alla proprietà *Sandboxed Solution.*

## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>Funzionalità ed elementi nelle soluzioni sandbox
 Le soluzioni sandbox supportano le funzionalità e gli elementi seguenti:

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

- Supporto per tutti i Web part che derivano da`System.Web.UI.WebControls.WebParts.WebPart`

- web part

- Elementi della funzionalità WebTemplate *(anzichéWebtemp.xml*)

- Visual Web part

  Le soluzioni sandbox non supportano le funzionalità e gli elementi seguenti:

- Pagine dell'applicazione

- Gruppo di azioni personalizzate

- Funzionalità con ambito farm

- Elemento `HideCustomAction`

- Funzionalità con ambito applicazione Web

- Flussi di lavoro con codice

## <a name="see-also"></a>Vedi anche
- [Differenze tra soluzioni sandbox e soluzioni farm](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)
- [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
