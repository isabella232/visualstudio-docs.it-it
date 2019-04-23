---
title: 'Procedura dettagliata: Importa un flusso di lavoro riutilizzabile di SharePoint Designer in Visual Studio | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.WSPImport.ImportWF
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing reusable workflows
- reusable workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 702c671922d8ea7a1552504be062b7b31de16a09
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60053936"
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio"></a>Procedura dettagliata: Importa un flusso di lavoro riutilizzabile di SharePoint Designer in Visual Studio
  Questa procedura dettagliata illustra come importare un flusso di lavoro riutilizzabile creati in SharePoint Designer 2010 in un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progetto flusso di lavoro di SharePoint.

 Flussi di lavoro creati in SharePoint Designer, oppure *flussi di lavoro dichiarativi*, costituiti da [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] istruzioni anziché codice. SharePoint Designer 2010 introduce *flussi di lavoro riutilizzabili*, che sono portabili e dichiarative dei flussi di lavoro che può essere utilizzati da diversi elenchi nei siti di SharePoint.

 Flussi di lavoro creati [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], ad esempio flussi di lavoro macchina a stati e sequenziali, vengono chiamati *flussi di lavoro di codice*. I flussi di lavoro di codice sono costituiti da file XML e i moduli di codice in cui gli utenti possono personalizzare il comportamento del flusso di lavoro.

 Tramite Visual Studio è possibile importare flussi di lavoro riutilizzabili creati in SharePoint Designer 2010 e convertirli in flussi di lavoro di codice per utilizzarli nei siti di SharePoint.

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di un flusso di lavoro semplice e riutilizzabili in SharePoint Designer.

- Esportare il flusso di lavoro riutilizzabile di SharePoint Designer a un *wsp* file e in SharePoint.

- L'importazione le *wsp* del file in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usando il progetto Importa flusso di lavoro riutilizzabile.

- Modifica il flusso di lavoro mediante l'aggiunta di codice.

- Usando il flusso di lavoro importato in un sito di SharePoint.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e SharePoint.

- Visual Studio.

- Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010.

## <a name="create-target-sharepoint-subsites"></a>Creare siti secondari di SharePoint di destinazione
 Innanzitutto è necessario creare due nuovi siti secondari di SharePoint: uno per ospitare i flussi di lavoro riutilizzabile da SharePoint Designer, un altro per ospitare i flussi di lavoro convertiti.

#### <a name="to-create-sharepoint-subsites"></a>Per creare siti secondari di SharePoint

1. In SharePoint Designer 2010, nella barra dei menu, scegliere **File** > **nuovo sito Web vuoto**.

2. Nel **nuovo sito Web vuoto** della finestra di dialogo Sfoglia in un sito di SharePoint in cui si desidera creare il flusso di lavoro o usare il valore di http://<em>NomeSistema</em>/ e quindi scegliere il **OK** pulsante.

    Viene visualizzata la Home page.

3. Nel **i siti secondari** keychains le **New** pulsante.

4. Nel **New** finestra di dialogo scegliere **i modelli di SharePoint** dall'elenco nel riquadro a sinistra e scegliere **sito del Team** dall'elenco nel riquadro di destra.

5. Nel **specificare il percorso del sito Web** casella, sostituire la parola **sitosecondario** nell'URL con **SPD1**, quindi scegliere il **OK** pulsante.

    Verrà aperto il nuovo sito secondario in SharePoint Designer. Chiudere questa istanza di Designer in SharePoint e tornare alla prima istanza (sito di livello superiore).

6. Ripetere i passaggi da 3 a 5 per creare il secondo sito secondario, questa volta sostituendo la parola **sitosecondario** nel [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] con **SPD2**.

## <a name="create-a-sharepoint-designer-reusable-workflow"></a>Creare un flusso di lavoro riutilizzabile di SharePoint Designer
 Poiché SharePoint non include eventuali flussi di lavoro riutilizzabili che è possibile usare per questo esempio, si creerà uno. In questo flusso di lavoro semplice, quando un utente immette una nuova attività nell'elenco attività con un titolo specifico, l'attività viene assegnato a tale utente.

