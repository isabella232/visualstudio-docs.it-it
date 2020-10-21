---
title: 'Procedura dettagliata: importare un flusso di lavoro riutilizzabile di SharePoint Designer | Microsoft Docs'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 8e6680c6ff95808db56e5bb32e02e0775c935011
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/30/2020
ms.locfileid: "92298047"
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow"></a>Procedura dettagliata: importare un flusso di lavoro riutilizzabile di SharePoint Designer

  In questa procedura dettagliata viene illustrato come importare un flusso di lavoro riutilizzabile creato in SharePoint Designer 2010 in un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progetto flusso di lavoro di SharePoint.

 I flussi di lavoro creati in SharePoint Designer, o *flussi di lavoro dichiarativi*, sono costituiti da [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] istruzioni anziché da codice. SharePoint Designer 2010 introduce *flussi di lavoro riutilizzabili*, che sono flussi di lavoro dichiarativi portabili che possono essere utilizzati da elenchi diversi nei siti di SharePoint.

 I flussi di lavoro creati in [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] , ad esempio i flussi di lavoro sequenziali e delle macchine a Stati, sono denominati *flussi di lavoro di codice* I flussi di lavoro di codice sono costituiti da file XML e moduli di codice in cui gli utenti possono personalizzare il comportamento del flusso di lavoro.

 Tramite Visual Studio è possibile importare flussi di lavoro riutilizzabili creati in SharePoint Designer 2010 e convertirli in flussi di lavoro di codice per utilizzarli nei siti di SharePoint.

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di un flusso di lavoro semplice e riutilizzabile in SharePoint Designer.

- Esportazione del flusso di lavoro riutilizzabile di SharePoint Designer in un file con estensione *WSP* e in SharePoint.

- Importazione del file con *estensione wsp* in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tramite il progetto di flusso di lavoro di importazione riutilizzabile.

- Modifica del flusso di lavoro mediante l'aggiunta di codice.

- Utilizzo del flusso di lavoro importato in un sito di SharePoint.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e SharePoint.

- Visual Studio.

- Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010.

## <a name="create-target-sharepoint-subsites"></a>Creare siti secondari di SharePoint di destinazione
 Prima di tutto si creano due nuovi siti secondari di SharePoint: uno per ospitare i flussi di lavoro riutilizzabili da SharePoint Designer, un altro per ospitare i flussi di lavoro convertiti.

#### <a name="to-create-sharepoint-subsites"></a>Per creare siti secondari di SharePoint

1. In SharePoint Designer 2010, sulla barra dei menu scegliere **file**  >  **nuovo sito Web vuoto**.

2. Nella finestra di dialogo **nuovo sito Web vuoto** passare a un sito di SharePoint in cui si desidera creare il flusso di lavoro oppure utilizzare il valore di http://<em>SystemName</em>/, quindi scegliere il pulsante **OK** .

    Verrà visualizzata la Home page.

3. Nella sezione **siti secondari** scegliere il pulsante **nuovo** .

4. Nella finestra di dialogo **nuovo** scegliere **modelli di SharePoint** dall'elenco nel riquadro a sinistra e scegliere sito del **Team** dall'elenco nel riquadro di destra.

5. Nella casella **specificare il percorso del sito Web** sostituire il **sito secondario** di Word nell'URL con **SPD1**, quindi scegliere il pulsante **OK** .

    Verrà aperto il nuovo sito secondario in SharePoint Designer. Chiudere l'istanza di SharePoint Designer e tornare alla prima istanza (sito di livello superiore).

6. Ripetere i passaggi 3-5 per creare il secondo sito secondario, questa volta sostituendo il **sito secondario** di Word in [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] con **SPD2**.

## <a name="create-a-sharepoint-designer-reusable-workflow"></a>Creazione di un flusso di lavoro riutilizzabile di SharePoint Designer
 Poiché SharePoint non include i flussi di lavoro riutilizzabili che è possibile utilizzare per questo esempio, ne verrà creato uno. In questo semplice flusso di lavoro, quando un utente immette una nuova attività nell'elenco attività con un titolo specifico, l'attività viene assegnata a tale utente.

