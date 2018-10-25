---
title: Creazione di soluzioni flusso di lavoro di SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c4e808d93d2ae3039d4c5d79d1c14c65360bba32
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892311"
---
# <a name="create-sharepoint-workflow-solutions"></a>Creare soluzioni di flusso di lavoro di SharePoint

[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fornisce strumenti che consentono di creare flussi di lavoro personalizzati che gestiscono il ciclo di vita dei documenti ed elencare elementi in un sito Web di SharePoint. Gli elementi forniti prevedono una finestra di progettazione, un set di controlli dell'attività e i riferimenti all'assembly necessari. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] include anche il **Personalizzazione guidata SharePoint**, per creare e configurare i flussi di lavoro.

Per altre informazioni su SharePoint, vedere [Microsoft SharePoint Products and Technologies](http://go.microsoft.com/fwlink/?LinkId=178470).

## <a name="workflows-in-sharepoint"></a>Flussi di lavoro in SharePoint
 Quando si aggiunge un flusso di lavoro a una raccolta di SharePoint o un elenco, si applica un processo di business su tutti gli elementi nell'elenco o libreria. Un flusso di lavoro vengono descritte le azioni che il sistema o gli utenti devono eseguire su ogni elemento, ad esempio inviare l'elemento da modificare e quindi esaminato. Queste azioni, note come *attività*, sono i blocchi predefiniti del flusso di lavoro.

 È possibile creare flussi di lavoro di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e distribuirli a un sito Web di SharePoint. Dopo aver distribuito un flusso di lavoro in SharePoint, associarlo a una libreria o elenco. Si può quindi essere avviato automaticamente, da un processo, o manualmente dall'utente. Per altre informazioni sull'operazione del flusso di lavoro, vedere [i flussi di lavoro di sviluppo di SharePoint con Visual Studio](https://docs.microsoft.com/sharepoint/dev/general-development/develop-sharepoint-workflows-using-visual-studio).

## <a name="create-custom-sharepoint-workflows"></a>Creare flussi di lavoro di SharePoint personalizzati
 Sono disponibili in due progetti di flusso di lavoro di SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]: **flusso di lavoro sequenziale** e **lavoro macchina a stati**.

 Oggetto *flusso di lavoro sequenza* rappresenta una serie di passaggi. I passaggi vengono eseguiti uno dopo l'altro fino al completamento dell'ultima attività. Flussi di lavoro sequenziali sono sempre strettamente sequenziale la loro esecuzione. Poiché possono ricevere gli eventi esterni e includere flussi di logica parallela, può variare l'esatto ordine di esecuzione. La figura seguente mostra un esempio di flusso di lavoro sequenza.

 ![Flusso di lavoro sequenza](../sharepoint/media/sp-sequential.png "flusso di lavoro sequenza")

 Oggetto *lavoro macchina a stati* rappresenta un set di stati, transizioni e le azioni. Eseguire i passaggi descritti in un flusso di lavoro macchina in modo asincrono. Ciò significa non vengono necessariamente eseguite una dopo l'altra, ma vengono invece generati da azioni e gli stati. Uno stato assegnato come stato iniziale e quindi, in base a un evento, viene effettuata una transizione a un altro stato. La macchina a stati può avere uno stato finale che determina la fine del flusso di lavoro. Il diagramma seguente mostra un esempio di un lavoro macchina a stati.

 ![Stato del flusso di lavoro di Machine](../sharepoint/media/sp-state.png "lo stato del flusso di lavoro di Machine")

 Per altre informazioni sui tipi di flusso di lavoro, vedere [tipi di flusso di lavoro](http://go.microsoft.com/fwlink/?LinkId=178995).

### <a name="use-the-wizard"></a>Utilizzare la procedura guidata
 Quando si crea un progetto di flusso di lavoro di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], è innanzitutto specificare le impostazioni nel **Personalizzazione guidata SharePoint**. La procedura guidata Usa queste impostazioni per creare un progetto in **Esplora soluzioni**. Questo progetto contiene un file di codice, più file che vengono usate per distribuire il flusso di lavoro e fa riferimento agli assembly necessari per creare un flusso di lavoro di SharePoint personalizzato.

 Dopo aver creato il flusso di lavoro, è possibile modificarne le proprietà nella finestra Proprietà. Sebbene la maggior parte delle proprietà del flusso di lavoro possono essere modificate direttamente nella finestra Proprietà, alcune richiedono fare clic su un pulsante con puntini di sospensione (![ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ellisse di ASP.NET Mobile Designer")) per modificare i relativi valori. Questo pulsante Riavvia il **Personalizzazione guidata SharePoint**. Dopo aver apportato la proprietà cambia valore, scegliere il **fine** pulsante per renderle effettive.

> [!NOTE]
>  Il **tipo di flusso di lavoro** proprietà è di sola lettura e non può essere modificata. Se si desidera modificare il tipo di flusso di lavoro, è necessario creare un altro flusso di lavoro.

## <a name="design-a-sharepoint-workflow"></a>Progettare un flusso di lavoro di SharePoint
 Dopo aver definito tutti i passaggi nel processo di business, usare il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Progettazione flussi di lavoro per la progettazione del flusso di lavoro di SharePoint. Per aprire la finestra di progettazione, fare doppio clic su Workflow1.cs o Workflow1.vb in **Esplora soluzioni**, oppure aprire il menu di scelta rapida per uno di questi file e quindi scegliere **aprire**.

### <a name="activities"></a>Attività
 Per progettare un flusso di lavoro, aggiungere le attività eseguite dal **casella degli strumenti** a un *pianificazione del flusso di lavoro* nella finestra di progettazione. Una pianificazione del flusso di lavoro contiene la sequenza di attività nell'ordine che deve essere eseguite.

 Esistono due tipi di attività:

- *Attività semplici* eseguire una singola unità di lavoro, ad esempio "ritarda per un giorno" o "Avvia servizio Web".

- *Le attività composte* contenere altre attività, ad esempio, un'attività condizionale può contenere due rami.

  Sono disponibili in entrambi i tipi di attività di **casella degli strumenti**.

  Attività possono avere proprietà, metodi ed eventi. Usare la **proprietà** finestra per impostare le proprietà di un'attività.

  È anche possibile creare un'attività personalizzata. Per altre informazioni, vedere [procedura dettagliata: creare un'attività flusso di lavoro di sito personalizzati](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md).

  Le attività sono organizzate nelle seguenti schede nel **casella degli strumenti**:

- **Flusso di lavoro SharePoint**

- **Windows Workflow v3.0**

- **Windows Workflow v3.5**

  Non tutte le attività del flusso di lavoro di base sono supportate da SharePoint. Per altre informazioni, vedere [Cenni preliminari sulle attività del flusso di lavoro per Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkID=156094).

#### <a name="sharepoint-workflow-activities"></a>Attività del flusso di lavoro di SharePoint
 Il **flusso di lavoro SharePoint** schede contengono le attività specializzate per l'uso in [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]. Queste attività semplificano lo sviluppo di flussi di lavoro ciclo di vita documento. Per altre informazioni sulle attività elencate nel **flusso di lavoro SharePoint** scheda, vedere [Cenni preliminari sulle attività del flusso di lavoro per Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkID=156094).

#### <a name="windows-workflow-activities"></a>Attività del flusso di lavoro di Windows
 Il **flusso di lavoro di Windows** schede contengono le attività fornite dal [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)]. È possibile utilizzare queste attività per creare pianificazioni di flusso di lavoro per qualsiasi tipo di applicazione di flusso di lavoro di Windows.

 Per altre informazioni sulle attività elencate nel **i flussi di lavoro di Windows** scheda, vedere [attività di Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkID=156096). Per altre informazioni su Windows Workflow Foundation, vedere [Panoramica di Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkID=128632).

### <a name="work-with-activities-in-the-designer"></a>Utilizzare le attività nella finestra di progettazione
 La pianificazione del flusso di lavoro può contenere una combinazione di attività del flusso di lavoro di Windows e le attività del flusso di lavoro di SharePoint.

 La finestra di progettazione vengono visualizzati segnali visivi che consentono di posizionare e configurare le attività in modo corretto. Quando si trascina o si copia un'attività nella pianificazione del flusso di lavoro, nella finestra di progettazione vengono visualizzate delle icone con il segno di addizione (+) in verde che indicano le posizioni valide per quell'attività nel flusso di lavoro. Non è possibile posizionare un'attività in una posizione in cui non sarebbe valido. Ad esempio, è possibile posizionare un'attività di invio come prima attività in un ramo di attività di ascolto. Per altre informazioni, vedere [Centro per sviluppatori di SharePoint Designer](http://go.microsoft.com/fwlink/?LinkId=178476).

## <a name="collect-information-during-the-workflow"></a>Raccogliere informazioni durante il flusso di lavoro
 È possibile raccogliere informazioni dagli utenti in determinati momenti nel flusso di lavoro. È possibile raccogliere informazioni tramite moduli o le proprietà dell'elemento.

### <a name="forms"></a>Moduli
 I moduli sono come le finestre di dialogo che contengono domande e forniscono agli utenti di fornire risposte modi.

 Esistono quattro tipi di form che può essere usato in un flusso di lavoro:

- Associazione

- Avvio

- Modifica

- Attività

  Tra questi, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] include modelli di elementi per i form di associazione e di avvio. Un esempio di un' *form di associazione* è quello che consente all'amministratore di installare il flusso di lavoro immettere i parametri correlati al flusso di lavoro, ad esempio un limite di spesa per un flusso di lavoro di nota spese. Un esempio di un' *form di avvio* è quello che consente all'utente di un flusso di lavoro di spesa di immettere l'importo speso nel flusso di lavoro. Per altre informazioni su questi tipi di form, vedere [SharePoint modelli di elemento di progetto e progetto](../sharepoint/sharepoint-project-and-project-item-templates.md).

### <a name="item-properties"></a>Proprietà degli elementi
 È anche possibile raccogliere informazioni dagli utenti usando le proprietà di un elemento nell'elenco o raccolta di SharePoint. Il file di codice principale (Workflow1.cs o Workflow1.vb) dichiara un'istanza della classe Microsoft.SharePoint.Workflow.SPWorkflowActivationProperties.WorkflowProperties denominata `workflowProperties`. Usare il `workflowProperties` oggetto per accedere alle proprietà della libreria o dell'elenco nel codice. Per un esempio, vedere [procedura dettagliata: creare ed eseguire il debug di una soluzione di flusso di lavoro SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md).

## <a name="debug-a-sharepoint-workflow-template"></a>Eseguire il debug di un modello di flusso di lavoro di SharePoint
 Eseguire il debug di un progetto di flusso di lavoro SharePoint lo stesso quando si esegue il debug di altri [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progetti basati su Web. Quando si avvia il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debugger [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vengono utilizzate le impostazioni specificate nella **Personalizzazione guidata SharePoint** per aprire il sito Web di SharePoint appropriato e associare automaticamente il modello di flusso di lavoro con la libreria appropriata o elenco. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Associa anche il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] del debugger per il [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] processo denominato *w3wp.exe*.

 Per testare il flusso di lavoro, è necessario avviarlo manualmente. Per altre informazioni, vedere la sezione "Il debug dei flussi di lavoro" in [debug delle soluzioni SharePoint](../sharepoint/debugging-sharepoint-solutions.md). Per altre informazioni sulle [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debug delle applicazioni Web, vedere [eseguire il Debug di script e applicazioni web](../debugger/debugging-web-applications-and-script.md).

## <a name="deploy-a-sharepoint-workflow-template"></a>Distribuire un modello di flusso di lavoro di SharePoint
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Distribuire progetti di flusso di lavoro di SharePoint come qualsiasi altro [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progetti SharePoint. Per altre informazioni, vedere [soluzioni del pacchetto e distribuire SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).

## <a name="import-globally-reusable-workflows"></a>Importa i flussi di lavoro riutilizzabile globalmente
 Oltre a creare flussi di lavoro riutilizzabili specifiche del sito, SharePoint Designer consente di creare *flussi di lavoro riutilizzabile globalmente*, quali sono i flussi di lavoro che può essere utilizzati da qualsiasi sito di SharePoint. Il progetto Importa flusso di lavoro riutilizzabili in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] attualmente non è possibile importare flussi di lavoro riutilizzabile globalmente. Tuttavia, è possibile utilizzare SharePoint Designer per convertire un flusso di lavoro riutilizzabile globalmente in un flusso di lavoro riutilizzabile, o importare il flusso di lavoro come un flusso di lavoro dichiarativo non convertito. Per altre informazioni, vedere [elementi di importazione da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Procedura dettagliata: Creare ed eseguire il debug di una soluzione del flusso di lavoro di SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|Illustra la procedura dettagliata illustra la creazione e debug di un semplice [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] flusso di lavoro.|
|[Procedura dettagliata: Creare un flusso di lavoro con form di associazione e di avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|Illustra la procedura dettagliata per la creazione di un più complete [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] flusso di lavoro completato con i form di associazione e di avvio.|
|[Procedura dettagliata: Aggiungere una pagina dell'applicazione a un flusso di lavoro](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|Si basa sull'argomento [procedura dettagliata: creare un flusso di lavoro con form di associazione e di avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) aggiungendo un ulteriore *aspx* pagina dell'applicazione che invia report sui dati immessi nel flusso di lavoro.|
|[Procedura dettagliata: Creare un'attività flusso di lavoro del sito personalizzata](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|Viene illustrato come eseguire due attività fondamentali: creare un flusso di lavoro a livello di sito e creare un'attività flusso di lavoro personalizzato.|
|[Procedura dettagliata: Importare un flusso di lavoro riutilizzabile di SharePoint Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|Viene illustrato come importare flussi di lavoro dichiarativi riutilizzabili creati in SharePoint Designer 2010 in un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progetto SharePoint.|

## <a name="see-also"></a>Vedere anche

- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Build e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Creare le pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)