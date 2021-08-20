---
title: 'Procedura dettagliata: Importare un flusso di lavoro SharePoint Designer riutilizzabile | Microsoft Docs'
titleSuffix: ''
description: In questa procedura dettagliata importare un flusso di lavoro riutilizzabile creato in SharePoint Designer in un progetto Visual Studio SharePoint flusso di lavoro.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: ab8357b126ab2bfacea24cd3b922baa40fb25da4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148747"
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow"></a>Procedura dettagliata: Importare un flusso di lavoro SharePoint Designer riutilizzabile

  Questa procedura dettagliata illustra come importare un flusso di lavoro riutilizzabile creato in SharePoint Designer 2010 in un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint flusso di lavoro.

 I flussi di lavoro creati SharePoint Designer, o flussi di lavoro *dichiarativi,* sono costituiti [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] da istruzioni anziché da codice. SharePoint Designer 2010 introduce flussi di lavoro riutilizzabili, che sono flussi di lavoro dichiarativi portabili che possono essere usati da elenchi diversi in SharePoint siti.

 I flussi di lavoro creati in , ad esempio i flussi di lavoro sequenziali e della macchina [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] a stati, sono *detti flussi di lavoro di codice.* I flussi di lavoro di codice sono costituiti da file XML e moduli di codice in cui gli utenti possono personalizzare il comportamento del flusso di lavoro.

 Tramite Visual Studio è possibile importare flussi di lavoro riutilizzabili creati in SharePoint Designer 2010 e convertirli in flussi di lavoro di codice per utilizzarli nei siti di SharePoint.

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di un flusso di lavoro semplice e riutilizzabile in SharePoint Designer.

- Esportazione del flusso di lavoro SharePoint Designer riutilizzabile in un file con estensione *wsp* e in SharePoint.

- Importazione del file *con estensione wsp* in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tramite il progetto Importa flusso di lavoro riutilizzabile.

- Modifica del flusso di lavoro mediante l'aggiunta di codice.

- Uso del flusso di lavoro importato in un SharePoint sito.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e SharePoint.

- Visual Studio.

- Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010.

## <a name="create-target-sharepoint-subsites"></a>Creare siti SharePoint di destinazione
 Prima di tutto si creano due SharePoint secondari: uno per ospitare i flussi di lavoro riutilizzabili da SharePoint Designer, un altro per ospitare i flussi di lavoro convertiti.

#### <a name="to-create-sharepoint-subsites"></a>Per creare SharePoint siti secondari

1. In SharePoint Designer 2010 scegliere **File** Nuovo sito  >  **Web vuoto sulla barra dei** menu.

2. Nella finestra di dialogo Nuovo sito **Web** vuoto passare a un sito SharePoint in cui si vuole creare il flusso di lavoro oppure usare il valore di http://<em>SystemName</em>/ e quindi scegliere **OK.**

    Viene visualizzata la home page.

3. Nella sezione **Siti secondari** scegliere il **pulsante** Nuovo.

4. Nella finestra **di** dialogo Nuovo scegliere SharePoint **modelli** dall'elenco nel riquadro sinistro e scegliere Sito del **team** dall'elenco nel riquadro destro.

5. Nella casella **Specificare il percorso del** sito Web sostituire la parola **sito** secondario nell'URL con **SPD1** e quindi scegliere **OK.**

    Verrà aperto il nuovo sito secondario in SharePoint progettazione. Chiudere questa istanza di SharePoint Designer e tornare alla prima istanza (il sito di primo livello).

6. Ripetere i passaggi da 3 a 5 per creare il secondo sito secondario, questa volta sostituendo la **parola** sito secondario in [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] con **SPD2**.

## <a name="create-a-sharepoint-designer-reusable-workflow"></a>Creare un flusso di lavoro SharePoint Designer riutilizzabile
 Poiché SharePoint non include flussi di lavoro riutilizzabili che è possibile usare per questo esempio, ne verrà creato uno. In questo flusso di lavoro semplice, quando un utente immette una nuova attività nell'elenco attività con un titolo specifico, l'attività viene assegnata a tale utente.

