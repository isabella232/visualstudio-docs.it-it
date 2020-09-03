---
title: Creare un elemento di progetto colonna del sito con il modello di progetto, parte 2
ms.date: 02/02/2017
ms.topic: how-to
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c3b84d901a1fd94d72ff14ec5c481e04676c5cbc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016405"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-2"></a>Procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 2
  Dopo aver definito un tipo personalizzato di elemento di progetto SharePoint e averlo associato a un modello di progetto in Visual Studio, potrebbe essere necessario anche fornire una procedura guidata per il modello. È possibile utilizzare la procedura guidata per raccogliere informazioni dagli utenti quando utilizzano il modello per creare un nuovo progetto che contiene l'elemento del progetto. Le informazioni raccolte possono essere utilizzate per inizializzare l'elemento del progetto.

 In questa procedura dettagliata verrà aggiunta una procedura guidata al modello di progetto colonna del sito illustrato in [procedura dettagliata: creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md). Quando un utente crea un progetto di colonna del sito, la procedura guidata raccoglie informazioni sulla colonna del sito, ad esempio il tipo e il gruppo di base, e aggiunge tali informazioni al file *Elements.xml* nel nuovo progetto.

 In questa procedura dettagliata vengono descritte le attività seguenti:

- Creazione di una procedura guidata per un tipo di elemento di progetto SharePoint personalizzato associato a un modello di progetto.

- Definizione di un'interfaccia utente personalizzata della procedura guidata simile alle procedure guidate predefinite per i progetti SharePoint in Visual Studio.

