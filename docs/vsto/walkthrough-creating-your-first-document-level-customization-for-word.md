---
title: Creare la prima personalizzazione a livello di documento per Word
description: Creare una personalizzazione a livello di documento per Microsoft Word. Le funzionalità create in questo tipo di soluzione sono disponibili solo quando si apre un documento specifico.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, creating your first project
- Word [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 7c039abd3a6637afe56e80164cb3add830dc44ea
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155486"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-word"></a>Procedura dettagliata: Creare la prima personalizzazione a livello di documento per Word

  Questa procedura dettagliata introduttiva mostra come creare una personalizzazione a livello di documento per Microsoft Office Word. Le funzionalità create in questo tipo di soluzione sono disponibili solo quando si apre un documento specifico. Una personalizzazione a livello di documento non può essere usata per apportare modifiche a un'intera applicazione, ad esempio per visualizzare una nuova scheda della barra multifunzione quando si apre un documento qualsiasi.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Vengono illustrate le attività seguenti:

- Creazione di un progetto relativo al documento di Word

- Aggiunta di testo al documento ospitato nella finestra di progettazione di Visual Studio.

- Scrittura di codice che usa il modello a oggetti di Word per aggiungere testo al documento personalizzato quando quest'ultimo viene aperto.

- Creazione ed esecuzione del progetto a scopo di test.

- Pulizia del progetto per rimuovere dal computer di sviluppo le impostazioni di sicurezza e i file di compilazione non necessari.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti

 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Creare il progetto

### <a name="to-create-a-new-word-document-project-in-visual-studio"></a>Per creare un progetto di documento di Word in Visual Studio

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Scegliere **Nuovo** dal menu **File** e quindi fare clic su **Progetto**.
::: moniker range="vs-2017"
3. Nel riquadro dei modelli, espandere **Visual C#** o **Visual Basic**, quindi espandere **Office/SharePoint**.

4. Nel nodo **Office/SharePoint** espandere selezionare il VSTO **componenti aggiuntivi.**

5. Nell'elenco dei modelli di progetto selezionare un progetto documento VSTO Word.

6. Nella casella **Nome** digitare **FirstDocumentCustomization**.

7. Fare clic su **OK**.

8. Selezionare **Crea un nuovo documento dalla** procedura guidata Visual Studio Tools per Office Project **e** fare clic su **OK.**
::: moniker-end
::: moniker range=">=vs-2019"
3. Nella finestra **di dialogo Crea un nuovo Project** selezionare il progetto Documento VSTO **Word.**

     [!INCLUDE[new-project-dialog-search](../vsto/includes/new-project-dialog-search-md.md)]

4. Fare clic su **Avanti**.

5. Digitare **FirstWorkbookCustomization** nella **casella Nome** della finestra di dialogo Configura il nuovo **progetto** e fare clic su **Crea**.

6. Selezionare **Crea un nuovo documento dalla** procedura guidata Visual Studio Tools per Office Project **e** fare clic su **OK.**
::: moniker-end
   - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea il **progetto FirstDocumentCustomization** e aggiunge il documento **FirstDocumentCustomization** e il file di codice ThisDocument al progetto. Il **documento FirstDocumentCustomization** viene aperto automaticamente nella finestra di progettazione.

## <a name="close-and-reopen-the-document-in-the-designer"></a>Chiudere e riaprire il documento nella finestra di progettazione

 Se mentre si sviluppa il progetto nella finestra di progettazione si chiude intenzionalmente o accidentalmente il documento, è possibile riaprirlo.

### <a name="to-close-and-reopen-the-document-in-the-designer"></a>Per chiudere e riaprire il documento nella finestra di progettazione

1. Chiudere il documento facendo clic sul **pulsante Chiudi** (X) per la finestra di progettazione.

2. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul file di codice **ThisDocument** e **scegliere Progettazione visualizzazioni**.

     \- - oppure -

     In **Esplora soluzioni** fare doppio clic sul file **di codice ThisDocument.**

## <a name="add-text-to-the-document-in-the-designer"></a>Aggiungere testo al documento nella finestra di progettazione

 È possibile progettare l'interfaccia utente della personalizzazione modificando il documento che viene aperto nella finestra di progettazione. Ad esempio, è possibile aggiungere testo, tabelle o controlli Word. Per altre informazioni su come usare la finestra di progettazione, vedere Office [progetti nell'ambiente Visual Studio .](../vsto/office-projects-in-the-visual-studio-environment.md)

### <a name="to-add-text-to-your-document-by-using-the-designer"></a>Per aggiungere testo al documento con la finestra di progettazione

1. Nel documento aperto nella finestra di progettazione, digitare il testo seguente.

     **This text was added by using the designer.**

## <a name="add-text-to-the-document-programmatically"></a>Aggiungere testo al documento a livello di codice

 Quindi, aggiungere codice al file di codice ThisDocument. Il nuovo codice usa il modello a oggetti di Word per aggiungere nel documento un secondo paragrafo di testo. Per impostazione predefinita, il file di codice ThisDocument contiene il seguente codice generato:

- Una definizione parziale della classe `ThisDocument`, che rappresenta il modello di programmazione del documento e consente di accedere al modello a oggetti di Word. Per altre informazioni, vedere Elemento [host documento](../vsto/document-host-item.md) e Panoramica del modello a oggetti [di Word.](../vsto/word-object-model-overview.md) Il resto della classe `ThisDocument` viene definito in un file di codice nascosto che l'utente non deve modificare.

- I gestori eventi `ThisDocument_Startup` e `ThisDocument_Shutdown` . Questi gestori eventi vengono chiamati quando il documento viene aperto o chiuso. Possono essere usati per inizializzare la personalizzazione quando il documento viene aperto e per liberare le risorse usate dalla personalizzazione quando il documento viene chiuso. Per altre informazioni, vedere [Eventi nei Office .](../vsto/events-in-office-projects.md)

### <a name="to-add-a-second-paragraph-of-text-to-the-document-by-using-code"></a>Per aggiungere nel documento un secondo paragrafo di testo usando il codice

1. In **Esplora soluzioni** fare clic con il pulsante destro **del mouse su ThisDocument** e quindi **scegliere Visualizza codice**.

     Il file di codice verrà aperto in Visual Studio.

2. Sostituire il gestore eventi `ThisDocument_Startup` con il codice seguente. Quando il documento viene aperto, questo codice aggiunge un secondo paragrafo di testo al documento.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/FirstDocumentCustomization/ThisDocument.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/FirstDocumentCustomization/ThisDocument.cs" id="Snippet1":::

    > [!NOTE]
    > Questo codice usa il valore di indice 1 per accedere al primo paragrafo contenuto nella proprietà <xref:Microsoft.Office.Tools.Word.Document.Paragraphs%2A>. Anche se Visual Basic e Visual C# usano matrici in base 0, il limite inferiore di matrice della maggior parte delle raccolte del modello a oggetti di Word è 1. Per altre informazioni, vedere [Scrivere codice in Office soluzioni](../vsto/writing-code-in-office-solutions.md).

## <a name="test-the-project"></a>Testare il progetto

### <a name="to-test-your-document"></a>Per testare il documento

1. Premere **F5** per compilare ed eseguire il progetto.

     Quando si compila il progetto, il codice viene compilato in un assembly associato al documento. Visual Studio inserisce una copia del documento e l'assembly nella cartella dell'output di compilazione del progetto e configura le impostazioni di sicurezza nel computer di sviluppo in modo da consentire l'esecuzione della personalizzazione. Per altre informazioni, vedere [Compilare Office soluzioni](../vsto/building-office-solutions.md).

2. Nel documento, verificare che sia visualizzato il testo seguente.

     **This text was added by using the designer.**

     **This text was added by using code.**

3. Chiudere il documento.

## <a name="clean-up-the-project"></a>Pulire il progetto

 Al termine dello sviluppo di un progetto, è necessario rimuovere le impostazioni di sicurezza e i file contenuti nella cartella dell'output di compilazione creati dal processo di compilazione.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Per pulire il progetto completato nel computer di sviluppo

1. In Visual Studio, nel menu **Compila** , fare clic su **Pulisci soluzione**.

## <a name="next-steps"></a>Passaggi successivi

 Dopo aver creato questa personalizzazione di base a livello di documento per Word, per approfondire le proprie conoscenze sullo sviluppo di personalizzazioni è possibile consultare gli argomenti seguenti:

- Attività di programmazione generali che è possibile eseguire nelle personalizzazioni a livello di documento: [Programmare personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md).

- Attività di programmazione specifiche delle personalizzazioni a livello di documento per Word: [soluzioni Word](../vsto/word-solutions.md).

- Utilizzo del modello a oggetti di Word: [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md).

- Personalizzazione dell'interfaccia utente di Word, ad esempio aggiungendo una scheda personalizzata alla barra multifunzione o creando un riquadro azioni personalizzato: Office [personalizzazione dell'interfaccia utente](../vsto/office-ui-customization.md).

- Uso di oggetti Word estesi forniti dalle soluzioni Office in Visual Studio per eseguire attività che non sono possibili usando il modello a oggetti di Word , ad esempio l'hosting di controlli gestiti nei documenti e l'associazione dei controlli di Word ai dati tramite il modello data binding forms di Windows: [Automatizzare Word](../vsto/automating-word-by-using-extended-objects.md)usando oggetti estesi .

- Compilazione e debug di personalizzazioni a livello di documento per Word: [Compilare](../vsto/building-office-solutions.md)Office soluzioni .

- Distribuzione di personalizzazioni a livello di documento per Word: [distribuire una Office soluzione](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Vedi anche

- [Office panoramica dello sviluppo di soluzioni &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Soluzioni Word](../vsto/word-solutions.md)
- [Programmare personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)
- [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)
- [Automatizzare Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)
- [Office Personalizzazione dell'interfaccia utente](../vsto/office-ui-customization.md)
- [Compilare Office soluzioni](../vsto/building-office-solutions.md)
- [Distribuire una soluzione Office distribuzione](../vsto/deploying-an-office-solution.md)
- [Office dei modelli di progetto](../vsto/office-project-templates-overview.md)