#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>Per creare un flusso di lavoro SharePoint Designer riutilizzabile

1. Nella sezione **Siti secondari** scegliere il sito **SPD1** per modificarlo.

2. Sulla barra multifunzione scegliere il **pulsante Flusso di lavoro riutilizzabile.**

     Verrà visualizzata la procedura guidata Crea flusso di lavoro riutilizzabile.

3. Nella casella **Nome** immettere **SPD Task Workflow**.

4. **Nell'elenco Tipo di** contenuto scegliere **Attività** e quindi fare clic sul **pulsante OK.**

     Il flusso di lavoro viene aperto nella finestra SharePoint Progettazione flussi di lavoro.

5. Nella finestra di progettazione del flusso di lavoro scegliere Passaggio 1 e quindi sulla barra multifunzione scegliere il **pulsante** Condizione.

6. Nell'elenco delle condizioni scegliere **Se il campo dell'elemento corrente è uguale al valore**.

     Questo passaggio aggiunge una condizione denominata **Se il campo è uguale al valore**.

7. Nel campo **Se è uguale a condizione valore** scegliere il collegamento **al** campo.

8. Nell'elenco dei valori scegliere **Titolo**.

9. Nel campo **Se è uguale a condizione valore** scegliere il collegamento **valore.**

10. Nella casella immettere **Nuova attività**.

     L'istruzione condition legge ora **If Current Item:Title uguale a New task**.

11. Scegliere la riga sotto l'istruzione condition e quindi, sulla barra multifunzione, scegliere il **pulsante** Azione.

12. Nell'elenco delle azioni scegliere **Imposta campo nell'elemento corrente.**

13. **Nell'azione Imposta campo su valore** scegliere il **collegamento** al campo e quindi nell'elenco scegliere **Assegnato a**.

14. **Nell'azione Imposta campo** su  valore scegliere il collegamento al valore e quindi nell'elenco di utenti e gruppi esistenti scegliere Utente che ha **creato l'elemento.**

15. Scegliere il **pulsante** Aggiungi e quindi fare clic **sul pulsante OK.**

     L'istruzione di azione legge ora **Imposta Assegnato a su Elemento corrente:CreatedBy**.

## <a name="save-and-deploy-the-reusable-workflow"></a>Salvare e distribuire il flusso di lavoro riutilizzabile
 Poiché può importare solo file con estensione wsp, è necessario salvare il flusso di lavoro riutilizzabile come file con estensione wsp e distribuirlo in SharePoint prima di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] importarlo in   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

> [!IMPORTANT]
> Se viene visualizzato un errore di runtime durante l'esecuzione della procedura seguente, è necessario eseguire la procedura in un sistema che abbia accesso al SharePoint sito.

#### <a name="to-save-and-deploy-the-reusable-workflow"></a>Per salvare e distribuire il flusso di lavoro riutilizzabile

1. Nella parte superiore di SharePoint Designer  scegliere il pulsante Salva per  salvare lo stato di avanzamento e quindi scegliere il pulsante Pubblica per distribuire il flusso di lavoro nel sito SharePoint **SPD1.**

2. Nel riquadro di spostamento scegliere **l'oggetto Flussi di** lavoro.

3. In **Flusso di lavoro riutilizzabile** scegliere Flusso di lavoro attività **SPD**.

4. Sulla barra multifunzione scegliere il **pulsante Salva come modello** per salvare il flusso di lavoro come file con estensione *wsp.*

5. Aprire il sito SharePoint **SPD1** in un browser per visualizzare il file con estensione *wsp* in SharePoint.

6. Nella barra Avvio rapido scegliere il **collegamento Librerie.**

7. Nella sezione **Raccolte documenti** scegliere il collegamento **Asset del** sito.

     Il file **del flusso di lavoro attività SPD** è elencato con altri asset del sito.

8. Nell'elenco di file scegliere il nome del file.

9. Nella finestra **di dialogo Download** file scegliere il pulsante **Salva** per salvare il file con *estensione wsp* nel sistema locale.