#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>Per creare un flusso di lavoro riutilizzabile di SharePoint Designer

1. Nel **i siti secondari** keychains le **SPD1** sito per modificarlo.

2. Sulla barra multifunzione scegliere la **flusso di lavoro riutilizzabile** pulsante.

     Viene visualizzata la procedura guidata Crea flusso di lavoro riutilizzabile.

3. Nel **Name** casella, immettere **SPD Task Workflow**.

4. Nel **tipo di contenuto** scegliere **attività**, quindi scegliere il **OK** pulsante.

     Nella finestra di progettazione del flusso di lavoro SharePoint Designer viene aperto il flusso di lavoro.

5. Nella finestra di progettazione del flusso di lavoro, scegliere il passaggio 1 e quindi sulla barra multifunzione scegliere la **condizione** pulsante.

6. Nell'elenco delle condizioni, scegliere **se il campo elemento corrente è uguale al valore**.

     Questo passaggio viene aggiunta una condizione denominata **se campo è uguale al valore**.

7. Nel **se campo è uguale al valore** condizione, selezionare la **campo** collegamento.

8. Nell'elenco di valori, scegliere **titolo**.

9. Nel **se campo è uguale al valore** condizione, selezionare la **valore** collegamento.

10. Nella casella, immettere **nuova attività**.

     L'istruzione di condizione ora legge **se corrente: titolo dell'elemento è uguale a nuova attività**.

11. Scegliere la riga sotto l'istruzione della condizione e quindi sulla barra multifunzione scegliere la **azione** pulsante.

12. Nell'elenco di azioni, scegliere **campo Set nell'elemento corrente**.

13. Nel **campo insieme al valore** azione, scegliere il **campo** collegamento e quindi nell'elenco, scegliere **assegnato a**.

14. Nel **campo insieme al valore** azione, scegliere il **valore** collegamento e quindi nell'elenco di utenti e gruppi esistenti, scegliere **utente che ha creato l'elemento**.

15. Scegliere il **Add** pulsante e quindi scegliere il **OK** pulsante.

     L'istruzione di azione ora legge **impostare assegnato a per elemento corrente: CreatedBy**.

## <a name="save-and-deploy-the-reusable-workflow"></a>Salvare e distribuire il flusso di lavoro riutilizzabile
 Perché [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] possibile importare solo *wsp* i file, è necessario salvare il flusso di lavoro riutilizzabile come una *wsp* file e distribuirlo a SharePoint prima di importarli in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

> [!IMPORTANT]
>  Se si riceve un errore di runtime eseguendo la procedura seguente, è necessario eseguire la procedura in un sistema che ha accesso al sito di SharePoint.

#### <a name="to-save-and-deploy-the-reusable-workflow"></a>Per salvare e distribuire il flusso di lavoro riutilizzabile

1. Nella parte superiore di SharePoint Designer, scegliere il **salvare** pulsante per salvare lo stato di avanzamento e quindi scegliere il **Publish** per distribuire il flusso di lavoro il **SPD1** sito di SharePoint .

2. Nel riquadro di spostamento, scegliere il **flussi di lavoro** oggetto.

3. Sotto **flusso di lavoro riutilizzabile**, scegliere **SPD Task Workflow**.

4. Sulla barra multifunzione, scegliere il **Salva con nome modello** consente di salvare il flusso di lavoro come una *con estensione wsp* file.

5. Aprire il **SPD1** sito di SharePoint in un browser per visualizzare i *wsp* file in SharePoint.

6. Nella barra Avvio veloce scegliere il **librerie** collegamento.

7. Nel **raccolte documenti** keychains le **gli asset dei siti** collegamento.

     Il **SPD Task Workflow** file sia elencato con altre risorse del sito.

8. Nell'elenco di file scegliere il nome del file.

9. Nel **del File da scaricare** finestra di dialogo scegliere la **salvare** consente di salvare il *wsp* file nel sistema locale.

