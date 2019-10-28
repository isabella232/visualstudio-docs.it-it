---
title: Creazione di soluzioni flusso di lavoro SharePoint | Microsoft Docs
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f4139760995d655dbeb4e1c76d164f21949a9b50
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984564"
---
# <a name="create-sharepoint-workflow-solutions"></a>Creazione di soluzioni flusso di lavoro SharePoint

[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] offre strumenti che consentono di creare flussi di lavoro personalizzati che gestiscono il ciclo di vita dei documenti e degli elementi dell'elenco in un sito Web di SharePoint. Gli elementi forniti prevedono una finestra di progettazione, un set di controlli dell'attività e i riferimenti all'assembly necessari. per la creazione e la configurazione dei flussi di lavoro, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] inoltre inclusa la **procedura guidata di personalizzazione di SharePoint**.

Per ulteriori informazioni su SharePoint, vedere [prodotti e tecnologie Microsoft SharePoint](/sharepoint/dev/).

## <a name="workflows-in-sharepoint"></a>Flussi di lavoro in SharePoint
 Quando si aggiunge un flusso di lavoro a una raccolta o a un elenco di SharePoint, viene applicato un processo di business su tutti gli elementi della raccolta o dell'elenco. Un flusso di lavoro descrive le azioni che il sistema o gli utenti devono eseguire su ogni elemento, ad esempio l'invio dell'elemento da modificare e quindi la revisione. Queste azioni, note come *attività*, sono i blocchi predefiniti del flusso di lavoro.

 È possibile creare flussi di lavoro di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e distribuirli in un sito Web di SharePoint. Dopo la distribuzione di un flusso di lavoro in SharePoint, è possibile associarlo a una raccolta o a un elenco. Può quindi essere avviato automaticamente, da un processo o manualmente da un utente. Per altre informazioni sulle operazioni del flusso di lavoro, vedere [sviluppare flussi di lavoro SharePoint con Visual Studio](/sharepoint/dev/general-development/develop-sharepoint-workflows-using-visual-studio).

## <a name="create-custom-sharepoint-workflows"></a>Creazione di flussi di lavoro SharePoint personalizzati
 Sono disponibili due progetti di flusso di lavoro di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]: flusso di lavoro **sequenziale** e **flusso di lavoro della macchina a stati**.

 Un *flusso di lavoro sequenziale* rappresenta una serie di passaggi. I passaggi vengono eseguiti uno dopo l'altro fino al completamento dell'ultima attività. I flussi di lavoro sequenziali sono sempre rigorosamente sequenziali nell'esecuzione. Poiché possono ricevere eventi esterni e includere flussi logici paralleli, l'ordine di esecuzione esatto può variare. Nella figura seguente viene illustrato un esempio di flusso di lavoro sequenziale.

 ![Flusso di lavoro sequenziale](../sharepoint/media/sp-sequential.png "Flusso di lavoro sequenziale")

 Un *flusso di lavoro della macchina a stati* rappresenta un set di Stati, transizioni e azioni. I passaggi nel flusso di lavoro di una macchina a stati vengono eseguiti in modo asincrono. Ciò significa che non vengono necessariamente eseguiti uno dopo l'altro, ma vengono invece attivati da azioni e Stati. Uno stato viene assegnato come stato di avvio e quindi, in base a un evento, viene eseguita una transizione a un altro stato. La macchina a stati può avere uno stato finale che determina la fine del flusso di lavoro. Il diagramma seguente mostra un esempio di flusso di lavoro di una macchina a Stati.

 ![Flusso di lavoro macchina a Stati](../sharepoint/media/sp-state.png "StateMachineWorkflow")

 Per ulteriori informazioni sui tipi di flussi di lavoro, vedere [tipi di flussi di lavoro](/previous-versions/office/developer/sharepoint-2010/ms468447(v=office.14)).

