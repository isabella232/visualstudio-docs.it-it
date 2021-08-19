---
title: Creare la prima personalizzazione a livello di documento per Excel
description: Creare una personalizzazione a livello di documento per Microsoft Excel. Le funzionalità create in questo tipo di soluzione sono disponibili solo quando si apre una cartella di lavoro specifica.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: bd69d27b399f237fddb2f543e28a236edfdb8603
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122114986"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-excel"></a>Procedura dettagliata: Creare la prima personalizzazione a livello di documento per Excel

  Questa procedura dettagliata introduttiva mostra come creare una personalizzazione a livello di documento per Microsoft Office Excel. Le funzionalità create in questo tipo di soluzione sono disponibili solo quando si apre una cartella di lavoro specifica. Una personalizzazione a livello di documento non può essere usata per apportare modifiche a un'intera applicazione, ad esempio per visualizzare una nuova scheda della barra multifunzione quando si apre una cartella di lavoro qualsiasi.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Vengono illustrate le attività seguenti:

- Creazione di un progetto cartella di lavoro di Excel.

- Aggiunta di testo a un foglio di lavoro ospitato nella finestra di progettazione di Visual Studio.

- Scrittura di codice che usa il modello a oggetti di Excel per aggiungere testo al foglio di lavoro personalizzato quando quest'ultimo viene aperta.

- Creazione ed esecuzione del progetto a scopo di test.

- Pulizia del progetto completato per rimuovere dal computer di sviluppo le impostazioni di sicurezza e i file di compilazione non necessari.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti

 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Creare il progetto

### <a name="to-create-a-new-excel-workbook-project-in-visual-studio"></a>Per creare un nuovo progetto cartella di lavoro di Excel in Visual Studio

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Scegliere **Nuovo** dal menu **File** e quindi fare clic su **Progetto**.
::: moniker range="vs-2017"
3. Nel riquadro dei modelli, espandere **Visual C#** o **Visual Basic**, quindi espandere **Office/SharePoint**.

4. Nel nodo **Office/SharePoint** espanso selezionare il **VSTO componenti aggiuntivi.**

5. Nell'elenco dei modelli di progetto scegliere un progetto Excel VSTO cartella di lavoro.

6. Nella casella **Nome** digitare **FirstWorkbookCustomization**.

7. Fare clic su **OK**.

8. Selezionare **Crea un nuovo documento dalla** procedura guidata Visual Studio Tools per Office Project **e** fare clic su **OK.**
::: moniker-end
::: moniker range=">=vs-2019"
3. Nella finestra **di dialogo Crea un nuovo Project** selezionare il Excel VSTO cartella **di** lavoro.

     [!INCLUDE[new-project-dialog-search](../vsto/includes/new-project-dialog-search-md.md)]

4. Fare clic su **Avanti**.

5. Digitare **FirstWorkbookCustomization nella** casella **Nome della** finestra di dialogo Configura il nuovo **progetto** e fare clic su **Crea.**

