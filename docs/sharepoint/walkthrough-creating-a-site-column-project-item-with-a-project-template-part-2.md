---
title: Creare un elemento di progetto colonna del sito con il modello di progetto, parte 2
titleSuffix: ''
description: Aggiungere una procedura guidata a un modello di progetto colonna del sito per raccogliere dati dagli utenti quando usano il modello per creare un progetto SharePoint contenente l'elemento di progetto.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: c4530a43787b2e29c2600476a44c808132d668ceaa89b851efeddd403c2c30e6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121352818"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-2"></a>Procedura dettagliata: Creare un elemento di progetto colonna del sito con un modello di progetto, parte 2
  Dopo aver definito un tipo personalizzato di SharePoint elemento di progetto e associato a un modello di progetto in Visual Studio, è anche possibile fornire una procedura guidata per il modello. È possibile usare la procedura guidata per raccogliere informazioni dagli utenti quando usano il modello per creare un nuovo progetto che contiene l'elemento di progetto. Le informazioni raccolte possono essere usate per inizializzare l'elemento di progetto.

 In questa procedura dettagliata si aggiungerà una procedura guidata al modello di progetto Colonna del sito illustrata in Procedura dettagliata: Creazione di una colonna del sito Project elemento con un [modello di Project, parte 1.](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md) Quando un utente crea un progetto colonna del sito, la procedura guidata raccoglie informazioni sulla colonna del sito (ad esempio il tipo di base e il gruppo) e aggiunge queste informazioni al file *Elements.xml* nel nuovo progetto.

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di una procedura guidata per un tipo SharePoint elemento di progetto personalizzato associato a un modello di progetto.

- Definizione di un'interfaccia utente personalizzata della procedura guidata simile alle procedure guidate incorporate per SharePoint progetti in Visual Studio.

- Creazione di *SharePoint comandi personalizzati* usati per chiamare nel sito SharePoint locale durante l'esecuzione della procedura guidata. SharePoint sono metodi che possono essere usati dalle estensioni Visual Studio per chiamare le API nel modello a oggetti SharePoint server. Per altre informazioni, vedere [Chiamata nei modelli SharePoint a oggetti .](../sharepoint/calling-into-the-sharepoint-object-models.md)

- Uso di parametri sostituibili per SharePoint file di progetto con i dati raccolti nella procedura guidata.

- Creazione di un nuovo file con estensione snk in ogni nuova istanza del progetto Colonna del sito. Questo file viene usato per firmare l'output del progetto in modo che l SharePoint assembly della soluzione possa essere distribuito nella Global Assembly Cache.

- Debug e test della procedura guidata.

> [!NOTE]
> Per una serie di flussi di lavoro di esempio, vedere SharePoint [di flusso di lavoro.](/sharepoint/dev/general-development/sharepoint-workflow-samples)

## <a name="prerequisites"></a>Prerequisiti
 Per eseguire questa procedura dettagliata, è innanzitutto necessario creare la soluzione SiteColumnProjectItem completando Procedura dettagliata: Creazione di una colonna del sito Project item con un [modello di Project, parte 1.](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)

 Per completare questa procedura dettagliata sono necessari anche i componenti seguenti nel computer di sviluppo:

- Edizioni supportate di Windows, SharePoint e Visual Studio.

- SDK Visual Studio. Questa procedura dettagliata usa il **modello di Project VSIX** nell'SDK per creare un pacchetto VSIX per distribuire l'elemento di progetto. Per altre informazioni, vedere [Estendere gli strumenti SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  La conoscenza dei concetti seguenti è utile, ma non necessaria, per completare la procedura dettagliata:

- Procedure guidate per i modelli di progetto e di elemento in Visual Studio. Per altre informazioni, [vedere Procedura: Usare procedure guidate](../extensibility/how-to-use-wizards-with-project-templates.md) con Project modelli e l'interfaccia. <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>

- Colonne del sito in SharePoint. Per altre informazioni, vedere [Colonne.](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14))

## <a name="understand-the-wizard-components"></a>Comprendere i componenti della procedura guidata
 La procedura guidata illustrata in questa procedura dettagliata contiene diversi componenti. Nella tabella seguente vengono descritti questi componenti.