#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>Per creare un flusso di lavoro riutilizzabile di SharePoint Designer

1. Nella sezione **siti secondari** scegliere il sito **SPD1** per modificarlo.

2. Sulla barra multifunzione scegliere il pulsante **flusso di lavoro riutilizzabile** .

     Verrà visualizzata la creazione guidata flusso di lavoro riutilizzabile.

3. Nella casella **nome** immettere **SPD Task Workflow**.

4. Nell'elenco **tipo di contenuto** scegliere **attività**, quindi scegliere il pulsante **OK** .

     Il flusso di lavoro viene aperto in Progettazione flussi di lavoro di SharePoint Designer.

5. Nella finestra di progettazione del flusso di lavoro scegliere il passaggio 1, quindi sulla barra multifunzione scegliere il pulsante **condizione** .

6. Nell'elenco delle condizioni scegliere se il **campo elemento corrente è uguale a valore**.

     Questo passaggio aggiunge una condizione denominata se il **campo è uguale a value**.

7. Se il **campo IF è uguale** a Condition Value, scegliere il collegamento al **campo** .

8. Nell'elenco di valori scegliere **title**.

9. Se il **campo IF è uguale** a Condition Value, scegliere il collegamento **value** .

10. Nella casella immettere **nuova attività**.

     L'istruzione Condition legge ora **se l'elemento corrente: title è uguale a New Task**.

11. Scegliere la riga sotto l'istruzione Condition, quindi sulla barra multifunzione scegliere il pulsante **azione** .

12. Nell'elenco delle azioni scegliere **Imposta campo nell'elemento corrente**.

13. Nell'azione **Imposta campo su valore** scegliere il collegamento **campo** , quindi nell'elenco scegliere **assegnato a**.

14. Nell'azione **Imposta campo su valore** scegliere il collegamento **valore** , quindi nell'elenco di utenti e gruppi esistenti scegliere **utente che ha creato l'elemento**.

15. Scegliere il pulsante **Aggiungi** , quindi scegliere il pulsante **OK** .

     L'istruzione di azione ora legge il **Set assegnato a sull'elemento corrente: CreatedBy**.

## <a name="save-and-deploy-the-reusable-workflow"></a>Salvare e distribuire il flusso di lavoro riutilizzabile
 Poiché [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] può importare solo file con *estensione wsp* , è necessario salvare il flusso di lavoro riutilizzabile come file con estensione *WSP* e distribuirlo in SharePoint prima di importarlo in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

> [!IMPORTANT]
> Se si riceve un errore di runtime eseguendo la procedura riportata di seguito, è necessario eseguire la procedura in un sistema con accesso al sito di SharePoint.

#### <a name="to-save-and-deploy-the-reusable-workflow"></a>Per salvare e distribuire il flusso di lavoro riutilizzabile

1. Nella parte superiore di SharePoint Designer, scegliere il pulsante **Salva** per salvare lo stato di avanzamento, quindi scegliere il pulsante **pubblica** per distribuire il flusso di lavoro nel sito di SharePoint **SPD1** .

2. Nel riquadro di spostamento scegliere l'oggetto **flussi di lavoro** .

3. In **flusso di lavoro riutilizzabile**scegliere **SPD Task Workflow**.

4. Sulla barra multifunzione scegliere il pulsante **Salva come modello** per salvare il flusso di lavoro come file con estensione *WSP* .

5. Aprire il sito di **SPD1** SharePoint in un browser per visualizzare il file con *estensione wsp* in SharePoint.

6. Sulla barra QuickLaunch scegliere il collegamento **librerie** .

7. Nella sezione **raccolte documenti** scegliere il collegamento **Asset sito** .

     Il file del **flusso di lavoro delle attività SPD** è elencato con altre risorse del sito.

8. Nell'elenco di file scegliere il nome del file.

9. Nella finestra di dialogo **download del file** scegliere il pulsante **Salva** per salvare il file con *estensione wsp* nel sistema locale.