### <a name="use-the-wizard"></a>Utilizzare la procedura guidata
 Quando si crea un progetto flusso di lavoro di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], è necessario innanzitutto specificarne le impostazioni nella **procedura guidata di personalizzazione di SharePoint**. La procedura guidata usa queste impostazioni per creare un progetto in **Esplora soluzioni**. Questo progetto contiene un file di codice, diversi file utilizzati per distribuire il flusso di lavoro e i riferimenti agli assembly necessari per creare un flusso di lavoro di SharePoint personalizzato.

 Dopo aver creato il flusso di lavoro, è possibile modificarne le proprietà nella Finestra Proprietà. Anche se la maggior parte delle proprietà del flusso di lavoro può essere modificata direttamente nella Finestra Proprietà, è necessario fare clic su un pulsante con i puntini di sospensione (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")) per modificarne i valori. Questo pulsante Riavvia la **personalizzazione guidata SharePoint**. Dopo aver apportato le modifiche al valore della proprietà, fare clic sul pulsante **fine** per finalizzarle.

> [!NOTE]
> La proprietà del **tipo di flusso di lavoro** è di sola lettura e non può essere modificata. Se si desidera modificare il tipo di flusso di lavoro, è necessario creare un altro flusso di lavoro.

## <a name="design-a-sharepoint-workflow"></a>Progettare un flusso di lavoro di SharePoint
 Dopo aver definito tutti i passaggi del processo di business, utilizzare la finestra di progettazione del flusso di lavoro [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] per progettare il flusso di lavoro di SharePoint. Per aprire la finestra di progettazione, fare doppio clic su Workflow1.cs o Workflow1. vb in **Esplora soluzioni**oppure aprire il menu di scelta rapida per uno di questi file, quindi scegliere **Apri**.

### <a name="activities"></a>Attività
 Per progettare un flusso di lavoro, aggiungere attività dalla **casella degli strumenti** a una *pianificazione del flusso di lavoro* nella finestra di progettazione. Una pianificazione del flusso di lavoro contiene la sequenza di attività nell'ordine in cui devono essere eseguite.

 Esistono due tipi di attività:

- Le *attività semplici* eseguono una singola unità di lavoro, ad esempio "ritardo per 1 giorno" o "Avvia servizio Web".

- Le *attività composite* contengono altre attività; ad esempio, un'attività condizionale potrebbe contenere due rami.

  Entrambi i tipi di attività sono disponibili nella **casella degli strumenti**.

  Le attività possono avere proprietà, metodi ed eventi. Utilizzare la finestra **Proprietà** per impostare le proprietà di un'attività.

  È anche possibile creare un'attività personalizzata. Per ulteriori informazioni, vedere [procedura dettagliata: creare un'attività del flusso di lavoro del sito personalizzata](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md).

  Le attività sono organizzate nelle schede seguenti della **casella degli strumenti**:

- **Flusso di lavoro di SharePoint**

- **Windows Workflow v 3.0**

- **Windows Workflow versione 3.5**

  Non tutte le attività di base del flusso di lavoro sono supportate da SharePoint. Per ulteriori informazioni, vedere [Cenni preliminari sulle attività del flusso di lavoro per Windows SharePoint Services](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

#### <a name="sharepoint-workflow-activities"></a>Attività del flusso di lavoro di SharePoint
 Le schede del **flusso di lavoro di SharePoint** contengono attività specializzate da usare in [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]. Queste attività semplificano e semplificano lo sviluppo di flussi di lavoro del ciclo di vita dei documenti. Per ulteriori informazioni sulle attività elencate nella scheda **flusso di lavoro SharePoint** , vedere [Cenni preliminari sulle attività del flusso di lavoro per Windows SharePoint Services](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

#### <a name="windows-workflow-activities"></a>Attività di Windows Workflow
 Le schede dei **flussi di lavoro di Windows** contengono le attività fornite dal [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)]. È possibile utilizzare queste attività per creare pianificazioni del flusso di lavoro per qualsiasi tipo di applicazione Windows Workflow.

 Per ulteriori informazioni sulle attività elencate nella scheda **flussi di lavoro di Windows** , vedere [attività Windows Workflow Foundation](/previous-versions/dotnet/netframework-3.5/ms733615(v=vs.90)). Per ulteriori informazioni sulla Windows Workflow Foundation, vedere [Panoramica di Windows Workflow Foundation](/previous-versions/dotnet/netframework-3.5/ms734631(v=vs.90)).

### <a name="work-with-activities-in-the-designer"></a>Usare le attività nella finestra di progettazione
 La pianificazione del flusso di lavoro può contenere una combinazione di attività di Windows Workflow e attività del flusso di lavoro di SharePoint.

 Nella finestra di progettazione vengono visualizzati i segnali visivi per facilitare la posizione e la configurazione corretta delle attività. Quando si trascina o si copia un'attività nella pianificazione del flusso di lavoro, nella finestra di progettazione vengono visualizzate delle icone con il segno di addizione (+) in verde che indicano le posizioni valide per quell'attività nel flusso di lavoro. Non è possibile posizionare un'attività in una posizione in cui non sarebbe valida. Non è ad esempio possibile posizionare un'attività Send come prima attività in un ramo dell'attività Listen. Per ulteriori informazioni, vedere [centro per sviluppatori di SharePoint Designer](https://developer.microsoft.com/office/docs).

## <a name="collect-information-during-the-workflow"></a>Raccogli informazioni durante il flusso di lavoro
 Potrebbe essere necessario raccogliere informazioni dagli utenti in orari predefiniti del flusso di lavoro. È possibile raccogliere informazioni usando i form o le proprietà degli elementi.

### <a name="forms"></a>Moduli
 I moduli sono simili alle finestre di dialogo che contengono domande e forniscono modi per consentire agli utenti di fornire risposte.

 Sono disponibili quattro tipi di form che possono essere utilizzati in un flusso di lavoro:

- Associazione

- Avvio

- Modifica

- Attività

  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] include modelli di elementi per i form di associazione e di avvio. Un esempio di un *modulo di associazione* è quello che consente all'amministratore di installare il flusso di lavoro di immettere i parametri relativi al flusso di lavoro, ad esempio un limite di spesa per un flusso di lavoro delle spese. Un esempio di un *modulo di avvio* è quello che consente all'utente di un flusso di lavoro di spesa di immettere la quantità di tempo trascorsa nel flusso di lavoro. Per ulteriori informazioni su questi tipi di form, vedere [modelli di progetto e di elementi di progetto SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

### <a name="item-properties"></a>Proprietà elemento
 È anche possibile raccogliere informazioni dagli utenti usando le proprietà di un elemento nella raccolta o nell'elenco di SharePoint. Il file di codice principale (Workflow1.cs o Workflow1. vb) dichiara un'istanza della classe Microsoft. SharePoint. Workflow. SPWorkflowActivationProperties. WorkflowProperties denominata `workflowProperties`. Utilizzare l'oggetto `workflowProperties` per accedere alle proprietà della raccolta o dell'elenco nel codice. Per un esempio, vedere [procedura dettagliata: creare ed eseguire il debug di una soluzione flusso di lavoro di SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md).

## <a name="debug-a-sharepoint-workflow-template"></a>Eseguire il debug di un modello di flusso di lavoro SharePoint
 È possibile eseguire il debug di un progetto di flusso di lavoro SharePoint nello stesso modo in cui si esegue il debug di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] altri progetti basati sul Web Quando si avvia il debugger [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilizza le impostazioni specificate nella **procedura guidata di personalizzazione di SharePoint** per aprire il sito Web di SharePoint appropriato e associare automaticamente il modello di flusso di lavoro alla libreria appropriata o elenco. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] connette inoltre il debugger [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] al processo [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] denominato *w3wp. exe*.

 Per eseguire il test del flusso di lavoro, è necessario avviarlo manualmente. Per ulteriori informazioni, vedere la sezione "debug dei flussi di lavoro" in [debug di soluzioni SharePoint](../sharepoint/debugging-sharepoint-solutions.md). Per altre informazioni sul debug di applicazioni Web [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], vedere [eseguire il debug di script e applicazioni Web](../debugger/how-to-enable-debugging-for-aspnet-applications.md).