|Componente|Descrizione|
|---------------|-----------------|
|Implementazione della procedura guidata|Si tratta di una classe, denominata `SiteColumnProjectWizard` , che implementa <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> l'interfaccia . Questa interfaccia definisce i metodi che Visual Studio quando la procedura guidata viene avviata e completata e in determinati momenti durante l'esecuzione della procedura guidata.|
|Interfaccia utente della procedura guidata|Si tratta di una finestra basata su WPF, denominata `WizardWindow` . Questa finestra include due controlli utente, `Page1` denominati e `Page2` . Questi controlli utente rappresentano le due pagine della procedura guidata.<br /><br /> In questa procedura dettagliata il metodo <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> dell'implementazione della procedura guidata visualizza l'interfaccia utente della procedura guidata.|
|Modello di dati della procedura guidata|Si tratta di una classe intermedia, denominata , che fornisce un livello tra l'interfaccia utente della procedura guidata e `SiteColumnWizardModel` l'implementazione della procedura guidata. Questo esempio usa questa classe per astrarre l'implementazione della procedura guidata e l'interfaccia utente della procedura guidata l'una dall'altra; Questa classe non è un componente obbligatorio di tutte le procedure guidate.<br /><br /> In questa procedura dettagliata l'implementazione della procedura guidata passa un oggetto alla finestra della `SiteColumnWizardModel` procedura guidata quando visualizza l'interfaccia utente della procedura guidata. L'interfaccia utente della procedura guidata usa i metodi di questo oggetto per salvare i valori dei controlli nell'interfaccia utente ed eseguire attività come la verifica della validità dell'URL del sito di input. Al termine della procedura guidata, l'implementazione della procedura guidata usa l'oggetto per `SiteColumnWizardModel` determinare lo stato finale dell'interfaccia utente.|
|Project di firma|Si tratta di una classe helper, denominata , usata dall'implementazione della procedura guidata per creare un nuovo `ProjectSigningManager` file key.snk in ogni nuova istanza del progetto.|
|SharePoint (comandi)|Si tratta di metodi utilizzati dal modello di dati della procedura guidata per chiamare nel sito di SharePoint locale durante l'esecuzione della procedura guidata. Poiché SharePoint comandi devono avere come destinazione .NET Framework 3.5, questi comandi vengono implementati in un assembly diverso rispetto al resto del codice della procedura guidata.|

## <a name="create-the-projects"></a>Creare i progetti
 Per completare questa procedura dettagliata, è necessario aggiungere diversi progetti alla soluzione SiteColumnProjectItem creata in Procedura dettagliata: Creare un elemento di progetto colonna del sito con un modello di [progetto, parte 1:](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)

- Un progetto WPF. Si implementerà <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> l'interfaccia e si definirà l'interfaccia utente della procedura guidata in questo progetto.

- Progetto di libreria di classi che definisce i SharePoint seguenti. Questo progetto deve essere the.NET Framework 3.5.

  Avviare la procedura dettagliata creando i progetti.

#### <a name="to-create-the-wpf-project"></a>Per creare il progetto WPF

1. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aprire la soluzione SiteColumnProjectItem.

2. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo della soluzione **SiteColumnProjectItem,** scegliere Aggiungi **e** quindi scegliere Nuovo **Project**.

3. Nella parte superiore della finestra di dialogo **Aggiungi nuovo Project** verificare che nell'elenco delle versioni del .NET Framework **4.5** sia selezionata la versione .NET Framework.

4. Espandere il **nodo Visual C#** o **il nodo Visual Basic** e scegliere il **Windows** nodo.

5. Nell'elenco dei modelli di progetto scegliere Libreria di controlli utente **WPF,** assegnare al progetto il nome **ProjectTemplateWizard** e quindi scegliere **il pulsante OK.**

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il **progetto ProjectTemplateWizard** alla soluzione e apre il file UserControl1.xaml predefinito.

6. Eliminare il file UserControl1.xaml dal progetto.

#### <a name="to-create-the-sharepoint-commands-project"></a>Per creare il progetto SharePoint comandi

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo della soluzione SiteColumnProjectItem, scegliere Aggiungi **e** quindi scegliere **Nuovo Project**.

2. Nella parte superiore della finestra **di dialogo Project** nuova versione scegliere .NET Framework **3.5** nell'elenco delle versioni del .NET Framework.

3. Espandere il **nodo Visual C#** **o il Visual Basic** e quindi scegliere il **Windows** nodo.

4. Scegliere il **modello di progetto** Libreria di classi, assegnare al progetto il nome **SharePointCommands** e quindi scegliere **il pulsante OK.**

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il **progetto SharePointCommands** alla soluzione e apre il file di codice Class1 predefinito.