## <a name="import-the-wsp-file-into-visual-studio"></a>Importare il file con estensione wsp in Visual Studio
 Importare il file con *estensione wsp* in utilizzando [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] un progetto di flusso di lavoro di importazione riutilizzabile. Questo progetto converte il flusso di lavoro da un flusso di lavoro dichiarativo riutilizzabile in un flusso di lavoro di codice. Dopo la conversione del flusso di lavoro, verrà utilizzato il codice per modificarne il comportamento.

#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>Per importare un flusso di lavoro da un file con estensione wsp e modificarlo

1. Nella [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] barra dei menu di scegliere **file**  >  **nuovo**  >  **progetto**.

2. Nella finestra di dialogo **nuovo progetto** espandere il nodo **SharePoint** sotto **Visual C#** o **Visual Basic**, quindi scegliere il nodo **2010** .

3. Nel riquadro **modelli** scegliere il modello **Importa flusso di lavoro riutilizzabile di SharePoint 2010** , lasciare il nome del progetto come **WorkflowImportProject1**, quindi scegliere il pulsante **OK** .

    Viene visualizzata la Personalizzazione guidata SharePoint.

4. Nella pagina **specificare il sito e il livello di sicurezza per il debug** immettere [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] per il secondo sito secondario di SharePoint creato in precedenza: http://<em>System Name</em>/SPD2.

5. Nella sezione **Qual è il livello di attendibilità per la soluzione SharePoint** scegliere il pulsante di opzione **Distribuisci come soluzione farm** , quindi scegliere il pulsante **Avanti** .

    Per ulteriori informazioni sulle soluzioni create mediante sandbox e farm, vedere Considerazioni sulle soluzioni [create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).

6. Nella pagina **specificare l'origine del nuovo progetto** passare al percorso nel sistema in cui è stato salvato in precedenza il file con *estensione wsp* , aprire il file, quindi scegliere il pulsante **Avanti** .

   > [!NOTE]
   > Scegliere il pulsante **fine** per importare tutti gli elementi disponibili nel file con estensione *WSP* .

    Viene visualizzato un elenco di flussi di lavoro riutilizzabili disponibili per l'importazione.

7. Nella casella **selezionare gli elementi da importare** scegliere il flusso di lavoro del flusso di lavoro dell' **attività SPD** , quindi scegliere il pulsante **fine** .

    Al termine dell'operazione di importazione, viene creato un progetto denominato **WorkflowImportProject1** contenente un flusso di lavoro denominato **SPD_Workflow_TestFT**. In questa cartella è il file di definizione del flusso di lavoro *Elements.xml* e il file di progettazione del flusso di lavoro (*. xoml*). La finestra di progettazione contiene due file: il file delle regole (. Rules) e il file code-behind, ovvero *. cs* o *. vb*, a seconda del linguaggio di programmazione del progetto.

8. In **Esplora soluzioni**eliminare la cartella **altri file importati** .

9. Nel file di *Elements.xml* eliminare `InstantiationURL="_layouts/IniErkflIP.sspx"` .

10. In **Esplora soluzioni**scegliere **WorkflowImportProject1**, quindi nella barra dei menu scegliere **progetto**  >  **impostato come progetto di avvio** per impostare **WorkflowImportProject1** come elemento di avvio.

     L'elenco verrà visualizzato immediatamente quando si esegue il debug del progetto.