## <a name="import-the-wsp-file-into-visual-studio"></a>Importare il file con estensione wsp in Visual Studio
 Importare il file *con estensione wsp* in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usando un progetto Importa flusso di lavoro riutilizzabile. Questo progetto converte il flusso di lavoro da un flusso di lavoro riutilizzabile e dichiarativo in un flusso di lavoro di codice. Dopo la conversione del flusso di lavoro, si userà il codice per modificarne il comportamento.

#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>Per importare un flusso di lavoro da un file con estensione wsp e modificarlo

1. Nella [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] barra dei menu scegliere **File** nuovo Project  >    >  .

2. Nella finestra **di dialogo Nuovo** Project espandere il nodo **SharePoint** in **Visual C#** o **Visual Basic** e quindi scegliere il **nodo 2010.**

3. Nel **riquadro** Modelli scegliere il modello Import **Reusable SharePoint 2010 Workflow** (Importa flusso di lavoro SharePoint 2010), lasciare il nome del progetto **workflowImportProject1** e quindi scegliere **OK.**

    Viene visualizzata la Personalizzazione guidata SharePoint.

4. Nella pagina **Specificare il sito** e il livello di sicurezza per il debug immettere per il secondo sito secondario SharePoint creato in precedenza: http:// nome di sistema [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] /SPD2.<em></em>

5. Nella sezione Qual è il livello di attendibilità per questa soluzione **SharePoint?** scegliere il pulsante di opzione Distribuisci come soluzione **farm** e quindi scegliere **il pulsante** Avanti.

    Per altre informazioni sulle soluzioni sandbox e farm, vedere [Considerazioni sulle soluzioni in modalità sandbox.](../sharepoint/sandboxed-solution-considerations.md)

6. Nella pagina **Specificare il nuovo** progetto di origine passare al percorso del sistema in cui è stato salvato in precedenza il file con estensione *wsp,* aprire il file e quindi scegliere **il pulsante** Avanti.

   > [!NOTE]
   > Scegliere il **pulsante** Fine per importare tutti gli elementi disponibili nel file *con estensione wsp.*

    Verrà visualizzato un elenco di flussi di lavoro riutilizzabili disponibili per l'importazione.

7. Nella casella **Seleziona elementi da importare** scegliere il flusso di lavoro Flusso di lavoro attività **SPD** e quindi scegliere **il pulsante** Fine.

    Al termine dell'operazione di importazione, viene creato un progetto **denominato WorkflowImportProject1** contenente un flusso di lavoro denominato **SPD_Workflow_TestFT**. In questa cartella è presente il file di definizione del *flusso di lavoroElements.xml* file di progettazione del flusso di lavoro (*xoml*). La finestra di progettazione contiene due file: il file delle regole (con estensione rules) e il file code-behind *(cs* o *vb*, a seconda del linguaggio di programmazione del progetto).

8. In **Esplora soluzioni** eliminare la **cartella Altri file** importati.

9. Nel file *Elements.xml* eliminare `InstantiationURL="_layouts/IniErkflIP.sspx"` .

10. In **Esplora soluzioni** scegliere **WorkflowImportProject1** e quindi nella barra dei menu scegliere **Project** Imposta come Project per impostare  >   **WorkflowImportProject1** come elemento di avvio.

     L'elenco viene visualizzato immediatamente quando si esegue il debug del progetto.