## <a name="deploy-a-sharepoint-workflow-template"></a>Distribuire un modello di flusso di lavoro di SharePoint
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i progetti di flusso di lavoro SharePoint vengono distribuiti esattamente come gli altri progetti [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint. Per altre informazioni, vedere creare [pacchetti e distribuire soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).

## <a name="import-globally-reusable-workflows"></a>Importare flussi di lavoro riutilizzabili a livello globale
 Oltre alla creazione di flussi di lavoro riutilizzabili specifici del sito, SharePoint Designer consente di creare *flussi di lavoro riutilizzabili a livello globale*, ovvero flussi di lavoro che possono essere utilizzati da qualsiasi sito di SharePoint. Il progetto di flusso di lavoro di importazione riutilizzabile in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] attualmente non importa i flussi di lavoro riutilizzabili a livello globale. Tuttavia, è possibile utilizzare SharePoint Designer per convertire un flusso di lavoro riutilizzabile a livello globale in un flusso di lavoro riutilizzabile o importare il flusso di lavoro come flusso di lavoro dichiarativo non convertito. Per ulteriori informazioni, vedere [importare elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Procedura dettagliata: creare ed eseguire il debug di una soluzione flusso di lavoro SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|Guida dettagliata alla creazione e al debug di un semplice flusso di lavoro di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|
|[Procedura dettagliata: creare un flusso di lavoro con form di associazione e di avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|Guida dettagliata alla creazione di un flusso di lavoro di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con funzionalità complete completate con i moduli di associazione e di avvio.|
|[Procedura dettagliata: aggiungere una pagina dell'applicazione a un flusso di lavoro](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|Si basa sull'argomento [procedura dettagliata: creare un flusso di lavoro con i form di associazione e di avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) aggiungendo una pagina dell'applicazione *aspx* aggiuntiva che segnala i dati immessi nel flusso di lavoro.|
|[Procedura dettagliata: creare un'attività personalizzata del flusso di lavoro del sito](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|Viene illustrato come eseguire due attività principali: creare un flusso di lavoro a livello di sito e creare un'attività personalizzata del flusso di lavoro.|
|[Procedura dettagliata: importare un flusso di lavoro riutilizzabile di SharePoint Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|Viene illustrato come importare flussi di lavoro dichiarativi riutilizzabili creati in SharePoint Designer 2010 in un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progetto SharePoint.|

## <a name="see-also"></a>Vedere anche

- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Build e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Creazione di pagine applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)