## <a name="import-the-wsp-file-into-visual-studio"></a>Importare il file. wsp in Visual Studio
 Importa i *wsp* del file in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usando un progetto Importa flusso di lavoro riutilizzabile. Questo progetto converte il flusso di lavoro da un flusso di lavoro riutilizzabile e dichiarativo in un flusso di lavoro di codice. Dopo aver convertito il flusso di lavoro, si utilizzerà codice per modificarne il comportamento.

#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>Per importare un flusso di lavoro da un file con estensione wsp e modificarlo

1. Nelle [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], nella barra dei menu, scegliere **File** > **New** > **progetto**.

2. Nel **nuovo progetto** finestra di dialogo espandere il **SharePoint** nodo sotto **Visual c#** o **Visual Basic**e quindi scegliere il **2010** nodo.

3. Nel **modelli** riquadro, scegliere il **flusso di lavoro di importazione riutilizzabile SharePoint 2010** modello, lasciare il nome del progetto come **WorkflowImportProject1**e quindi scegliere il **OK** pulsante.

    Viene visualizzata la personalizzazione guidata SharePoint.

4. Nel **specificare il livello di sito e la sicurezza per il debug** pagina, immettere il [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] per il secondo sito secondario di SharePoint creato in precedenza: http://<em>il nome del sistema</em>/SPD2.

5. Nel **qual è il livello di attendibilità per la soluzione SharePoint?** keychains le **Distribuisci come soluzione farm** pulsante di opzione e quindi scegliere il **Avanti** pulsante.

    Per altre informazioni sulle modalità sandbox e soluzioni farm, vedere [considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).

6. Nel **specificare l'origine del nuovo progetto** pagina, selezionare il percorso nel sistema in cui è salvato in precedenza il *wsp* del file, aprire il file e quindi scegliere il **Avanti** pulsante.

   > [!NOTE]
   >  Scegliere il **Finish** per importare tutti gli elementi disponibili nel *wsp* file.

    Ciò consente di visualizzare un elenco di flussi di lavoro riutilizzabili per l'importazione.

7. Nel **selezionare gli elementi da importare** scegliere i **SPD Task Workflow** flusso di lavoro e quindi scegliere il **fine** pulsante.

    Al termine dell'operazione di importazione, un progetto denominato **WorkflowImportProject1** viene creato un flusso di lavoro denominato **SPD_Workflow_TestFT**. In questa cartella sono presenti file di definizione del flusso di lavoro *Elements* e il file di progettazione del flusso di lavoro (*xoml*). La finestra di progettazione contiene due file: il file delle regole (con estensione rules) e il file code-behind (entrambi *cs* oppure *vb*, a seconda del linguaggio di programmazione del progetto).

8. Nelle **Esplora soluzioni**, eliminare il **altri file importati** cartella.

9. Nel *Elements* del file, eliminare `InstantiationURL="_layouts/IniErkflIP.sspx"`.

10. Nelle **Esplora soluzioni**, scegliere **WorkflowImportProject1**, quindi nella barra dei menu, scegliere **progetto** > **impostato come progetto di avvio**  per impostare **WorkflowImportProject1** come elemento di avvio.

     Verrà visualizzato l'elenco immediatamente quando si esegue il debug del progetto.

