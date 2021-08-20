---
title: 'Procedura dettagliata: Creare il primo VSTO per Word'
description: Creare un componente aggiuntivo a livello di applicazione per Microsoft Word. Questa funzionalità è disponibile per l'applicazione stessa, indipendentemente da quali documenti sono aperti.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Word [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 0c6f06400e1f35af9cce874d601c03f6cf1dc4a1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155460"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-word"></a>Procedura dettagliata: Creare il primo VSTO per Word
  Questa procedura dettagliata introduttiva illustra come creare un componente aggiuntivo VSTO per Microsoft Office Word.  Le funzionalità create in questo tipo di soluzione sono disponibili per l'applicazione, indipendentemente da quali documenti vengano aperti.

 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]

 Vengono illustrate le attività seguenti:

- Creazione di un progetto di componente aggiuntivo VSTO di Word.

- Scrittura di codice che usa il modello a oggetti di Word per aggiungere testo a un documento quando quest'ultimo viene salvato.

- Creazione ed esecuzione del progetto a scopo di test.

- Pulizia del progetto completato, per fare in modo che il componente aggiuntivo VSTO non venga più eseguito automaticamente nel computer di sviluppo.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Creare il progetto

### <a name="to-create-a-new-word-vsto-add-in-project-in-visual-studio"></a>Per creare un nuovo progetto per un componente aggiuntivo VSTO di Word in Visual Studio

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Scegliere **Nuovo** dal menu **File** e quindi fare clic su **Progetto**.

3. Nel riquadro dei modelli, espandere **Visual C#** o **Visual Basic**, quindi espandere **Office/SharePoint**.

4. Nel nodo **Office/SharePoint** espanso, selezionare il nodo **Componenti aggiuntivi di Office** .

5. Nell'elenco dei modelli di progetto scegliere un progetto del componente aggiuntivo VSTO di Word.

6. Nella casella **Nome** digitare **FirstWordAddIn**.

7. Fare clic su **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea il **progetto FirstWordAddIn** e apre il file di codice ThisAddIn nell'editor.

## <a name="write-code-to-add-text-to-the-saved-document"></a>Scrivere codice per aggiungere testo al documento salvato
 Aggiungere quindi codice al file di codice ThisAddIn. Il nuovo codice usa il modello a oggetti di Word per aggiungere testo boilerplate in ogni documento salvato. Per impostazione predefinita, il file di codice ThisAddIn contiene il seguente codice generato:

- Una definizione parziale della classe `ThisAddIn` . Questa classe fornisce un punto di ingresso per il codice e fornisce l'accesso al modello a oggetti di Word. Per altre informazioni, vedere [Programmi VSTO componenti aggiuntivi](../vsto/programming-vsto-add-ins.md). Il resto della classe è definito in un file di codice nascosto `ThisAddIn` che non è necessario modificare.

- I gestori eventi `ThisAddIn_Startup` e `ThisAddIn_Shutdown` . Questi gestori eventi vengono chiamati quando Word carica e scarica il componente aggiuntivo VSTO. Usare questi gestori eventi per inizializzare il componente aggiuntivo VSTO al momento del caricamento e per eseguire la pulizia delle risorse usate dal componente aggiuntivo VSTO quando viene scaricato. Per altre informazioni, vedere [Eventi nei progetti Office .](../vsto/events-in-office-projects.md)

### <a name="to-add-a-paragraph-of-text-to-the-saved-document"></a>Per aggiungere un paragrafo di testo nel documento salvato

1. Nel file di codice ThisAddIn, aggiungere il codice seguente alla classe `ThisAddIn` . Il nuovo codice definisce un gestore eventi per l'evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>, generato quando un documento viene salvato.

    Quando l'utente salva un documento, il gestore eventi aggiunge nuovo testo all'inizio del documento.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/FirstWordAddIn/ThisAddIn.vb" id="Snippet1":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs" id="Snippet1":::

   > [!NOTE]
   > Questo codice usa il valore di indice 1 per accedere al primo paragrafo della raccolta <xref:Microsoft.Office.Interop.Word._Document.Paragraphs%2A>. Anche se Visual Basic e Visual C# usano matrici in base 0, il limite inferiore di matrice della maggior parte delle raccolte del modello a oggetti di Word è 1. Per altre informazioni, vedere [Scrivere codice in Office soluzioni](../vsto/writing-code-in-office-solutions.md).

