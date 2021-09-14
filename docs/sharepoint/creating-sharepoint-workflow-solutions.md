---
title: Creazione di SharePoint flusso di lavoro | Microsoft Docs
description: Creare SharePoint flusso di lavoro usando gli strumenti per creare flussi di lavoro personalizzati che gestiscono il ciclo di vita di documenti ed elementi di elenco nei SharePoint web.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VSTO.NewSharePointWorkflowWizard.Page3
- VS.SharePointTools.Workflow.WorkflowName
- VSTO.NewSharePointWorkflowWizard.Page2
- VSTO.NewSharePointWorkflowWizard.Page1
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: ba44e9c128cafec7223e5a90b0aa2d37cab6f8e2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635644"
---
# <a name="create-sharepoint-workflow-solutions"></a>Creare soluzioni SharePoint flusso di lavoro

[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]offre strumenti che consentono di creare flussi di lavoro personalizzati che gestiscono il ciclo di vita di documenti ed elementi di elenco in SharePoint sito Web. Gli elementi forniti prevedono una finestra di progettazione, un set di controlli dell'attività e i riferimenti all'assembly necessari. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]include anche la **SharePoint personalizzazione guidata**, che consente di creare e configurare i flussi di lavoro.

Per altre informazioni sui SharePoint, vedere [Prodotti e tecnologie SharePoint Microsoft.](/sharepoint/dev/)

## <a name="workflows-in-sharepoint"></a>Flussi di lavoro in SharePoint
 Quando si aggiunge un flusso di lavoro a una SharePoint o a un elenco, si applica un processo aziendale a tutti gli elementi nella raccolta o nell'elenco. Un flusso di lavoro descrive le azioni che il sistema o gli utenti devono eseguire su ogni elemento, ad esempio l'invio dell'elemento da modificare e quindi rivedere. Queste azioni, note come *attività*, sono i blocchi predefiniti del flusso di lavoro.

 È possibile creare SharePoint flussi di lavoro in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e distribuirli in un SharePoint Web. Dopo aver distribuito un flusso di lavoro SharePoint, associarlo a una raccolta o a un elenco. Può quindi essere avviato automaticamente, da un processo o manualmente da un utente. Per altre informazioni sull'operazione del flusso di lavoro, vedere [Sviluppare SharePoint di lavoro usando Visual Studio](/sharepoint/dev/general-development/develop-sharepoint-workflows-using-visual-studio).

## <a name="create-custom-sharepoint-workflows"></a>Creare flussi di lavoro SharePoint personalizzati
 Due SharePoint flusso di lavoro sono disponibili in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] : Flusso di lavoro **sequenziale** e Flusso di lavoro **macchina a stati.**

 Un *flusso di lavoro sequenziale* rappresenta una serie di passaggi. I passaggi vengono eseguiti uno dopo l'altro fino al completamento dell'ultima attività. I flussi di lavoro sequenziali sono sempre strettamente sequenziali durante l'esecuzione. Poiché possono ricevere eventi esterni e includere flussi logici paralleli, l'ordine esatto di esecuzione può variare. Nella figura seguente viene illustrato un esempio di flusso di lavoro sequenziale.

 ![Flusso di lavoro sequenziale](../sharepoint/media/sp-sequential.png "Flusso di lavoro sequenziale")

 Un *flusso di lavoro* della macchina a stati rappresenta un set di stati, transizioni e azioni. I passaggi in un flusso di lavoro della macchina a stati vengono eseguiti in modo asincrono. Ciò significa che non vengono necessariamente eseguite una dopo l'altra, ma vengono attivate da azioni e stati. Uno stato viene assegnato come stato iniziale e quindi, in base a un evento, viene effettuata una transizione a un altro stato. La macchina a stati può avere uno stato finale che determina la fine del flusso di lavoro. Il diagramma seguente mostra un esempio di flusso di lavoro di una macchina a stati.

 ![StateMachineWorkflow](../sharepoint/media/sp-state.png "StateMachineWorkflow")

 Per altre informazioni sui tipi di flusso di lavoro, vedere [Tipi di flusso di lavoro.](/previous-versions/office/developer/sharepoint-2010/ms468447(v=office.14))