6. Selezionare **Crea un nuovo documento dalla** procedura guidata Visual Studio Tools per Office Project **e** fare clic su **OK.**
::: moniker-end
   - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea il **progetto FirstWorkbookCustomization** e aggiunge i file seguenti al progetto.

   - *FirstWorkbookCustomization*.xlsx: rappresenta Excel cartella di lavoro nel progetto. Contiene tutti i fogli di lavoro e i grafici.

   - Sheet1 (file con estensione *vb* per Visual Basic o *cs* per Visual C#): foglio di lavoro che fornisce l'area di progettazione e il codice per il primo foglio di lavoro nella cartella di lavoro. Per altre informazioni, vedere Elemento [host Worksheet.](../vsto/worksheet-host-item.md)

   - Sheet2 (file *con* estensione vb per Visual Basic o *cs* per Visual C#): foglio di lavoro che fornisce l'area di progettazione e il codice per il secondo foglio di lavoro nella cartella di lavoro.

   - Sheet3 (file *con* estensione vb per Visual Basic o *cs* per Visual C#): foglio di lavoro che fornisce l'area di progettazione e il codice per il terzo foglio di lavoro nella cartella di lavoro.

   - ThisWorkbook (file con estensione *vb* per Visual Basic o *cs* per Visual C#): contiene l'area di progettazione e il codice per le personalizzazioni a livello di cartella di lavoro. Per altre informazioni, vedere Elemento [host Workbook.](../vsto/workbook-host-item.md)

     Il file di codice Sheet1 viene aperto automaticamente nella finestra di progettazione.

## <a name="close-and-reopen-worksheets-in-the-designer"></a>Chiudere e riaprire i fogli di lavoro nella finestra di progettazione

 Se mentre si sviluppa il progetto si chiude intenzionalmente o accidentalmente una cartella di lavoro o un foglio di lavoro nella finestra di progettazione, è possibile riaprirlo.

### <a name="to-close-and-reopen-a-worksheet-in-the-designer"></a>Per chiudere e riaprire un foglio di lavoro nella finestra di progettazione

1. Chiudere la cartella di lavoro facendo clic **sul pulsante Chiudi** (X) per la finestra di progettazione.

2. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul file di codice **Sheet1** e **scegliere Progettazione visualizzazioni**.

     \- - oppure -

     In **Esplora soluzioni** fare doppio clic sul file **di codice Sheet1.**

## <a name="add-text-to-a-worksheet-in-the-designer"></a>Aggiungere testo a un foglio di lavoro nella finestra di progettazione

 È possibile progettare l'interfaccia utente della personalizzazione modificando il foglio di lavoro aperto nella finestra di progettazione. Ad esempio, è possibile aggiungere testo alle celle, applicare formule o aggiungere controlli di Excel. Per altre informazioni sull'uso della finestra di progettazione, Office [progetti nell'ambiente Visual Studio .](../vsto/office-projects-in-the-visual-studio-environment.md)

### <a name="to-add-text-to-a-worksheet-by-using-the-designer"></a>Per aggiungere testo a un foglio di lavoro mediante la finestra di progettazione

1. Nel foglio di lavoro aperto nella finestra di progettazione selezionare la cella **A1** e quindi digitare il testo seguente.

     **This text was added by using the designer.**

> [!WARNING]
> Se si aggiunge questa riga di testo alla cella **A2,** verrà sovrascritta da altro codice in questo esempio.

## <a name="add-text-to-a-worksheet-programmatically"></a>Aggiungere testo a un foglio di lavoro a livello di codice

 Aggiungere quindi codice al file di codice Sheet1. Il nuovo codice usa il modello a oggetti di Excel per aggiungere nella cartella di lavoro una seconda riga di testo. Per impostazione predefinita, il file di codice Sheet1 contiene il seguente codice generato:

- Una definizione parziale della classe `Sheet1`, che rappresenta il modello di programmazione del foglio di lavoro e consente di accedere al modello a oggetti di Excel. Per altre informazioni, vedere [Elemento host Worksheet e](../vsto/worksheet-host-item.md) Panoramica del modello a oggetti di [Word.](../vsto/word-object-model-overview.md) Il resto della classe `Sheet1` viene definito in un file di codice nascosto che l'utente non deve modificare.

- I gestori eventi `Sheet1_Startup` e `Sheet1_Shutdown` . Questi gestori eventi vengono chiamati quando Excel carica e scarica la personalizzazione. Usare questi gestori eventi per inizializzare la personalizzazione quando viene caricata e per eseguire la pulizia delle risorse usate dalla personalizzazione quando viene scaricata. Per altre informazioni, vedere [Eventi nei progetti Office .](../vsto/events-in-office-projects.md)

### <a name="to-add-a-second-line-of-text-to-the-worksheet-by-using-code"></a>Per aggiungere al foglio di lavoro una seconda riga di codice mediante codice

1. In **Esplora soluzioni** fare clic con il pulsante destro **del mouse su Sheet1** e quindi scegliere Visualizza **codice.**

     Il file di codice verrà aperto in Visual Studio.

2. Sostituire il gestore eventi `Sheet1_Startup` con il codice seguente. Quando viene aperto il foglio Sheet1, questo codice aggiunge una seconda riga di testo al foglio di lavoro.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelWorkbookTutorial/Sheet1.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ExcelWorkbookTutorial/Sheet1.vb" id="Snippet1":::

## <a name="test-the-project"></a>Testare il progetto

### <a name="to-test-your-workbook"></a>Per testare la cartella di lavoro

1. Premere **F5** per compilare ed eseguire il progetto.

     Quando si compila il progetto, il codice viene compilato in un assembly associato alla cartella di lavoro. Visual Studio inserisce una copia della cartella di lavoro e l'assembly nella cartella dell'output di compilazione del progetto e configura le impostazioni di sicurezza nel computer di sviluppo in modo da consentire l'esecuzione della personalizzazione. Per altre informazioni, vedere [Compilare Office soluzioni](../vsto/building-office-solutions.md).

2. Nella cartella di lavoro verificare che sia visualizzato il testo seguente.

     **This text was added by using the designer.**

     **This text was added by using code.**

3. Chiudere la cartella di lavoro.

## <a name="clean-up-the-project"></a>Pulire il progetto

 Al termine dello sviluppo di un progetto, è necessario rimuovere le impostazioni di sicurezza e i file contenuti nella cartella dell'output di compilazione creati dal processo di compilazione.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Per pulire il progetto completato nel computer di sviluppo

1. In Visual Studio, nel menu **Compila** , fare clic su **Pulisci soluzione**.

## <a name="next-steps"></a>Passaggi successivi

 Dopo aver creato questa personalizzazione di base a livello di documento per Excel, per approfondire le proprie conoscenze sullo sviluppo di personalizzazioni è possibile consultare gli argomenti seguenti:

- Attività di programmazione generali che è possibile eseguire nelle personalizzazioni a livello di documento: [Programmare personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md).

- Attività di programmazione specifiche delle personalizzazioni a livello di documento per Excel: [Excel soluzioni](../vsto/excel-solutions.md).

- Uso del modello a oggetti di Excel: [Excel panoramica del modello a oggetti](../vsto/excel-object-model-overview.md).

- Personalizzazione dell'interfaccia utente Excel, ad esempio, aggiungendo una scheda personalizzata alla barra multifunzione o creando un riquadro azioni personalizzato: Office personalizzazione [dell'interfaccia utente.](../vsto/office-ui-customization.md)

- Uso di oggetti Excel estesi forniti dagli strumenti di sviluppo Office in Visual Studio per eseguire attività che non sono possibili usando il modello a oggetti di Excel (ad esempio, l'hosting di controlli gestiti nei documenti e l'associazione di controlli Excel ai dati tramite il modello data binding di Windows Forms): [automatizzare il Excel](../vsto/automating-excel-by-using-extended-objects.md)usando oggetti estesi.

- Compilazione e debug di personalizzazioni a livello di documento per Excel: [Compilare Office soluzioni](../vsto/building-office-solutions.md).

- Distribuzione di personalizzazioni a livello di documento per Excel: [distribuire una soluzione Office personalizzata.](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>Vedi anche

- [Office sullo sviluppo di soluzioni &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Excel soluzioni](../vsto/excel-solutions.md)
- [Programmare personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)
- [Excel panoramica del modello a oggetti](../vsto/excel-object-model-overview.md)
- [Automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Office Personalizzazione dell'interfaccia utente](../vsto/office-ui-customization.md)
- [Compilare Office soluzioni](../vsto/building-office-solutions.md)
- [Distribuire una soluzione Office distribuzione](../vsto/deploying-an-office-solution.md)
- [Office dei modelli di progetto](../vsto/office-project-templates-overview.md)