5. Eliminare il file di codice Class1 dal progetto.

## <a name="configure-the-projects"></a>Configurare i progetti
 Prima di creare la procedura guidata, è necessario aggiungere alcuni file di codice e riferimenti ad assembly ai progetti.

#### <a name="to-configure-the-wizard-project"></a>Per configurare il progetto della procedura guidata

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo del progetto **ProjectTemplateWizard** e quindi scegliere **Proprietà.**

2. In Progettazione **Project scegliere** la  scheda Applicazione per un progetto  Visual C# o la scheda Compila per un Visual Basic progetto.

3. Assicurarsi che il framework di destinazione sia impostato sul .NET Framework 4.5, non sul profilo .NET Framework 4.5.

     Per altre informazioni, vedere [Procedura: Impostare come destinazione una versione del .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

4. Aprire il menu di scelta rapida **per il progetto ProjectTemplateWizard,** scegliere **Aggiungi** e quindi **nuovo elemento.**

5. Scegliere **l'elemento Finestra (WPF),** assegnare all'elemento il nome **WizardWindow** e quindi scegliere **il pulsante** Aggiungi.

6. Aggiungere due **elementi Controllo utente (WPF)** al progetto e assegnare loro i nomi **Page1** **e Page2.**

7. Aggiungere quattro file di codice al progetto e assegnare loro i nomi seguenti:

    - SiteColumnProjectWizard

    - SiteColumnWizardModel

    - ProjectSigningManager

    - CommandIds

8. Aprire il menu di scelta rapida per il nodo del progetto **ProjectTemplateWizard** e quindi scegliere **Aggiungi riferimento.**

9. Espandere il **nodo Assembly,** scegliere il **nodo Estensioni** e quindi selezionare le caselle di controllo accanto agli assembly seguenti:

    - EnvDTE

    - Microsoft.VisualStudio.OLE.Interop

    - Microsoft.VisualStudio. SharePoint

    - Microsoft.VisualStudio.Shell.11.0

    - Microsoft.VisualStudio.Shell.Interop.10.0

    - Microsoft.VisualStudio.Shell.Interop.11.0

    - Microsoft.VisualStudio.TemplateWizardInterface

10. Scegliere il **pulsante OK** per aggiungere gli assembly al progetto.

11. In **Esplora soluzioni**, nella cartella **Riferimenti** per il **progetto ProjectTemplateWizard** scegliere **EnvDTE.**

12. Nella finestra **Proprietà** modificare il valore della proprietà Incorpora tipi **di** interoperabilità in **False.**

13. Se si sta sviluppando un progetto Visual Basic, importare lo spazio dei nomi ProjectTemplateWizard nel progetto usando Project **Designer.**

     Per altre informazioni, [vedere Procedura: Aggiungere o rimuovere spazi dei ](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)nomi importati &#40;Visual Basic&#41;.

#### <a name="to-configure-the-sharepointcommands-project"></a>Per configurare il progetto SharePointcommands

1. In **Esplora soluzioni** scegliere il **nodo del progetto SharePointCommands.**

2. Sulla barra dei menu scegliere **Project**, Aggiungi **elemento esistente**.

3. Nella finestra **di dialogo Aggiungi** elemento esistente passare alla cartella che contiene i file di codice per il progetto ProjectTemplateWizard e quindi scegliere il file di codice **CommandIds.**

4. Scegliere la freccia accanto al **pulsante** Aggiungi e quindi scegliere l'opzione **Aggiungi** come collegamento nel menu visualizzato.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il file di codice **al progetto SharePointCommands** come collegamento. Il file di codice si trova nel **progetto ProjectTemplateWizard,** ma anche il codice nel file viene compilato nel **progetto SharePointCommands.**

5. Nel **progetto SharePointCommands** aggiungere un altro file di codice denominato Commands.

6. Scegliere il progetto SharePointCommands e quindi nella barra dei menu scegliere **Project**  >  **Aggiungi riferimento.**

7. Espandere il **nodo Assembly,** scegliere il **nodo Estensioni** e quindi selezionare le caselle di controllo accanto agli assembly seguenti:

    - Microsoft. SharePoint

    - Microsoft.VisualStudio. SharePoint. Comandi

8. Scegliere il **pulsante OK** per aggiungere gli assembly al progetto.

## <a name="create-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>Creare il modello della procedura guidata, il gestore della firma e gli SHAREPOINT comando
 Aggiungere codice al progetto ProjectTemplateWizard per implementare i componenti seguenti nell'esempio:

- ID SharePoint comando. Queste stringhe identificano SharePoint comandi utilizzati dalla procedura guidata. Più avanti in questa procedura dettagliata si aggiungerà codice al progetto SharePointCommands per implementare i comandi.

- Modello di dati della procedura guidata.

- Gestore della firma del progetto.

  Per altre informazioni su questi componenti, vedere Informazioni [sui componenti della procedura guidata.](#understand-the-wizard-components)

#### <a name="to-define-the-sharepoint-command-ids"></a>Per definire gli ID SharePoint di comando

1. Nel progetto ProjectTemplateWizard aprire il file di codice CommandIds e quindi sostituire l'intero contenuto del file con il codice seguente.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs" id="Snippet5":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb" id="Snippet5":::

#### <a name="to-create-the-wizard-model"></a>Per creare il modello della procedura guidata

1. Aprire il file di codice SiteColumnWizardModel e sostituire l'intero contenuto del file con il codice seguente.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb" id="Snippet6":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs" id="Snippet6":::

#### <a name="to-create-the-project-signing-manager"></a>Per creare il gestore della firma del progetto

1. Aprire il file di codice ProjectSigningManager e quindi sostituire l'intero contenuto del file con il codice seguente.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb" id="Snippet8":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs" id="Snippet8":::

## <a name="create-the-wizard-ui"></a>Creare l'interfaccia utente della procedura guidata
 Aggiungere xaml per definire l'interfaccia utente della finestra della procedura guidata e i due controlli utente che forniscono l'interfaccia utente per le pagine della procedura guidata e aggiungere codice per definire il comportamento della finestra e dei controlli utente. La procedura guidata creata è simile alla procedura guidata incorporata per SharePoint progetti in Visual Studio.

> [!NOTE]
> Nei passaggi seguenti il progetto presenterà alcuni errori di compilazione dopo aver aggiunto codice o XAML al progetto. Questi errori verranno visualizzati quando si aggiungerà codice nei passaggi successivi.

#### <a name="to-create-the-wizard-window-ui"></a>Per creare l'interfaccia utente della finestra della procedura guidata

1. Nel progetto ProjectTemplateWizard aprire il menu di scelta rapida per  il file WizardWindow.xaml e quindi scegliere Apri per aprire la finestra nella finestra di progettazione.

2. Nella visualizzazione XAML della finestra di progettazione sostituire il codice XAML corrente con il codice XAML seguente. Il codice XAML definisce un'interfaccia utente che include un'intestazione, un oggetto che contiene le pagine della procedura guidata e i pulsanti di spostamento <xref:System.Windows.Controls.Grid> nella parte inferiore della finestra.

     :::code language="xml" source="../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml" id="Snippet10":::

    > [!NOTE]
    > La finestra creata in questo codice XAML è derivata dalla <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> classe di base . Quando si aggiunge una finestra di dialogo WPF personalizzata a Visual Studio, è consigliabile derivare la finestra di dialogo da questa classe per applicare stili coerenti con altre finestre di dialogo Visual Studio ed evitare problemi di finestra di dialogo modale che altrimenti potrebbero verificarsi. Per altre informazioni, vedere [Creazione e gestione di finestre di dialogo modali.](../extensibility/creating-and-managing-modal-dialog-boxes.md)

3. Se si sta sviluppando un progetto Visual Basic, rimuovere lo spazio dei nomi dal nome della classe `ProjectTemplateWizard` `WizardWindow` `x:Class` nell'attributo `Window` dell'elemento . Questo elemento si trova nella prima riga del codice XAML. Al termine, la prima riga dovrebbe essere simile all'esempio seguente.

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. Aprire il file code-behind per il file WizardWindow.xaml.

5. Sostituire il contenuto di questo file, ad eccezione delle dichiarazioni all'inizio del `using` file, con il codice seguente.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb" id="Snippet4":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs" id="Snippet4":::

#### <a name="to-create-the-first-wizard-page-ui"></a>Per creare l'interfaccia utente della prima pagina della procedura guidata

1. Nel progetto ProjectTemplateWizard aprire il menu di scelta rapida per  il file Page1.xaml e quindi scegliere Apri per aprire il controllo utente nella finestra di progettazione.

2. Nella visualizzazione XAML della finestra di progettazione sostituire il codice XAML corrente con il codice XAML seguente. Il codice XAML definisce un'interfaccia utente che include una casella di testo in cui gli utenti possono immettere l'URL dei siti locali da usare per il debug. L'interfaccia utente include anche pulsanti di opzione con cui gli utenti possono specificare se il progetto è in modalità sandbox.

     :::code language="xml" source="../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml" id="Snippet11":::

3. Se si sviluppa un progetto Visual Basic, rimuovere lo spazio dei nomi dal nome della classe `ProjectTemplateWizard` `Page1` `x:Class` nell'attributo `UserControl` dell'elemento . Si trova nella prima riga del codice XAML. Al termine, la prima riga dovrebbe essere simile alla seguente.

    ```xml
    <UserControl x:Class="Page1"
    ```

4. Sostituire il contenuto del file Page1.xaml, ad eccezione delle dichiarazioni all'inizio del `using` file, con il codice seguente.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs" id="Snippet2":::

#### <a name="to-create-the-second-wizard-page-ui"></a>Per creare l'interfaccia utente della seconda pagina della procedura guidata

1. Nel progetto ProjectTemplateWizard aprire il menu di scelta rapida per il file Page2.xaml e quindi scegliere **Apri.**

     Il controllo utente viene visualizzato nella finestra di progettazione.

2. Nella visualizzazione XAML sostituire il codice XAML corrente con il codice XAML seguente. Il codice XAML definisce un'interfaccia utente che include un elenco a discesa per la scelta del tipo di base della colonna del sito, una casella combinata per specificare un gruppo predefinito o personalizzato in cui visualizzare la colonna del sito nella raccolta e una casella di testo per specificare il nome della colonna del sito.

     :::code language="xml" source="../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml" id="Snippet12":::

3. Se si sviluppa un progetto Visual Basic, rimuovere lo spazio dei nomi dal nome della classe `ProjectTemplateWizard` `Page2` `x:Class` nell'attributo `UserControl` dell'elemento . Si trova nella prima riga del codice XAML. Al termine, la prima riga dovrebbe essere simile alla seguente.

    ```xml
    <UserControl x:Class="Page2"
    ```

4. Sostituire il contenuto del file code-behind per il file Page2.xaml, ad eccezione delle dichiarazioni all'inizio del `using` file, con il codice seguente.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb" id="Snippet3":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs" id="Snippet3":::

## <a name="implement-the-wizard"></a>Implementare la procedura guidata
 Definire la funzionalità principale della procedura guidata implementando <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> l'interfaccia . Questa interfaccia definisce i metodi che Visual Studio chiama all'avvio e al termine della procedura guidata e in determinati momenti durante l'esecuzione della procedura guidata.

#### <a name="to-implement-the-wizard"></a>Per implementare la procedura guidata

1. Nel progetto ProjectTemplateWizard aprire il file di codice SiteColumnProjectWizard.

2. Sostituire l'intero contenuto di questo file con il codice seguente.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb" id="Snippet7":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs" id="Snippet7":::

## <a name="create-the-sharepoint-commands"></a>Creare i SharePoint seguenti
 Creare due comandi personalizzati che chiamano nel modello a oggetti SharePoint server. Un comando determina se l'URL del sito che l'utente digitare nella procedura guidata è valido. L'altro comando ottiene tutti i tipi di campo dal sito SharePoint specificato in modo che gli utenti possano selezionare quello da usare come base per la nuova colonna del sito.

#### <a name="to-define-the-sharepoint-commands"></a>Per definire i SharePoint seguenti

1. Nel progetto **SharePointCommands** aprire il file di codice Commands.

2. Sostituire l'intero contenuto di questo file con il codice seguente.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb" id="Snippet9":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs" id="Snippet9":::

## <a name="checkpoint"></a>Checkpoint
 A questo punto della procedura dettagliata, tutto il codice per la procedura guidata si trova ora nel progetto. Compilare il progetto per assicurarsi che venga compilato senza errori.

#### <a name="to-build-your-project"></a>Per compilare il progetto

1. Nella barra dei menu scegliere **Compila**  >  **compila soluzione.**

## <a name="removing-the-keysnk-file-from-the-project-template"></a>Rimozione del file key.snk dal modello di progetto
 In Procedura dettagliata: Creare un elemento di progetto colonna del sito con un modello di progetto, parte [1,](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)il modello di progetto creato contiene un file key.snk usato per firmare ogni istanza del progetto Colonna del sito. Questo file key.snk non è più necessario perché la procedura guidata ora genera un nuovo file key.snk per ogni progetto. Rimuovere il file key.snk dal modello di progetto e rimuovere i riferimenti a questo file.

#### <a name="to-remove-the-keysnk-file-from-the-project-template"></a>Per rimuovere il file key.snk dal modello di progetto

1. In **Esplora soluzioni**, nel nodo **SiteColumnProjectTemplate** aprire il menu di scelta rapida per il file **key.snk** e quindi scegliere **Elimina.**

2. Nella finestra di dialogo di conferma visualizzata fare clic sul pulsante **OK**.

3. Nel nodo **SiteColumnProjectTemplate** aprire il file SiteColumnProjectTemplate.vstemplate e quindi rimuovere l'elemento seguente.

    ```xml
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
    ```

4. Salvare e chiudere il file.

5. Nel nodo **SiteColumnProjectTemplate** aprire il file ProjectTemplate.csproj o ProjectTemplate.vbproj e quindi rimuovere `PropertyGroup` l'elemento seguente.

    ```xml
    <PropertyGroup>
      <SignAssembly>true</SignAssembly>
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
    </PropertyGroup>
    ```

6. Rimuovere l'elemento `None` seguente.

    ```xml
    <None Include="key.snk" />
    ```

7. Salvare e chiudere il file.

## <a name="associating-the-wizard-with-the-project-template"></a>Associazione della procedura guidata al modello di progetto
 Dopo aver implementato la procedura guidata, è necessario associarla al modello di progetto **Colonna** sito. A tale scopo, è necessario completare tre procedure:

1. Firmare l'assembly della procedura guidata con un nome sicuro.

2. Ottenere il token di chiave pubblica per l'assembly della procedura guidata.

3. Aggiungere un riferimento all'assembly della procedura guidata nel file con estensione vstemplate per il **modello di progetto Colonna** sito.

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Per firmare l'assembly della procedura guidata con un nome sicuro

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il **progetto ProjectTemplateWizard** e quindi scegliere **Proprietà.**

2. Nella scheda **Firma** selezionare la casella di controllo **Firma assembly**.

3. **Nell'elenco Scegliere un file di chiave con nome** sicuro scegliere **\<New...>** .

4. Nella finestra **di dialogo** Crea chiave con nome sicuro immettere un nome per il nuovo file di chiave, deselezionare la casella di controllo Proteggi il file di chiave con **una password** e quindi scegliere il **pulsante OK.**

5. Aprire il menu di scelta rapida **per il progetto ProjectTemplateWizard** e quindi scegliere **Compila** per creare il file ProjectTemplateWizard.dll progetto.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Per ottenere il token di chiave pubblica per l'assembly della procedura guidata

1. Nel **menu Start scegliere** Tutti **i** programmi, **Microsoft Visual Studio**, **Strumenti di Visual Studio** e quindi scegliere **Prompt dei comandi per gli sviluppatori**.

     Verrà Visual Studio finestra del prompt dei comandi.

2. Eseguire il comando seguente, sostituendo *PathToWizardAssembly* con il percorso completo dell'assembly ProjectTemplateWizard.dll compilato per il progetto ProjectTemplateWizard nel computer di sviluppo:

    ```cmd
    sn.exe -T PathToWizardAssembly
    ```

     Il token di chiave pubblica per l'assembly ProjectTemplateWizard.dll viene scritto nella finestra Visual Studio prompt dei comandi.

3. Mantenere aperta Visual Studio prompt dei comandi. Il token di chiave pubblica sarà necessario durante la procedura successiva.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Per aggiungere un riferimento all'assembly della procedura guidata nel file con estensione vstemplate

1. In **Esplora soluzioni** espandere il nodo del progetto **SiteColumnProjectTemplate** e aprire il file SiteColumnProjectTemplate.vstemplate.

2. Alla fine del file aggiungere l'elemento `WizardExtension` seguente tra i tag e `</TemplateContent>` `</VSTemplate>` . Sostituire il *valore del token* `PublicKeyToken` dell'attributo con il token di chiave pubblica ottenuto nella procedura precedente.

    ```xml
    <WizardExtension>
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>
    </WizardExtension>
    ```

     Per altre informazioni `WizardExtension` sull'elemento , vedere Elemento [WizardExtension &#40;Visual Studio Templates&#41;](../extensibility/wizardextension-element-visual-studio-templates.md).

3. Salvare e chiudere il file.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>Aggiungere parametri sostituibili al file Elements.xml nel modello di progetto
 Aggiungere diversi parametri sostituibili al file *Elements.xml* nel progetto SiteColumnProjectTemplate. Questi parametri vengono inizializzati nel `RunStarted` metodo nella classe definita in `SiteColumnProjectWizard` precedenza. Quando un utente crea un progetto Colonna del sito, Visual Studio sostituisce automaticamente questi parametri nel file *Elements.xml* nel nuovo progetto con i valori specificati nella procedura guidata.

 Un parametro sostituibile è un token che inizia e termina con il carattere di dollaro ($). Oltre a definire i propri parametri sostituibili, è possibile usare i parametri predefiniti definiti e inizializzati dal sistema di SharePoint progetto. Per altre informazioni, vedere [Parametri sostituibili.](../sharepoint/replaceable-parameters.md)

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Per aggiungere parametri sostituibili al file Elements.xml

1. Nel progetto SiteColumnProjectTemplate sostituire il contenuto del file *Elements.xml* con il codice XML seguente.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <Field ID="{$guid5$}"
             Name="$fieldname$"
             DisplayName="$fieldname$"
             Type="$selectedfieldtype$"
             Group="$selectedgrouptype$">
      </Field>
    </Elements>
    ```

     Il nuovo codice XML modifica i valori degli `Name` attributi , , e in parametri `DisplayName` `Type` `Group` sostituibili personalizzati.

2. Salvare e chiudere il file.

## <a name="add-the-wizard-to-the-vsix-package"></a>Aggiungere la procedura guidata al pacchetto VSIX
 Per distribuire la procedura guidata con il pacchetto VSIX che contiene il modello di progetto Colonna del sito, aggiungere riferimenti al progetto della procedura guidata e al progetto dei comandi SharePoint al file source.extension.vsixmanifest nel progetto VSIX.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Per aggiungere la procedura guidata al pacchetto VSIX

1. In **Esplora soluzioni**, nel progetto **SiteColumnProjectItem** aprire il menu di scelta rapida per il file **source.extension.vsixmanifest** e quindi scegliere **Apri.**

     Visual Studio apre il file nell'editor manifesto.

2. Nella **scheda Asset dell'editor** scegliere il **pulsante** Nuovo.

     Verrà **visualizzata la finestra di dialogo** Aggiungi nuovo asset.

3. **Nell'elenco Tipo** scegliere **Microsoft.VisualStudio.Assembly**.

4. **Nell'elenco** Origine scegliere **Un progetto nella soluzione corrente.**

5. **Nell'Project** progetto scegliere **ProjectTemplateWizard** e quindi scegliere **il pulsante OK.**

6. Nella **scheda Asset dell'editor** scegliere di nuovo **il pulsante** Nuovo.

     Verrà **visualizzata la finestra di dialogo** Aggiungi nuovo asset.

7. **Nell'elenco** Tipo immettere **SharePoint. Commands.v4**.

8. **Nell'elenco** Origine scegliere **Un progetto nella soluzione corrente.**

9. **Nell'Project** selezionare il progetto **SharePointCommands** e quindi scegliere **il pulsante OK.**

10. Nella barra dei menu scegliere **Compila** soluzione e quindi assicurarsi che la soluzione sia  >  compilata senza errori.

## <a name="test-the-wizard"></a>Testare la procedura guidata
 A questo punto è possibile testare la procedura guidata. Avviare prima di tutto il debug della soluzione SiteColumnProjectItem nell'istanza sperimentale di Visual Studio. Testare quindi la procedura guidata per il progetto Colonna del sito nell'istanza sperimentale di Visual Studio. Infine, compilare ed eseguire il progetto per verificare che la colonna del sito funzioni come previsto.

#### <a name="to-start-debugging-the-solution"></a>Per avviare il debug della soluzione

1. Riavviare Visual Studio con credenziali amministrative e quindi aprire la soluzione SiteColumnProjectItem.

2. Nel progetto ProjectTemplateWizard aprire il file di codice SiteColumnProjectWizard e quindi aggiungere un punto di interruzione alla prima riga di codice nel `RunStarted` metodo .

3. Sulla barra dei menu scegliere **Debug**  >  **Exceptions (Eccezioni di debug).**

4. Nella finestra **di** dialogo Eccezioni  verificare che  le caselle di controllo Generata e Non gestita dall'utente per Eccezioni **Common Language Runtime** siano deselezionate e quindi scegliere il pulsante **OK.**

5. Avviare il debug premendo **F5 oppure,** sulla barra dei menu, **scegliere Debug**  >  **Avvia debug**.

     Visual Studio installa l'estensione in %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Site Column\1.0 e avvia un'istanza sperimentale di Visual Studio. Si testerà l'elemento di progetto in questa istanza di Visual Studio.

#### <a name="to-test-the-wizard-in-visual-studio"></a>Per testare la procedura guidata in Visual Studio

1. Nell'istanza sperimentale di Visual Studio, sulla barra dei menu scegliere **File**  >    >  **Nuovo Project**.

2. Espandere il nodo **Visual C#** o il nodo **Visual Basic (a** seconda del linguaggio che supporta il modello di progetto), espandere il nodo **SharePoint** e quindi scegliere il **nodo 2010.**

3. Nell'elenco dei modelli di progetto scegliere **Colonna** del sito, assegnare al progetto il nome **SiteColumnWizardTest** e quindi scegliere **il pulsante OK.**

4. Verificare che il codice nell'altra istanza di Visual Studio si arresti in corrispondenza del punto di interruzione impostato in precedenza nel `RunStarted` metodo .

5. Continuare a eseguire il debug del progetto premendo **F5** oppure, sulla barra dei menu, scegliere **Debug**  >  **Continua.**

6. Nella **Personalizzazione guidata SharePoint,** immettere l'URL del sito che si vuole usare per il debug e quindi scegliere **il pulsante** Avanti.

7. Nella seconda pagina della **Personalizzazione guidata SharePoint,** effettuare le selezioni seguenti:

   - **Nell'elenco Tipo** scegliere **Boolean**.

   - **Nell'elenco** Gruppo scegliere **Colonne sì/no personalizzate.**

   - Nella casella **Nome** immettere **My Yes/No Column (Colonna Sì/No)** e quindi scegliere il pulsante Finish **(Fine).**

     In **Esplora soluzioni** viene visualizzato un nuovo progetto che contiene un elemento di progetto denominato **Field1** e Visual Studio apre il file *Elements.xml* del progetto nell'editor.

8. Verificare che *Elements.xml* contenga i valori specificati nella procedura guidata.

#### <a name="to-test-the-site-column-in-sharepoint"></a>Per testare la colonna del sito in SharePoint

1. Nell'istanza sperimentale Visual Studio premere **F5.**

     La colonna del sito viene in pacchetto e distribuita nel sito SharePoint specificato dalla proprietà **URL** sito del progetto. Il Web browser apre la pagina predefinita di questo sito.

    > [!NOTE]
    > Se viene **visualizzata la finestra di** dialogo Debug script disabilitato , scegliere il **pulsante** Sì per continuare il debug del progetto.

2. Nel menu **Azioni sito** scegliere **Site Impostazioni**.

3. Nella pagina Impostazioni sito in **Raccolte** scegliere il **collegamento Colonne del** sito.

4. Nell'elenco delle colonne del sito verificare che un gruppo Colonne **Sì/No** personalizzato contenga una colonna denominata My **Yes/No Column** e quindi chiudere il Web browser.

## <a name="clean-up-the-development-computer"></a>Pulire il computer di sviluppo
 Dopo aver completato il test dell'elemento di progetto, rimuovere il modello di progetto dall'istanza sperimentale di Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Per pulire il computer di sviluppo

1. Nell'istanza sperimentale di Visual Studio, sulla barra dei menu scegliere **Strumenti**  >  **Estensioni e aggiornamenti**.

     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

2. Nell'elenco delle estensioni scegliere **Colonna sito** e quindi fare clic **sul pulsante** Disinstalla.

3. Nella finestra di dialogo visualizzata  scegliere il pulsante Sì per confermare che si vuole disinstallare l'estensione e quindi scegliere il pulsante Riavvia **ora** per completare la disinstallazione.

4. Chiudere sia l'istanza sperimentale Visual Studio che l'istanza in cui è aperta la soluzione CustomActionProjectItem.

     Per informazioni su come distribuire le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] estensioni, vedere [Shipping Visual Studio Extensions.](../extensibility/shipping-visual-studio-extensions.md)

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: Creare un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Definire tipi di SharePoint di progetto personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Creazione di modelli di elemento e di modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Procedura: utilizzare procedure guidate con modelli di progetto](../extensibility/how-to-use-wizards-with-project-templates.md)