### <a name="use-the-wizard"></a>Usare la procedura guidata
 Quando si crea un progetto SharePoint flusso di lavoro in , è necessario specificarne innanzitutto le impostazioni [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nella **SharePoint personalizzazione guidata .** La procedura guidata usa queste impostazioni per creare un progetto in **Esplora soluzioni**. Questo progetto contiene un file di codice, diversi file usati per distribuire il flusso di lavoro e riferimenti ad assembly necessari per creare un flusso di lavoro SharePoint personalizzato.

 Dopo aver creato il flusso di lavoro, è possibile modificarne le proprietà nel Finestra Proprietà. Sebbene la maggior parte delle proprietà del flusso di lavoro possa essere modificata direttamente nel Finestra Proprietà, per alcune è necessario fare clic su un pulsante con i puntini di sospensione (![ASP.NET puntini](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")di sospensione di Progettazione dispositivi mobili ) per modificarne i valori. Questo pulsante riavvia la **personalizzazione SharePoint personalizzazione guidata**. Dopo aver apportato le modifiche al valore della proprietà, scegliere **il pulsante Fine** per finalizzarle.

> [!NOTE]
> La **proprietà Workflow Type** è di sola lettura e non può essere modificata. Se si desidera modificare il tipo di flusso di lavoro, è necessario creare un altro flusso di lavoro.

## <a name="design-a-sharepoint-workflow"></a>Progettare un flusso SharePoint lavoro
 Dopo aver definito tutti i passaggi del processo aziendale, utilizzare la finestra di progettazione del flusso di lavoro per progettare il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint lavoro. Per aprire la finestra di progettazione, fare doppio clic su Workflow1.cs o Workflow1.vb in **Esplora soluzioni** oppure aprire il menu di scelta rapida per uno di questi file e quindi scegliere **Apri.**

### <a name="activities"></a>Attività
 Per progettare un flusso di lavoro, aggiungere attività **dalla** casella degli strumenti a una pianificazione del flusso *di lavoro* nella finestra di progettazione. Una pianificazione del flusso di lavoro contiene la sequenza di attività nell'ordine in cui devono essere eseguite.

 Sono disponibili due tipi di attività:

- *Le attività* semplici eseguono una singola unità di lavoro, ad esempio "ritardare di 1 giorno" o "avviare il servizio Web".

- *Le attività composite* contengono altre attività. Ad esempio, un'attività condizionale può contenere due rami.

  Entrambi i tipi di attività sono disponibili nella casella degli **strumenti**.

  Le attività possono avere proprietà, metodi ed eventi. Usare la **finestra** Proprietà per impostare le proprietà di un'attività.

  È anche possibile creare un'attività personalizzata. Per altre informazioni, vedere Procedura [dettagliata: Creare un'attività personalizzata del flusso di lavoro del sito.](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)

  Le attività sono organizzate nelle schede seguenti della casella degli **strumenti**:

- **SharePoint Workflow**

- **Windows Flusso di lavoro v3.0**

- **Windows Flusso di lavoro v3.5**

  Non tutte le attività principali del flusso di lavoro sono supportate da SharePoint. Per altre informazioni, vedere [Workflow Activities for Windows SharePoint Services Overview](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

#### <a name="sharepoint-workflow-activities"></a>SharePoint attività del flusso di lavoro
 Le **schede SharePoint del flusso di** lavoro contengono attività specializzate da usare in [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] . Queste attività semplificano e semplificano lo sviluppo di flussi di lavoro del ciclo di vita dei documenti. Per altre informazioni sulle attività elencate nella scheda Flusso **SharePoint,** vedere [Workflow Activities for Windows SharePoint Services Overview](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

#### <a name="windows-workflow-activities"></a>Windows attività del flusso di lavoro
 Le **Windows del flusso** di lavoro contengono le attività fornite da [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)] . È possibile utilizzare queste attività per creare pianificazioni del flusso di lavoro per qualsiasi tipo di Windows flusso di lavoro.

 Per altre informazioni sulle attività elencate nella scheda Flussi **Windows,** vedere Windows [Workflow Foundation Activities](/previous-versions/dotnet/netframework-3.5/ms733615(v=vs.90)). Per altre informazioni su Windows Workflow Foundation, vedere Windows [Workflow Foundation Overview](/previous-versions/dotnet/netframework-3.5/ms734631(v=vs.90)).

### <a name="work-with-activities-in-the-designer"></a>Usare le attività nella finestra di progettazione
 La pianificazione del flusso di lavoro può contenere una combinazione di attività Windows flusso di lavoro e SharePoint flusso di lavoro.

 La finestra di progettazione visualizza segnali visivi che consentono di posizionare e configurare correttamente le attività. Quando si trascina o si copia un'attività nella pianificazione del flusso di lavoro, nella finestra di progettazione vengono visualizzate delle icone con il segno di addizione (+) in verde che indicano le posizioni valide per quell'attività nel flusso di lavoro. Non è possibile posizionare un'attività in una posizione in cui non sarebbe valida. Ad esempio, non è possibile posizionare un'attività Send come prima attività in un ramo di attività Listen. Per altre informazioni, vedere [SharePoint Designer Developer Center.](https://developer.microsoft.com/office/docs)

## <a name="collect-information-during-the-workflow"></a>Raccogliere informazioni durante il flusso di lavoro
 Potrebbe essere necessario raccogliere informazioni dagli utenti in orari predefiniti nel flusso di lavoro. È possibile raccogliere informazioni usando i moduli o le proprietà degli elementi.

### <a name="forms"></a>Moduli
 I moduli sono simili a finestre di dialogo che contengono domande e consentono agli utenti di fornire risposte.

 Esistono quattro tipi di moduli che possono essere usati in un flusso di lavoro:

- Association Rules

- Iniziazione

- Modifica

- Attività

  Di questi, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] include modelli di elemento per i moduli di associazione e avvio. Un esempio di *modulo* di associazione è quello che consente all'amministratore che installa il flusso di lavoro di immettere parametri correlati al flusso di lavoro, ad esempio un limite di spesa per un flusso di lavoro di spesa. Un esempio di modulo *di avvio è* quello che consente all'utente di un flusso di lavoro di spesa di immettere l'importo speso nel flusso di lavoro. Per altre informazioni su questi tipi di moduli, vedere Modelli di SharePoint [di progetto e di elemento di progetto.](../sharepoint/sharepoint-project-and-project-item-templates.md)

### <a name="item-properties"></a>Proprietà degli elementi
 È anche possibile raccogliere informazioni dagli utenti usando le proprietà di un elemento nel SharePoint o nell'elenco. Il file di codice principale (Workflow1.cs o Workflow1.vb) dichiara un'istanza di Microsoft. SharePoint. Classe Workflow.SPWorkflowActivationProperties.WorkflowProperties denominata `workflowProperties` . Usare `workflowProperties` l'oggetto per accedere alle proprietà della libreria o dell'elenco nel codice. Per un esempio, vedere [Procedura dettagliata: Creare ed eseguire il debug](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)di una SharePoint flusso di lavoro.

## <a name="debug-a-sharepoint-workflow-template"></a>Eseguire il debug di un modello SharePoint flusso di lavoro
 È possibile eseguire il debug di SharePoint progetto flusso di lavoro come si esegue il debug di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] altri progetti basati sul Web. Quando si avvia il debugger, utilizza le impostazioni specificate nella Personalizzazione guidata SharePoint per aprire il sito Web SharePoint appropriato e associare automaticamente il modello di flusso di lavoro alla raccolta o all'elenco [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] appropriato.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] collega anche il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debugger al processo denominato [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] *w3wp.exe*.

 Per testare il flusso di lavoro, è necessario avviarlo manualmente. Per altre informazioni, vedere la sezione "Debug dei flussi di lavoro" in [Debug SharePoint soluzioni](../sharepoint/debugging-sharepoint-solutions.md). Per altre informazioni sul debug [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] di applicazioni Web, vedere [Eseguire il debug di applicazioni Web e script](../debugger/how-to-enable-debugging-for-aspnet-applications.md).

## <a name="deploy-a-sharepoint-workflow-template"></a>Distribuire un modello SharePoint flusso di lavoro
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint flusso di lavoro vengono distribuiti come altri [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint progetto. Per altre informazioni, vedere [Creare pacchetti e distribuire SharePoint soluzioni](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).

## <a name="import-globally-reusable-workflows"></a>Importare flussi di lavoro riutilizzabili a livello globale
 Oltre a creare flussi di lavoro riutilizzabili specifici del sito, SharePoint Designer consente di creare flussi di lavoro riutilizzabili a livello globale, ovvero flussi di lavoro che possono essere usati da qualsiasi SharePoint sito.  Il progetto Importa flusso di lavoro riutilizzabile in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] attualmente non importa flussi di lavoro riutilizzabili a livello globale. Tuttavia, è possibile usare SharePoint Designer per convertire un flusso di lavoro riutilizzabile a livello globale in un flusso di lavoro riutilizzabile o importarlo come flusso di lavoro dichiarativo non convertito. Per altre informazioni, vedere [Importare elementi da un sito SharePoint esistente.](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Procedura dettagliata: Creare ed eseguire il debug di una soluzione SharePoint flusso di lavoro](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|Guida l'utente nella creazione e nel debug di un flusso di lavoro [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] semplice.|
|[Procedura dettagliata: Creare un flusso di lavoro con moduli di associazione e avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|Guida l'utente passo dopo passo alla creazione di un flusso di lavoro più completo completo di moduli di associazione [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e avvio.|
|[Procedura dettagliata: Aggiungere una pagina dell'applicazione a un flusso di lavoro](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|Si basa sull'argomento [Procedura dettagliata:](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) Creare un flusso di lavoro con moduli di associazione e avvio aggiungendo una pagina dell'applicazione *aspx* aggiuntiva che segnala i dati immessi nel flusso di lavoro.|
|[Procedura dettagliata: Creare un'attività del flusso di lavoro del sito personalizzata](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|Illustra come eseguire due attività chiave: creare un flusso di lavoro a livello di sito e creare un'attività del flusso di lavoro personalizzata.|
|[Procedura dettagliata: Importare un flusso SharePoint designer riutilizzabile in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|Illustra come importare flussi di lavoro dichiarativi riutilizzabili creati in SharePoint Designer 2010 in un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint progetto.|

## <a name="see-also"></a>Vedi anche

- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Build e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Creare pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)