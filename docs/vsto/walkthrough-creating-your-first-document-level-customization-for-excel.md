---
title: Creazione della prima personalizzazione a livello di documento per Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, creating your first project
- Excel [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8d45461c7dab250cd43d7a25d8693658c7b8e164
ms.sourcegitcommit: 3ba2968a4b44643482aadad4d50e1a55bb36b136
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2019
ms.locfileid: "74566968"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-excel"></a>Procedura dettagliata: creare la prima personalizzazione a livello di documento per Excel

  Questa procedura dettagliata introduttiva mostra come creare una personalizzazione a livello di documento per Microsoft Office Excel. Le funzionalità create in questo tipo di soluzione sono disponibili solo quando si apre una cartella di lavoro specifica. Una personalizzazione a livello di documento non può essere usata per apportare modifiche a un'intera applicazione, ad esempio per visualizzare una nuova scheda della barra multifunzione quando si apre una cartella di lavoro qualsiasi.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Questa procedura dettagliata illustra le attività seguenti:

- Creazione di un progetto cartella di lavoro di Excel.

- Aggiunta di testo a un foglio di lavoro ospitato nella finestra di progettazione di Visual Studio.

- Scrittura di codice che usa il modello a oggetti di Excel per aggiungere testo al foglio di lavoro personalizzato quando quest'ultimo viene aperta.

- Creazione ed esecuzione del progetto a scopo di test.

- Pulizia del progetto completato per rimuovere dal computer di sviluppo le impostazioni di sicurezza e i file di compilazione non necessari.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisites

 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Creare il progetto

### <a name="to-create-a-new-excel-workbook-project-in-visual-studio"></a>Per creare un nuovo progetto cartella di lavoro di Excel in Visual Studio

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.
::: moniker range="vs-2017"
3. Nel riquadro dei modelli, espandere **Visual C#** o **Visual Basic**, quindi espandere **Office/SharePoint**.

4. Nel nodo **Office/SharePoint** espanso, selezionare il nodo **componenti aggiuntivi VSTO** .

5. Nell'elenco dei modelli di progetto scegliere un progetto di cartella di lavoro VSTO di Excel.

6. Nella casella **nome** digitare **FirstWorkbookCustomization**.

7. Fare clic su **OK**.

8. Selezionare **Crea un nuovo documento** dalla **procedura guidata strumenti di Visual Studio per il progetto di Office**e fare clic su **OK**.
::: moniker-end
::: moniker range=">=vs-2019"
3. Nella finestra di dialogo **Crea un nuovo progetto** selezionare il progetto **cartella di lavoro VSTO di Excel** .

     [!INCLUDE[new-project-dialog-search](../vsto/includes/new-project-dialog-search-md.md)]

4. Scegliere **Avanti**.

5. Digitare **FirstWorkbookCustomization** nella casella **nome** della finestra di dialogo **Configura nuovo progetto** e fare clic su **Crea**.

6. Selezionare **Crea un nuovo documento** dalla **procedura guidata strumenti di Visual Studio per il progetto di Office**e fare clic su **OK**.
::: moniker-end
   - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea il progetto **FirstWorkbookCustomization** e aggiunge i file seguenti al progetto.

   - *FirstWorkbookCustomization*. xlsx: rappresenta la cartella di lavoro di Excel nel progetto. Contiene tutti i fogli di lavoro e i grafici.

   - Sheet1 (file*VB* per Visual Basic o file *CS* per Visual C#): un foglio di lavoro che fornisce l'area di progettazione e il codice per il primo foglio di lavoro della cartella di lavoro. Per ulteriori informazioni, vedere [elemento host Worksheet](../vsto/worksheet-host-item.md).

   - Sheet2 (file con estensione*VB* per Visual Basic o file *CS* per l' C#oggetto visivo): un foglio di lavoro che fornisce l'area di progettazione e il codice per il secondo foglio di lavoro della cartella di lavoro.

   - Sheet3 (file con estensione*VB* per Visual Basic o file *CS* per l' C#oggetto visivo): un foglio di lavoro che fornisce l'area di progettazione e il codice per il terzo foglio di lavoro della cartella di lavoro.

   - ThisWorkbook (file *. vb* per Visual Basic o file *CS* per Visual C#): contiene l'area di progettazione e il codice per le personalizzazioni a livello di cartella di lavoro. Per ulteriori informazioni, vedere [elemento host Workbook](../vsto/workbook-host-item.md).

     Il file di codice Sheet1 viene aperto automaticamente nella finestra di progettazione.

## <a name="close-and-reopen-worksheets-in-the-designer"></a>Chiudere e riaprire i fogli di progettazione nella finestra di progettazione

 Se mentre si sviluppa il progetto si chiude intenzionalmente o accidentalmente una cartella di lavoro o un foglio di lavoro nella finestra di progettazione, è possibile riaprirlo.

### <a name="to-close-and-reopen-a-worksheet-in-the-designer"></a>Per chiudere e riaprire un foglio di lavoro nella finestra di progettazione

1. Chiudere la cartella di lavoro facendo clic sul pulsante **Chiudi** (X) per la finestra di progettazione.

2. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul file di codice **Sheet1** , quindi scegliere **Visualizza finestra di progettazione**.

     \- oppure -

     In **Esplora soluzioni**fare doppio clic sul file di codice **Sheet1** .

## <a name="add-text-to-a-worksheet-in-the-designer"></a>Aggiungere testo a un foglio di progettazione

 È possibile progettare l'interfaccia utente della personalizzazione modificando il foglio di lavoro aperto nella finestra di progettazione. Ad esempio, è possibile aggiungere testo alle celle, applicare formule o aggiungere controlli di Excel. Per altre informazioni su come usare la finestra di progettazione, vedere [progetti di Office nell'ambiente Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

### <a name="to-add-text-to-a-worksheet-by-using-the-designer"></a>Per aggiungere testo a un foglio di lavoro mediante la finestra di progettazione

1. Nel foglio di comando aperto nella finestra di progettazione selezionare la cella **a1**, quindi digitare il testo seguente.

     **Questo testo è stato aggiunto tramite la finestra di progettazione.**

> [!WARNING]
> Se si aggiunge questa riga di testo alla cella **a2**, verrà sovrascritta da altro codice in questo esempio.

## <a name="add-text-to-a-worksheet-programmatically"></a>Aggiungere testo a un foglio di codice a livello di codice

 Aggiungere quindi codice al file di codice Sheet1. Il nuovo codice usa il modello a oggetti di Excel per aggiungere nella cartella di lavoro una seconda riga di testo. Per impostazione predefinita, il file di codice Sheet1 contiene il seguente codice generato:

- Una definizione parziale della classe `Sheet1`, che rappresenta il modello di programmazione del foglio di lavoro e consente di accedere al modello a oggetti di Excel. Per ulteriori informazioni, [elemento host Worksheet](../vsto/worksheet-host-item.md) e [Cenni preliminari sul modello a oggetti di Word](../vsto/word-object-model-overview.md). Il resto della classe `Sheet1` viene definito in un file di codice nascosto che l'utente non deve modificare.

- I gestori eventi `Sheet1_Startup` e `Sheet1_Shutdown` . Questi gestori eventi vengono chiamati quando Excel carica e scarica la personalizzazione. Usare questi gestori eventi per inizializzare la personalizzazione quando viene caricata e per eseguire la pulizia delle risorse usate dalla personalizzazione quando viene scaricata. Per altre informazioni, vedere [eventi nei progetti di Office](../vsto/events-in-office-projects.md).

### <a name="to-add-a-second-line-of-text-to-the-worksheet-by-using-code"></a>Per aggiungere al foglio di lavoro una seconda riga di codice mediante codice

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su **Sheet1**, quindi scegliere **Visualizza codice**.

     Il file di codice verrà aperto in Visual Studio.

2. Sostituire il gestore eventi `Sheet1_Startup` con il codice seguente. Quando viene aperto il foglio Sheet1, questo codice aggiunge una seconda riga di testo al foglio di lavoro.

     [!code-csharp[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelWorkbookTutorial/Sheet1.cs#1)]
     [!code-vb[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelWorkbookTutorial/Sheet1.vb#1)]

## <a name="test-the-project"></a>Testare il progetto

### <a name="to-test-your-workbook"></a>Per testare la cartella di lavoro

1. Premere **F5** per compilare ed eseguire il progetto.

     Quando si compila il progetto, il codice viene compilato in un assembly associato alla cartella di lavoro. Visual Studio inserisce una copia della cartella di lavoro e l'assembly nella cartella dell'output di compilazione del progetto e configura le impostazioni di sicurezza nel computer di sviluppo in modo da consentire l'esecuzione della personalizzazione. Per altre informazioni, vedere [compilare soluzioni Office](../vsto/building-office-solutions.md).

2. Nella cartella di lavoro verificare che sia visualizzato il testo seguente.

     **Questo testo è stato aggiunto tramite la finestra di progettazione.**

     **This text was added by using code.**

3. Chiudere la cartella di lavoro.

## <a name="clean-up-the-project"></a>Pulire il progetto

 Al termine dello sviluppo di un progetto, è necessario rimuovere le impostazioni di sicurezza e i file contenuti nella cartella dell'output di compilazione creati dal processo di compilazione.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Per pulire il progetto completato nel computer di sviluppo

1. In Visual Studio, nel menu **Compila** , fare clic su **Pulisci soluzione**.

## <a name="next-steps"></a>Passaggi successivi

 Dopo aver creato questa personalizzazione di base a livello di documento per Excel, per approfondire le proprie conoscenze sullo sviluppo di personalizzazioni è possibile consultare gli argomenti seguenti:

- Attività di programmazione generali che è possibile eseguire nelle personalizzazioni a livello di documento: [programma personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md).

- Attività di programmazione specifiche per le personalizzazioni a livello di documento per Excel: [soluzioni Excel](../vsto/excel-solutions.md).

- Uso del modello a oggetti di Excel: [Panoramica del modello a oggetti di Excel](../vsto/excel-object-model-overview.md).

- Personalizzazione dell'interfaccia utente di Excel, ad esempio tramite l'aggiunta di una scheda personalizzata alla barra multifunzione o la creazione di un riquadro azioni personalizzato: [personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).

- Uso di oggetti estesi di Excel forniti dagli strumenti di sviluppo di Office in Visual Studio per eseguire attività che non sono possibili usando il modello a oggetti di Excel (ad esempio, l'hosting di controlli gestiti nei documenti e l'associazione di controlli Excel ai dati tramite il modello di data binding Windows Forms): [automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md).

- Compilazione e debug di personalizzazioni a livello di documento per Excel: [compilazione di soluzioni Office](../vsto/building-office-solutions.md).

- Distribuzione di personalizzazioni a livello di documento per Excel: [distribuire una soluzione Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Vedere anche

- [Panoramica &#40;dello sviluppo di soluzioni Office VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Soluzioni Excel](../vsto/excel-solutions.md)
- [Programma personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)
- [Panoramica del modello a oggetti di Excel](../vsto/excel-object-model-overview.md)
- [Automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)
- [Compilazione di soluzioni Office](../vsto/building-office-solutions.md)
- [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)
- [Panoramica sui modelli di progetto di Office](../vsto/office-project-templates-overview.md)