2. Se si usa C#, aggiungere il seguente codice obbligatorio al gestore eventi `ThisAddIn_Startup` . Tale codice viene usato per connettere il gestore eventi `Application_DocumentBeforeSave` all'evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> .

    :::code language="csharp" source="../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs" id="Snippet2":::

   Per modificare il documento quando viene salvato, negli esempi di codice precedenti vengono usati gli oggetti seguenti:

- Il campo `Application` della classe `ThisAddIn` . Il campo `Application` restituisce un oggetto <xref:Microsoft.Office.Interop.Word.Application> che rappresenta l'istanza corrente di Word.

- Il parametro `Doc` del gestore eventi dell'evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> . Il parametro `Doc` è un oggetto <xref:Microsoft.Office.Interop.Word.Document> che rappresenta il documento salvato. Per altre informazioni, vedere Panoramica [del modello a oggetti di Word.](../vsto/word-object-model-overview.md)

## <a name="test-the-project"></a>Testare il progetto

### <a name="to-test-the-project"></a>Per testare il progetto

1. Premere **F5** per compilare ed eseguire il progetto.

     Quando si crea il progetto, il codice viene compilato in un assembly incluso nella cartella di output di compilazione relativa al progetto. Inoltre, Visual Studio crea un set di voci del Registro di sistema che consentono a Word di individuare e caricare il componente aggiuntivo VSTO e di configurare le impostazioni di sicurezza nel computer di sviluppo; in questo modo, si attiva l'esecuzione del componente aggiuntivo VSTO. Per altre informazioni, vedere [Compilare Office soluzioni](../vsto/building-office-solutions.md).

2. In Word, salvare il documento attivo.

3. Verificare che il seguente testo venga aggiunto al documento.

     **This text was added by using code.**

4. Chiudere Word.

## <a name="clean-up-the-project"></a>Pulire il progetto
 Al termine dello sviluppo di un progetto, rimuovere l'assembly del componente aggiuntivo VSTO, le voci del Registro di sistema e le impostazioni di sicurezza dal computer di sviluppo. In caso contrario, il componente aggiuntivo VSTO verrà eseguito ogni volta che si avvia Word nel computer di sviluppo.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Per pulire il progetto completato nel computer di sviluppo

1. In Visual Studio, nel menu **Compila** , fare clic su **Pulisci soluzione**.

## <a name="next-steps"></a>Passaggi successivi
 Ora che è stato creato un componente aggiuntivo VSTO di base per Word, è possibile acquisire altre informazioni sullo sviluppo di componenti aggiuntivi VSTO in questi argomenti:

- Attività di programmazione generali che è possibile VSTO componenti aggiuntivi: programma VSTO [componenti aggiuntivi](../vsto/programming-vsto-add-ins.md).

- Attività di programmazione specifiche di Word VSTO componenti aggiuntivi: [soluzioni Word](../vsto/word-solutions.md).

- Uso del modello a oggetti di Word: [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md).

- Personalizzazione dell'interfaccia utente di Word, ad esempio aggiungendo una scheda personalizzata alla barra multifunzione o creando un riquadro attività personalizzato: Office personalizzazione [dell'interfaccia utente.](../vsto/office-ui-customization.md)

- Compilazione e debug VSTO componenti aggiuntivi per Word: [Compilare Office soluzioni](../vsto/building-office-solutions.md).

- Distribuzione VSTO componenti aggiuntivi per Word: [distribuire una Office soluzione](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Vedi anche
- [Office sullo sviluppo di soluzioni &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Soluzioni Word](../vsto/word-solutions.md)
- [Programmi VSTO componenti aggiuntivi](../vsto/programming-vsto-add-ins.md)
- [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)
- [Office Personalizzazione dell'interfaccia utente](../vsto/office-ui-customization.md)
- [Creare Office soluzioni](../vsto/building-office-solutions.md)
- [Distribuire una soluzione Office distribuzione](../vsto/deploying-an-office-solution.md)
- [Office panoramica dei modelli di progetto](../vsto/office-project-templates-overview.md)