11. Poiché il **importare SharePoint 2010 flusso di lavoro riutilizzabile** modello non importare i valori di proprietà di associazione per il flusso di lavoro importato, è necessario immetterli. Per eseguire questa operazione:

    1. Nelle **Esplora soluzioni**, scegliere il **SPD_Workflow_TestFT** nodo.

    2. Scegliere i puntini di sospensione (![ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ellisse di ASP.NET Mobile Designer")) pulsante accanto a una delle proprietà dell'elenco, ad esempio il **elenco destinazione** proprietà.

    3. Immettere i valori mancanti nella personalizzazione guidata SharePoint e quindi scegliere il **fine** pulsante.

12. Scegliere il file con estensione xoml e quindi nella barra dei menu scegliere **View** > **progettazione** per visualizzare il flusso di lavoro importato nella finestra di progettazione del flusso di lavoro.

13. Nel **Windows Workflow v3.0** nodo delle **della casella degli strumenti**, effettuare una delle operazioni seguenti:

    - Aprire il menu di scelta rapida per il **codice** attività, quindi scegliere **copia**. Nella finestra di progettazione del flusso di lavoro, aprire il menu di scelta rapida per la riga sotto la **SequenceActivity1** attività, quindi scegliere **Incolla**.

    - Trascinare il **codice** attività dal **della casella degli strumenti** alla finestra di progettazione del flusso di lavoro e connetterla alla riga sotto il **SequenceActivity1** attività.

      Verrà aggiunta un'attività alla finestra di progettazione del flusso di lavoro denominato **CodeActivity1**. In questa attività si aggiungerà un'azione di codice che crea un annuncio nell'elenco di annunci quando l'utente inizia il flusso di lavoro.

14. Eseguire una delle procedure seguenti:

    - Fare doppio clic su **CodeActivity1** per generare un gestore dell'evento e visualizzare il codice.

    - Nel **delle proprietà** finestra per **CodeActivity1**, impostare il valore della **ExecuteCode** proprietà **codeActivity_ExecuteCode**.

15. Aggiungere il codice seguente sotto l'oggetto esistente **usando** oppure **Imports** istruzioni:

     [!code-csharp[SP_SPDWFImport#1](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]

16. Sostituire `codeActivity1_ExecuteCode` con quanto segue:

     [!code-csharp[SP_SPDWFImport#2](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]

## <a name="deploy-the-project-and-associate-the-workflow"></a>Distribuire il progetto e associare il flusso di lavoro
 Successivamente, eseguire WorkflowImportProject1 per distribuirla in un sito di SharePoint e quindi associare il flusso di lavoro con l'elenco di attività per visualizzare e testare la modifica, convertito del flusso di lavoro.

#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>Per distribuire il progetto e associare il flusso di lavoro

1. Nelle [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], scegliere il **F5** tasto per eseguire e distribuire il progetto di flusso di lavoro convertito.

2. Nella barra Avvio veloce scegliere il **attività** link per visualizzare l'elenco di attività.

3. Nel **strumenti elenco** scheda, scegliere il **elementi** pulsante e quindi scegliere il **nuovo elemento** pulsante.

     Il **attività - nuovo elemento** verrà visualizzata la finestra di dialogo.

4. Nel **Title** casella, immettere **nuova attività**e quindi scegliere il **Salva** pulsante.

5. Nel **strumenti elenco** scheda, scegliere il **elenco** pulsante e quindi scegliere il **impostazioni elenco** pulsante.

     Il **le impostazioni dell'elenco** verrà visualizzata la pagina.

6. Nel **autorizzazioni e gestione** keychains le **le impostazioni del flusso di lavoro** collegamento.

     Il **delle impostazioni del flusso di lavoro** verrà visualizzata la pagina.

7. Scegliere il **aggiungere un flusso di lavoro** collegamento.

8. Nel **flusso di lavoro** casella di riepilogo **WorkflowImportProject1 - SPD Workflow Test**.

9. Nel **Name** casella, immettere **SPD Workflow Test**e quindi scegliere il **OK** pulsante.

10. Nella barra Avvio veloce scegliere il **attività** elenco.

11. Scegliere la freccia accanto a **nuova attività**, quindi nell'elenco, scegliere **i flussi di lavoro**.

12. Nel **avvia un nuovo flusso di lavoro** , quindi scegliere il collegamento per **SPD Workflow Test**e quindi scegliere il **avviare** pulsante per avviare il flusso di lavoro.

    > [!NOTE]
    >  In alternativa, è possibile associare automaticamente un flusso di lavoro con un elenco di esecuzione della procedura guidata delle impostazioni del flusso di lavoro e impostando il flusso di lavoro per associare automaticamente.

     Si noti che dal flusso di lavoro vengono eseguite due azioni: il nome viene visualizzato nella finestra dell'attività **assegnato a** colonna e un annuncio viene visualizzato nel **annunci** elenco.

## <a name="see-also"></a>Vedere anche
- [Importare gli elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Creare controlli utente riutilizzabili per web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