- Creazione di due *comandi di SharePoint* utilizzati per chiamare il sito di SharePoint locale mentre è in esecuzione la procedura guidata. I comandi di SharePoint sono metodi che possono essere usati dalle estensioni di Visual Studio per chiamare le API nel modello a oggetti del server SharePoint. Per ulteriori informazioni, vedere [chiamata ai modelli a oggetti di SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

- Utilizzo di parametri sostituibili per inizializzare i file di progetto SharePoint con i dati raccolti nella procedura guidata.

- Creazione di un nuovo file con estensione snk in ogni nuova istanza del progetto di colonna del sito. Questo file viene usato per firmare l'output del progetto in modo che l'assembly della soluzione SharePoint possa essere distribuito nel Global Assembly Cache.

- Debug e test della procedura guidata.

> [!NOTE]
> Per una serie di flussi di lavoro di esempio, vedere [esempi di flussi di lavoro di SharePoint](/sharepoint/dev/general-development/sharepoint-workflow-samples).

## <a name="prerequisites"></a>Prerequisiti
 Per eseguire questa procedura dettagliata, è necessario innanzitutto creare la soluzione SiteColumnProjectItem completando [procedura dettagliata: creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).

 Per completare questa procedura dettagliata, è inoltre necessario che nel computer di sviluppo siano presenti i componenti seguenti:

- Edizioni supportate di Windows, SharePoint e Visual Studio.

- Visual Studio SDK. Questa procedura dettagliata usa il modello di **progetto VSIX** nell'SDK per creare un pacchetto VSIX per distribuire l'elemento di progetto. Per altre informazioni, vedere [estendere gli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Per completare la procedura dettagliata, è necessario conoscere i concetti seguenti:

- Procedure guidate per i modelli di progetto e di elemento in Visual Studio. Per altre informazioni, vedere [procedura: usare procedure guidate con modelli di progetto](../extensibility/how-to-use-wizards-with-project-templates.md) e l' <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaccia.

- Colonne del sito in SharePoint. Per ulteriori informazioni, vedere [colonne](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

## <a name="understand-the-wizard-components"></a>Informazioni sui componenti della procedura guidata
 La procedura guidata illustrata in questa procedura dettagliata contiene diversi componenti. Nella tabella seguente vengono descritti questi componenti.

|Componente|Descrizione|
|---------------|-----------------|
|Implementazione della procedura guidata|Si tratta di una classe, denominata `SiteColumnProjectWizard` , che implementa l' <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaccia. Questa interfaccia definisce i metodi chiamati da Visual Studio all'avvio e al termine della procedura guidata e in determinati orari durante l'esecuzione della procedura guidata.|
|Interfaccia utente della procedura guidata|Si tratta di una finestra basata su WPF, denominata `WizardWindow` . Questa finestra include due controlli utente, denominati `Page1` e `Page2` . Questi controlli utente rappresentano le due pagine della procedura guidata.<br /><br /> In questa procedura dettagliata, il <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> metodo dell'implementazione della procedura guidata Visualizza l'interfaccia utente della procedura guidata.|
|Modello di dati della procedura guidata|Si tratta di una classe intermedia, denominata `SiteColumnWizardModel` , che fornisce un livello tra l'interfaccia utente della procedura guidata e l'implementazione della procedura guidata. Questo esempio usa questa classe per astrarre l'implementazione della procedura guidata e l'interfaccia utente della procedura guidata. Questa classe non è un componente obbligatorio di tutte le procedure guidate.<br /><br /> In questa procedura dettagliata, l'implementazione della procedura guidata passa un `SiteColumnWizardModel` oggetto alla finestra della procedura guidata quando viene visualizzata l'interfaccia utente della procedura guidata. L'interfaccia utente della procedura guidata usa i metodi di questo oggetto per salvare i valori dei controlli nell'interfaccia utente e per eseguire attività come la verifica della validità dell'URL del sito di input. Dopo che l'utente ha completato la procedura guidata, l'implementazione della procedura guidata usa l' `SiteColumnWizardModel` oggetto per determinare lo stato finale dell'interfaccia utente.|
|Gestione firma progetto|Si tratta di una classe helper, denominata `ProjectSigningManager` , che viene usata dall'implementazione della procedura guidata per creare un nuovo file Key. snk in ogni nuova istanza del progetto.|
|SharePoint (comandi)|Si tratta di metodi utilizzati dal modello di dati della procedura guidata per effettuare chiamate nel sito di SharePoint locale mentre la procedura guidata è in esecuzione. Poiché i comandi di SharePoint devono essere destinati alla .NET Framework 3,5, questi comandi vengono implementati in un assembly diverso rispetto al resto del codice della procedura guidata.|

## <a name="create-the-projects"></a>Creare i progetti
 Per completare questa procedura dettagliata, è necessario aggiungere diversi progetti alla soluzione SiteColumnProjectItem creata in [procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md):

- Un progetto WPF. L'interfaccia verrà implementata <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> e verrà definita l'interfaccia utente della procedura guidata in questo progetto.

- Progetto di libreria di classi che definisce i comandi di SharePoint. Questo progetto deve avere come destinazione the.NET Framework 3,5.

  Avviare la procedura dettagliata creando i progetti.

#### <a name="to-create-the-wpf-project"></a>Per creare il progetto WPF

1. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aprire la soluzione SiteColumnProjectItem.

2. In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo della soluzione **SiteColumnProjectItem** , scegliere **Aggiungi**, quindi **nuovo progetto**.

3. Nella parte superiore della finestra di dialogo **Aggiungi nuovo progetto** verificare che **.NET Framework 4,5** sia selezionato nell'elenco delle versioni del .NET Framework.

4. Espandere il nodo **Visual C#** o il nodo **Visual Basic** e scegliere il nodo **Windows** .

5. Nell'elenco dei modelli di progetto scegliere **libreria di controlli utente WPF**, denominare il progetto **ProjectTemplateWizard**, quindi scegliere il pulsante **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **ProjectTemplateWizard** alla soluzione e apre il file UserControl1. XAML predefinito.

6. Eliminare il file UserControl1. XAML dal progetto.

#### <a name="to-create-the-sharepoint-commands-project"></a>Per creare il progetto di comandi di SharePoint

1. In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo della soluzione SiteColumnProjectItem, scegliere **Aggiungi**, quindi **nuovo progetto**.

2. Nella parte superiore della finestra di dialogo **Aggiungi nuovo progetto** scegliere **.NET Framework 3,5** nell'elenco delle versioni del .NET Framework.

3. Espandere il nodo **Visual C#** o il nodo  **Visual Basic** , quindi scegliere il nodo **Windows** .

4. Scegliere il modello di progetto **libreria di classi** , denominare il progetto **SharePointCommands**, quindi scegliere il pulsante **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **SharePointCommands** alla soluzione e apre il file di codice Class1 predefinito.

5. Eliminare il file di codice Class1 dal progetto.

## <a name="configure-the-projects"></a>Configurare i progetti
 Prima di creare la procedura guidata, è necessario aggiungere alcuni file di codice e riferimenti ad assembly ai progetti.

#### <a name="to-configure-the-wizard-project"></a>Per configurare il progetto della procedura guidata

1. In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo del progetto **ProjectTemplateWizard** , quindi scegliere **proprietà**.

2. In creazione **progetti**scegliere la scheda **applicazione** per un progetto Visual C# o la scheda **Compila** per un progetto Visual Basic.

3. Verificare che il Framework di destinazione sia impostato sul .NET Framework 4,5, non sul profilo client .NET Framework 4,5.

     Per altre informazioni, vedere [How to: target a version of the .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

4. Aprire il menu di scelta rapida per il progetto **ProjectTemplateWizard** , scegliere **Aggiungi**, quindi scegliere **nuovo elemento**.

5. Scegliere la voce **finestra (WPF)** , denominare l'elemento **WizardWindow**, quindi scegliere il pulsante **Aggiungi** .

6. Aggiungere due elementi del **controllo utente (WPF)** al progetto e denominarli **Pagina1** e **pagina2**.

7. Aggiungere quattro file di codice al progetto e assegnare loro i nomi seguenti:

    - SiteColumnProjectWizard

    - SiteColumnWizardModel

    - ProjectSigningManager

    - CommandIds

8. Aprire il menu di scelta rapida per il nodo del progetto **ProjectTemplateWizard** , quindi scegliere **Aggiungi riferimento**.

9. Espandere il nodo **assembly** , scegliere il nodo **estensioni** , quindi selezionare le caselle di controllo accanto agli assembly seguenti:

    - EnvDTE

    - Microsoft. VisualStudio. OLE. Interop

    - Microsoft. VisualStudio. SharePoint

    - Microsoft. VisualStudio. Shell. 11.0

    - Microsoft. VisualStudio. Shell. Interop. 10.0

    - Microsoft. VisualStudio. Shell. Interop. 11.0

    - Microsoft.VisualStudio.TemplateWizardInterface

10. Scegliere il pulsante **OK** per aggiungere gli assembly al progetto.

11. In **Esplora soluzioni**, nella cartella **riferimenti** per il progetto **ProjectTemplateWizard** , scegliere **EnvDTE**.

12. Nella finestra **Proprietà** modificare il valore della proprietà **Incorpora tipi di interoperabilità** su **false**.

13. Se si sta sviluppando un progetto di Visual Basic, importare lo spazio dei nomi ProjectTemplateWizard nel progetto usando **Progettazione progetti**.

     Per altre informazioni, vedere [procedura: aggiungere o rimuovere spazi dei nomi Importati &#40;Visual Basic&#41;](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md).

#### <a name="to-configure-the-sharepointcommands-project"></a>Per configurare il progetto SharePointcommands

1. In **Esplora soluzioni**scegliere il nodo del progetto **SharePointCommands** .

2. Sulla barra dei menu scegliere **progetto**,  **Aggiungi elemento esistente**.

3. Nella finestra di dialogo **Aggiungi elemento esistente** passare alla cartella che contiene i file di codice per il progetto ProjectTemplateWizard, quindi scegliere il file di codice **CommandIds** .

4. Scegliere la freccia accanto al pulsante **Aggiungi** , quindi scegliere l'opzione **Aggiungi come collegamento** nel menu visualizzato.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il file di codice al progetto **SharePointCommands** come collegamento. Il file di codice si trova nel progetto **ProjectTemplateWizard** , ma anche il codice nel file viene compilato nel progetto **SharePointCommands** .

5. Nel progetto **SharePointCommands** aggiungere un altro file di codice denominato Commands.

6. Scegliere il progetto SharePointCommands, quindi nella barra dei menu scegliere **progetto**  >  **Aggiungi riferimento**.

7. Espandere il nodo **assembly** , scegliere il nodo **estensioni** , quindi selezionare le caselle di controllo accanto agli assembly seguenti:

    - Microsoft. SharePoint

    - Microsoft. VisualStudio. SharePoint. Commands

8. Scegliere il pulsante **OK** per aggiungere gli assembly al progetto.

## <a name="create-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>Creare il modello di procedura guidata, il gestore della firma e gli ID dei comandi di SharePoint
 Aggiungere il codice al progetto ProjectTemplateWizard per implementare i componenti seguenti nell'esempio:

- ID dei comandi di SharePoint. Queste stringhe identificano i comandi di SharePoint utilizzati dalla procedura guidata. Più avanti in questa procedura dettagliata verrà aggiunto il codice al progetto SharePointCommands per implementare i comandi.

- Modello di dati della procedura guidata.

- Gestione firma progetto.

  Per ulteriori informazioni su questi componenti, vedere [comprendere i componenti della procedura guidata](#understand-the-wizard-components).

#### <a name="to-define-the-sharepoint-command-ids"></a>Per definire gli ID dei comandi di SharePoint

1. Nel progetto ProjectTemplateWizard aprire il file di codice CommandIds e sostituire l'intero contenuto del file con il codice seguente.

     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb#5)]

#### <a name="to-create-the-wizard-model"></a>Per creare il modello di procedura guidata

1. Aprire il file di codice SiteColumnWizardModel e sostituire l'intero contenuto del file con il codice seguente.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]

#### <a name="to-create-the-project-signing-manager"></a>Per creare il gestore della firma del progetto

1. Aprire il file di codice ProjectSigningManager, quindi sostituire l'intero contenuto del file con il codice seguente.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb#8)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs#8)]

## <a name="create-the-wizard-ui"></a>Creazione dell'interfaccia utente della procedura guidata
 Aggiungere XAML per definire l'interfaccia utente della finestra della procedura guidata e i due controlli utente che forniscono l'interfaccia utente per le pagine della procedura guidata e aggiungere il codice per definire il comportamento della finestra e dei controlli utente. La procedura guidata creata è simile alla procedura guidata incorporata per i progetti SharePoint in Visual Studio.

> [!NOTE]
> Nei passaggi seguenti il progetto avrà alcuni errori di compilazione dopo l'aggiunta del codice XAML o del codice al progetto. Questi errori si verificano quando si aggiunge codice nei passaggi successivi.

#### <a name="to-create-the-wizard-window-ui"></a>Per creare l'interfaccia utente della finestra della procedura guidata

1. Nel progetto ProjectTemplateWizard aprire il menu di scelta rapida per il file WizardWindow. XAML, quindi scegliere **Apri** per aprire la finestra nella finestra di progettazione.

2. Nella visualizzazione XAML della finestra di progettazione sostituire il codice XAML corrente con il codice XAML seguente. Il codice XAML definisce un'interfaccia utente che include un'intestazione, un oggetto <xref:System.Windows.Controls.Grid> che contiene le pagine della procedura guidata e i pulsanti di spostamento nella parte inferiore della finestra.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml#10)]

    > [!NOTE]
    > La finestra creata in questo codice XAML è derivata dalla <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> classe base. Quando si aggiunge una finestra di dialogo WPF personalizzata a Visual Studio, è consigliabile derivare la finestra di dialogo da questa classe per ottenere uno stile coerente con altre finestre di dialogo di Visual Studio ed evitare problemi di finestra di dialogo modale che potrebbero altrimenti verificarsi. Per ulteriori informazioni, vedere [creazione e gestione di finestre di dialogo modali](../extensibility/creating-and-managing-modal-dialog-boxes.md).

3. Se si sta sviluppando un progetto di Visual Basic, rimuovere lo `ProjectTemplateWizard` spazio dei nomi dal `WizardWindow` nome della classe nell' `x:Class` attributo dell' `Window` elemento. Questo elemento si trova nella prima riga del codice XAML. Al termine, la prima riga dovrebbe essere simile all'esempio seguente.

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. Aprire il file code-behind per il file WizardWindow. XAML.

5. Sostituire il contenuto di questo file, ad eccezione delle `using` dichiarazioni all'inizio del file, con il codice seguente.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb#4)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs#4)]

#### <a name="to-create-the-first-wizard-page-ui"></a>Per creare la prima interfaccia utente della pagina della procedura guidata

1. Nel progetto ProjectTemplateWizard aprire il menu di scelta rapida per il file Pagina1. XAML, quindi scegliere **Apri** per aprire il controllo utente nella finestra di progettazione.

2. Nella visualizzazione XAML della finestra di progettazione sostituire il codice XAML corrente con il codice XAML seguente. Il codice XAML definisce un'interfaccia utente che include una casella di testo in cui gli utenti possono immettere l'URL dei siti locali che desiderano utilizzare per il debug. L'interfaccia utente include anche pulsanti di opzione con cui gli utenti possono specificare se il progetto è in modalità sandbox.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml#11)]

3. Se si sta sviluppando un progetto di Visual Basic, rimuovere lo `ProjectTemplateWizard` spazio dei nomi dal `Page1` nome della classe nell' `x:Class` attributo dell' `UserControl` elemento. Si trova nella prima riga del codice XAML. Al termine, la prima riga avrà un aspetto simile al seguente.

    ```xml
    <UserControl x:Class="Page1"
    ```

4. Sostituire il contenuto del file Pagina1. XAML, ad eccezione delle `using` dichiarazioni all'inizio del file, con il codice seguente.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs#2)]

#### <a name="to-create-the-second-wizard-page-ui"></a>Per creare la seconda interfaccia utente della pagina della procedura guidata

1. Nel progetto ProjectTemplateWizard aprire il menu di scelta rapida per il file Pagina2. XAML, quindi scegliere **Apri**.

     Il controllo utente viene visualizzato nella finestra di progettazione.

2. Nella visualizzazione XAML sostituire il codice XAML corrente con il codice XAML seguente. Il codice XAML definisce un'interfaccia utente che include un elenco a discesa per la scelta del tipo di base della colonna del sito, una casella combinata per specificare un gruppo predefinito o personalizzato in cui visualizzare la colonna del sito nella raccolta e una casella di testo per specificare il nome della colonna del sito.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml#12)]

3. Se si sta sviluppando un progetto di Visual Basic, rimuovere lo `ProjectTemplateWizard` spazio dei nomi dal `Page2` nome della classe nell' `x:Class` attributo dell' `UserControl` elemento. Si trova nella prima riga del codice XAML. Al termine, la prima riga avrà un aspetto simile al seguente.

    ```xml
    <UserControl x:Class="Page2"
    ```

4. Sostituire il contenuto del file code-behind per il file Pagina2. XAML, ad eccezione delle `using` dichiarazioni all'inizio del file, con il codice seguente.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb#3)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs#3)]

## <a name="implement-the-wizard"></a>Implementare la procedura guidata
 Definire la funzionalità principale della procedura guidata implementando l' <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaccia. Questa interfaccia definisce i metodi chiamati da Visual Studio all'avvio e al termine della procedura guidata e in determinati orari durante l'esecuzione della procedura guidata.

#### <a name="to-implement-the-wizard"></a>Per implementare la procedura guidata

1. Nel progetto ProjectTemplateWizard aprire il file di codice SiteColumnProjectWizard.

2. Sostituire l'intero contenuto del file con il codice seguente.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]

## <a name="create-the-sharepoint-commands"></a>Creare i comandi di SharePoint
 Creare due comandi personalizzati che effettuano chiamate nel modello a oggetti del server SharePoint. Un comando determina se l'URL del sito che l'utente digita nella procedura guidata è valido. L'altro comando ottiene tutti i tipi di campo dal sito di SharePoint specificato, in modo che gli utenti possano selezionare quello da utilizzare come base per la nuova colonna del sito.

#### <a name="to-define-the-sharepoint-commands"></a>Per definire i comandi di SharePoint

1. Nel progetto **SharePointCommands** aprire il file di codice dei comandi.

2. Sostituire l'intero contenuto del file con il codice seguente.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb#9)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs#9)]

## <a name="checkpoint"></a>Checkpoint
 A questo punto della procedura dettagliata, tutto il codice per la procedura guidata è ora presente nel progetto. Compilare il progetto per assicurarsi che venga compilato senza errori.

#### <a name="to-build-your-project"></a>Per compilare il progetto

1. Sulla barra dei menu scegliere **Compila**  >  **Compila soluzione**.

## <a name="removing-the-keysnk-file-from-the-project-template"></a>Rimozione del file Key. snk dal modello di progetto
 In [procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md), il modello di progetto creato contiene un file Key. snk usato per firmare ogni istanza del progetto di colonna del sito. Questo file Key. snk non è più necessario perché la procedura guidata genera ora un nuovo file Key. snk per ogni progetto. Rimuovere il file Key. snk dal modello di progetto e rimuovere i riferimenti a questo file.

#### <a name="to-remove-the-keysnk-file-from-the-project-template"></a>Per rimuovere il file Key. snk dal modello di progetto

1. In **Esplora soluzioni**, nel nodo **SiteColumnProjectTemplate** aprire il menu di scelta rapida per il file **Key. snk** , quindi scegliere **Elimina**.

2. Nella finestra di dialogo di conferma visualizzata fare clic sul pulsante **OK**.

3. Nel nodo **SiteColumnProjectTemplate** aprire il file SiteColumnProjectTemplate. vstemplate, quindi rimuovere l'elemento seguente.

    ```xml
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
    ```

4. Salvare e chiudere il file.

5. Nel nodo **SiteColumnProjectTemplate** aprire il file ProjectTemplate. csproj o ProjectTemplate. vbproj, quindi rimuovere l' `PropertyGroup` elemento seguente.

    ```xml
    <PropertyGroup>
      <SignAssembly>true</SignAssembly>
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
    </PropertyGroup>
    ```

6. Rimuovere l' `None` elemento seguente.

    ```xml
    <None Include="key.snk" />
    ```

7. Salvare e chiudere il file.

## <a name="associating-the-wizard-with-the-project-template"></a>Associazione della procedura guidata al modello di progetto
 Ora che è stata implementata la procedura guidata, è necessario associare la procedura guidata al modello di progetto **colonna del sito** . Per eseguire questa operazione, è necessario completare tre procedure:

1. Firmare l'assembly della procedura guidata con un nome sicuro.

2. Ottenere il token di chiave pubblica per l'assembly della procedura guidata.

3. Aggiungere un riferimento all'assembly della procedura guidata nel file con estensione vstemplate per il modello di progetto della **colonna del sito** .

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Per firmare l'assembly della procedura guidata con un nome sicuro

1. In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto **ProjectTemplateWizard** , quindi scegliere **proprietà**.

2. Nella scheda **Firma** selezionare la casella di controllo **Firma assembly**.

3. Nell'elenco **Scegli un file chiave con nome sicuro** scegliere **\<New...>** .

4. Nella finestra di dialogo **Crea chiave con nome sicuro** immettere un nome per il nuovo file di chiave, deselezionare la casella di controllo **Proteggi file di chiave con una password** , quindi scegliere il pulsante **OK** .

5. Aprire il menu di scelta rapida per il progetto **ProjectTemplateWizard** , quindi scegliere **Compila** per creare il file di ProjectTemplateWizard.dll.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Per ottenere il token di chiave pubblica per l'assembly della procedura guidata

1. Dal **menu Start**scegliere **tutti i programmi**, fare clic **su Microsoft Visual Studio**, scegliere **strumenti di Visual Studio**, quindi scegliere **prompt dei comandi per gli sviluppatori**.

     Viene visualizzata una finestra del prompt dei comandi di Visual Studio.

2. Eseguire il comando seguente, sostituendo *PathToWizardAssembly* con il percorso completo dell'assembly ProjectTemplateWizard.dll compilato per il progetto ProjectTemplateWizard nel computer di sviluppo:

    ```cmd
    sn.exe -T PathToWizardAssembly
    ```

     Il token di chiave pubblica per l'assembly ProjectTemplateWizard.dll viene scritto nella finestra del prompt dei comandi di Visual Studio.

3. Lasciare aperta la finestra del prompt dei comandi di Visual Studio. Nel corso della procedura successiva sarà necessario il token di chiave pubblica.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Per aggiungere un riferimento all'assembly della procedura guidata nel file con estensione vstemplate

1. In **Esplora soluzioni**espandere il nodo del progetto **SiteColumnProjectTemplate** e aprire il file SiteColumnProjectTemplate. vstemplate.

2. In prossimità della fine del file, aggiungere l' `WizardExtension` elemento seguente tra i `</TemplateContent>` `</VSTemplate>` tag e. Sostituire il valore del *token* dell' `PublicKeyToken` attributo con il token di chiave pubblica ottenuto nella procedura precedente.

    ```xml
    <WizardExtension>
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>
    </WizardExtension>
    ```

     Per altre informazioni sull' `WizardExtension` elemento, vedere [elemento WizardExtension &#40;modelli di Visual Studio&#41;](../extensibility/wizardextension-element-visual-studio-templates.md).

3. Salvare e chiudere il file.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>Aggiungere parametri sostituibili al file di Elements.xml nel modello di progetto
 Aggiungere diversi parametri sostituibili al file *Elements.xml* nel progetto SiteColumnProjectTemplate. Questi parametri vengono inizializzati nel `RunStarted` metodo nella `SiteColumnProjectWizard` classe definita in precedenza. Quando un utente crea un progetto di colonna del sito, Visual Studio sostituisce automaticamente questi parametri nel file *Elements.xml* nel nuovo progetto con i valori specificati nella procedura guidata.

 Un parametro sostituibile è un token che inizia e termina con il segno di dollaro ($). Oltre a definire i propri parametri sostituibili, è possibile utilizzare parametri predefiniti definiti e inizializzati dal sistema del progetto SharePoint. Per ulteriori informazioni, vedere [parametri sostituibili](../sharepoint/replaceable-parameters.md).

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Per aggiungere parametri sostituibili al file di Elements.xml

1. Nel progetto SiteColumnProjectTemplate sostituire il contenuto del file di *Elements.xml* con il codice XML seguente.

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

     Il nuovo XML modifica i valori degli `Name` attributi, `DisplayName` , `Type` e `Group` in parametri sostituibili personalizzati.

2. Salvare e chiudere il file.

## <a name="add-the-wizard-to-the-vsix-package"></a>Aggiungere la procedura guidata al pacchetto VSIX
 Per distribuire la procedura guidata con il pacchetto VSIX che contiene il modello di progetto colonna del sito, aggiungere i riferimenti al progetto della procedura guidata e al progetto di comandi di SharePoint al file source. Extension. vsixmanifest nel progetto VSIX.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Per aggiungere la procedura guidata al pacchetto VSIX

1. In **Esplora soluzioni**, nel progetto **SiteColumnProjectItem** , aprire il menu di scelta rapida per il file **source. Extension. vsixmanifest** , quindi scegliere **Apri**.

     Visual Studio apre il file nell'editor manifesto.

2. Nella scheda **Asset** dell'Editor scegliere il pulsante **nuovo** .

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo asset** .

3. Nell'elenco **tipo** scegliere **Microsoft. VisualStudio. assembly**.

4. Nell'elenco **origine** scegliere **un progetto nella soluzione corrente**.

5. Nell'elenco **progetto** scegliere **ProjectTemplateWizard**, quindi scegliere il pulsante **OK** .

6. Nella scheda **Asset** dell'Editor scegliere di nuovo il pulsante **nuovo** .

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo asset** .

7. Nell'elenco **tipo** immettere **SharePoint. Commands. v4**.

8. Nell'elenco **origine** scegliere **un progetto nella soluzione corrente**.

9. Nell'elenco **progetto** scegliere il progetto **SharePointCommands** , quindi scegliere il pulsante **OK** .

10. Sulla barra dei menu scegliere **Compila**  >  **Compila soluzione**, quindi assicurarsi che la soluzione venga compilata senza errori.

## <a name="test-the-wizard"></a>Testare la procedura guidata
 A questo punto si è pronti per testare la procedura guidata. Innanzitutto, avviare il debug della soluzione SiteColumnProjectItem nell'istanza sperimentale di Visual Studio. Testare quindi la procedura guidata per il progetto di colonna del sito nell'istanza sperimentale di Visual Studio. Infine, compilare ed eseguire il progetto per verificare che la colonna del sito funzioni come previsto.

#### <a name="to-start-debugging-the-solution"></a>Per avviare il debug della soluzione

1. Riavviare Visual Studio con credenziali amministrative, quindi aprire la soluzione SiteColumnProjectItem.

2. Nel progetto ProjectTemplateWizard aprire il file di codice SiteColumnProjectWizard e quindi aggiungere un punto di interruzione alla prima riga di codice nel `RunStarted` metodo.

3. Nella barra dei menu scegliere **debug**  >  **eccezioni**.

4. Nella finestra di dialogo **eccezioni** assicurarsi che le caselle di controllo **generate** e non **gestite dall'utente** per le **eccezioni Common Language Runtime** siano deselezionate, quindi scegliere il pulsante **OK** .

5. Per avviare il debug, premere il tasto **F5** oppure scegliere **debug**  >  **Avvia debug**sulla barra dei menu.

     Visual Studio installa l'estensione in%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Site Column\1.0 e avvia un'istanza sperimentale di Visual Studio. Si eseguirà il test dell'elemento del progetto in questa istanza di Visual Studio.

#### <a name="to-test-the-wizard-in-visual-studio"></a>Per testare la procedura guidata in Visual Studio

1. Nella barra dei menu dell'istanza sperimentale di Visual Studio scegliere **file**  >  **nuovo**  >  **progetto**.

2. Espandere il nodo **Visual C#** o il nodo **Visual Basic** (a seconda della lingua supportata dal modello di progetto), espandere il nodo **SharePoint** , quindi scegliere il nodo **2010** .

3. Nell'elenco dei modelli di progetto scegliere **colonna sito**, denominare il progetto **SiteColumnWizardTest**, quindi scegliere il pulsante **OK** .

4. Verificare che il codice nell'altra istanza di Visual Studio si arresti in base al punto di interruzione impostato in precedenza nel `RunStarted` metodo.

5. Continuare a eseguire il debug del progetto scegliendo il tasto **F5** oppure, sulla barra dei menu, scegliere **debug**  >  **continua**.

6. Nella **procedura guidata di personalizzazione di SharePoint**, immettere l'URL del sito che si desidera utilizzare per il debug, quindi scegliere il pulsante **Avanti** .

7. Nella seconda pagina della **procedura guidata di personalizzazione di SharePoint**effettuare le selezioni seguenti:

   - Nell'elenco **tipo** scegliere **Boolean**.

   - Nell'elenco **gruppo** scegliere **Custom Yes/No Columns**.

   - Nella casella **nome** immettere la **colonna Yes/No**, quindi scegliere il pulsante **fine** .

     In **Esplora soluzioni**viene visualizzato un nuovo progetto che contiene un elemento di progetto denominato **Field1**e Visual Studio apre il file di *Elements.xml* del progetto nell'editor.

8. Verificare che *Elements.xml* contenga i valori specificati nella procedura guidata.

#### <a name="to-test-the-site-column-in-sharepoint"></a>Per testare la colonna del sito in SharePoint

1. Nell'istanza sperimentale di Visual Studio premere il tasto **F5** .

     La colonna del sito viene assemblata e distribuita nel sito di SharePoint specificato dalla proprietà **URL sito** del progetto. Il Web browser si apre alla pagina predefinita del sito.

    > [!NOTE]
    > Se viene visualizzata la finestra di dialogo **debug script disabilitato** , scegliere il pulsante **Sì** per continuare a eseguire il debug del progetto.

2. Scegliere **Impostazioni sito**dal menu **Azioni sito** .

3. Nella pagina Impostazioni sito, in **raccolte**, scegliere il collegamento **colonne sito** .

4. Nell'elenco delle colonne del sito verificare che un gruppo di **colonne Yes/No personalizzato** contenga una colonna denominata **My Yes/No Column**, quindi chiudere il Web browser.

## <a name="clean-up-the-development-computer"></a>Pulire il computer di sviluppo
 Al termine del test dell'elemento del progetto, rimuovere il modello di progetto dall'istanza sperimentale di Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Per pulire il computer di sviluppo

1. Nella barra dei menu dell'istanza sperimentale di Visual Studio scegliere **strumenti**  >  **estensioni e aggiornamenti**.

     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.

2. Nell'elenco di estensioni scegliere **colonna sito**, quindi scegliere il pulsante **Disinstalla** .

3. Nella finestra di dialogo visualizzata scegliere il pulsante **Sì** per confermare che si desidera disinstallare l'estensione, quindi scegliere il pulsante **Riavvia ora** per completare la disinstallazione.

4. Chiudere l'istanza sperimentale di Visual Studio e l'istanza in cui è aperta la soluzione CustomActionProjectItem.

     Per informazioni su come distribuire le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] estensioni, vedere [spedizione di estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Definire i tipi di elementi di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Creazione di modelli di elemento e di modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Procedura: utilizzare procedure guidate con modelli di progetto](../extensibility/how-to-use-wizards-with-project-templates.md)