11. Poiché il **modello Import Reusable SharePoint 2010 Workflow** non importa i valori delle proprietà di associazione per il flusso di lavoro importato, è necessario immetterli. Per eseguire questa operazione:

    1. In **Esplora soluzioni** scegliere il **nodo SPD_Workflow_TestFT.**

    2. Scegliere i puntini di sospensione (![ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")) accanto a una delle proprietà dell'elenco, ad esempio la proprietà **Elenco** di destinazione.

    3. Compilare i valori mancanti nella SharePoint personalizzazione guidata e quindi scegliere il **pulsante** Fine.

12. Scegliere il file con estensione xoml e quindi nella barra dei menu scegliere Progettazione viste per visualizzare il flusso di lavoro importato nella finestra di progettazione  >   del flusso di lavoro.

13. Nel nodo Windows flusso di lavoro **v3.0 della** **casella** degli strumenti eseguire una delle operazioni seguenti:

    - Aprire il menu di scelta rapida per **l'attività** Codice e quindi scegliere **Copia**. Nella finestra di progettazione del flusso di lavoro aprire il menu di scelta rapida per la riga **nell'attività SequenceActivity1** e quindi scegliere **Incolla**.

    - Trascinare **l'attività Code** dalla **Casella degli** strumenti alla finestra di progettazione del flusso di lavoro e connetterla alla riga sotto **l'attività SequenceActivity1.**

      Verrà aggiunta un'attività alla finestra di progettazione del flusso di lavoro **denominata CodeActivity1.** In questa attività si aggiungerà un'azione di codice che crea un annuncio nell'elenco Annunci quando l'utente avvia il flusso di lavoro.

14. Eseguire una delle procedure seguenti:

    - Fare doppio clic **su CodeActivity1** per generare un gestore eventi e visualizzare il codice.

    - Nella finestra **Proprietà** per **CodeActivity1** impostare il valore della **proprietà ExecuteCode** **su codeActivity_ExecuteCode**.

15. Aggiungere quanto segue nelle direttive **using o** **Imports** esistenti:

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb" id="Snippet1":::

16. Sostituire `codeActivity1_ExecuteCode` con quanto segue:

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs" id="Snippet2":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb" id="Snippet2":::

## <a name="deploy-the-project-and-associate-the-workflow"></a>Distribuire il progetto e associare il flusso di lavoro
 Eseguire quindi WorkflowImportProject1 per distribuirlo in un sito SharePoint e quindi associare il flusso di lavoro all'elenco Attività per visualizzare e testare il flusso di lavoro modificato e convertito.

#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>Per distribuire il progetto e associare il flusso di lavoro

1. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] scegliere il tasto **F5 per** eseguire e distribuire il progetto del flusso di lavoro convertito.

2. Sulla barra Avvio rapido scegliere il collegamento Attività **per** visualizzare l'elenco Attività.

3. Nella scheda **Strumenti elenco** scegliere il **pulsante Elementi** e quindi il pulsante **Nuovo** elemento.

     Verrà **visualizzata la finestra di dialogo** Attività - Nuovo elemento.

4. Nella casella **Titolo** immettere **Nuova attività** e quindi scegliere il **pulsante** Salva.

5. Nella scheda **Strumenti elenco** scegliere il **pulsante Elenco** e quindi il pulsante **Impostazioni** elenco.

     Viene **visualizzata Impostazioni** elenco.

6. Nella sezione **Autorizzazioni e gestione** scegliere il collegamento Gestione Impostazioni flusso **di** lavoro.

     Viene **visualizzata Impostazioni** flusso di lavoro.

7. Scegliere il **collegamento Aggiungi flusso di** lavoro.

8. **Nell'elenco Flusso di** lavoro scegliere **WorkflowImportProject1 - SPD Workflow Test**.

9. Nella casella **Nome** immettere **SPD Workflow Test** e quindi scegliere IL PULSANTE **OK.**

10. Nella barra Avvio rapido scegliere **l'elenco** Attività.

11. Scegliere la freccia accanto a **Nuova attività** e quindi nell'elenco scegliere Flussi **di lavoro**.

12. Nella sezione **Avvia un nuovo flusso di** lavoro scegliere il collegamento per Test flusso di lavoro **SPD** e quindi scegliere il **pulsante Avvia** per avviare il flusso di lavoro.

    > [!NOTE]
    > In alternativa, è possibile associare automaticamente un flusso di lavoro a un elenco eseguendo la procedura guidata delle impostazioni del flusso di lavoro e impostando il flusso di lavoro sull'associazione automatica.

     Si noti che il flusso di lavoro ha eseguito **due** azioni: il nome viene visualizzato nella colonna Assegnato a dell'attività e un annuncio viene visualizzato **nell'elenco Annunci.**

## <a name="see-also"></a>Vedi anche
- [Importare elementi da un sito SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Creare controlli riutilizzabili per web part o pagine dell'applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