11. Poiché il modello di **flusso di lavoro importazione riutilizzabile di SharePoint 2010** non importa i valori delle proprietà di associazione per il flusso di lavoro importato, è necessario immetterli Per eseguire questa operazione:

    1. In **Esplora soluzioni**scegliere il nodo **SPD_Workflow_TestFT** .

    2. Scegliere il pulsante con i puntini di sospensione (![ASP.NET Mobile Designer ellisse](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")) accanto a una delle proprietà dell'elenco, ad esempio la proprietà **elenco di destinazione** .

    3. Immettere i valori mancanti nella procedura guidata di personalizzazione di SharePoint, quindi scegliere il pulsante **fine** .

12. Scegliere il file con estensione xoml, quindi nella barra dei menu scegliere **Visualizza**  >  **finestra di progettazione** per visualizzare il flusso di lavoro importato nella finestra di progettazione del flusso di lavoro.

13. Nel nodo **Windows Workflow v 3.0** della **casella degli strumenti**eseguire uno dei passaggi seguenti:

    - Aprire il menu di scelta rapida per l'attività **codice** , quindi scegliere **copia**. Nella finestra di progettazione del flusso di lavoro aprire il menu di scelta rapida per la riga sotto l'attività **SequenceActivity1** , quindi scegliere **Incolla**.

    - Trascinare l'attività **Code** dalla **casella degli strumenti** alla finestra di progettazione del flusso di lavoro e connetterla alla riga sotto l'attività **SequenceActivity1** .

      Viene aggiunta un'attività alla finestra di progettazione del flusso di lavoro denominata **CodeActivity1**. In questa attività verrà aggiunta un'azione di codice che crea un annuncio nell'elenco degli annunci quando l'utente avvia il flusso di lavoro.

14. Eseguire una delle procedure seguenti:

    - Fare doppio clic su **CodeActivity1** per generare un gestore eventi e visualizzare il codice.

    - Nella finestra **Proprietà** di **CodeActivity1**impostare il valore della proprietà **ExecuteCode** su **codeActivity_ExecuteCode**.

15. Aggiungere quanto segue sotto le direttive **using** o **Imports** esistenti:

     [!code-csharp[SP_SPDWFImport#1](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]

16. Sostituire `codeActivity1_ExecuteCode` con quanto segue:

     [!code-csharp[SP_SPDWFImport#2](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]

## <a name="deploy-the-project-and-associate-the-workflow"></a>Distribuire il progetto e associare il flusso di lavoro
 Eseguire quindi WorkflowImportProject1 per distribuirlo in un sito di SharePoint e quindi associare il flusso di lavoro all'elenco attività per visualizzare e testare il flusso di lavoro modificato e convertito.

#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>Per distribuire il progetto e associare il flusso di lavoro

1. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] premere il tasto **F5** per eseguire e distribuire il progetto di flusso di lavoro convertito.

2. Sulla barra QuickLaunch scegliere il collegamento **attività** per visualizzare l'elenco attività.

3. Nella scheda **Strumenti elenco** scegliere il pulsante **elementi** , quindi scegliere il pulsante **nuovo elemento** .

     Verrà visualizzata la finestra di dialogo **attività-nuovo elemento** .

4. Nella casella **titolo** , immettere **nuova attività**, quindi scegliere il pulsante **Salva** .

5. Nella scheda **Strumenti elenco** scegliere il pulsante **elenco** , quindi scegliere il pulsante **Impostazioni elenco** .

     Verrà visualizzata la pagina **Impostazioni elenco** .

6. Nella sezione **autorizzazioni e gestione** scegliere il collegamento **Impostazioni flusso di lavoro** .

     Verrà visualizzata la pagina **Impostazioni flusso di lavoro** .

7. Scegliere il collegamento **Aggiungi un flusso di lavoro** .

8. Nell'elenco **flusso di lavoro** scegliere **WorkflowImportProject1-SPD Workflow Test**.

9. Nella casella **nome** immettere **SPD Workflow Test**, quindi scegliere il pulsante **OK** .

10. Nella barra QuickLaunch scegliere l'elenco **attività** .

11. Scegliere la freccia accanto a **nuova attività**, quindi nell'elenco scegliere **flussi di lavoro**.

12. Nella sezione **avviare un nuovo flusso di lavoro** scegliere il collegamento per **test del flusso di lavoro SPD**, quindi scegliere il pulsante **Avvia** per avviare il flusso di lavoro.

    > [!NOTE]
    > In alternativa, è possibile associare automaticamente un flusso di lavoro a un elenco eseguendo la procedura guidata delle impostazioni del flusso di lavoro e impostando il flusso di lavoro per l'associazione automatica.

     Si noti che due azioni vengono eseguite dal flusso di lavoro: il nome viene visualizzato nella colonna **assegnato a** dell'attività e viene visualizzato un annuncio nell'elenco degli **annunci** .

## <a name="see-also"></a>Vedere anche
- [Importa elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Creazione di controlli riutilizzabili per Web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
