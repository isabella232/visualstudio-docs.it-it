---
title: 'Procedura dettagliata: Creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 2 | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d4512dc15d394cdf2442d8bfcf440ccb31623a29
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942075"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-2"></a>Procedura dettagliata: Creare un elemento di progetto colonna del sito con un modello di progetto, parte 2
  Dopo aver definito un tipo di elemento di progetto SharePoint personalizzato e associarlo a un modello di progetto in Visual Studio, potrebbe anche voler fornire una procedura guidata per il modello. È possibile utilizzare la procedura guidata per raccogliere informazioni dagli utenti quando usano il modello per creare un nuovo progetto che contiene l'elemento del progetto. Le informazioni raccolte sono utilizzabile per inizializzare l'elemento del progetto.  
  
 In questa procedura dettagliata si aggiungerà una procedura guidata per il modello di progetto colonna del sito che è illustrato nel [procedura dettagliata: creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md). Quando un utente crea un progetto colonna del sito, la procedura guidata raccoglie le informazioni relative alla colonna di sito (ad esempio il tipo di base e gruppo) e aggiunge queste informazioni per il *Elements* file nel nuovo progetto.  
  
 In questa procedura dettagliata vengono descritte le attività seguenti:  
  
-   Creazione di una procedura guidata per un tipo di elemento di progetto SharePoint personalizzato associato a un modello di progetto.  
  
-   Definizione di una procedura guidata personalizzata dell'interfaccia utente simile alle procedure guidate predefinite per i progetti di SharePoint in Visual Studio.  
  
-   Creazione di due *comandi SharePoint* usate per effettuare chiamate nel sito di SharePoint locale, mentre è in esecuzione la procedura guidata. I comandi di SharePoint sono metodi che possono essere utilizzati dalle estensioni per Visual Studio per chiamare le API nel modello a oggetti server SharePoint. Per altre informazioni, vedere [chiamate a modelli a oggetti SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Uso dei parametri sostituibili per inizializzare i file di progetto SharePoint con i dati raccolti nella procedura guidata.  
  
-   Creazione di un nuovo file con estensione snk in ogni nuova istanza di progetto colonna del sito. Questo file viene usato per firmare il progetto in modo che l'assembly della soluzione SharePoint può essere distribuito nella global assembly cache di output.  
  
-   Il debug e test della procedura guidata.  
  
> [!NOTE]  
> Per una serie di flussi di lavoro di esempio, vedere [esempi di flusso di lavoro di SharePoint](https://docs.microsoft.com/sharepoint/dev/general-development/sharepoint-workflow-samples).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura dettagliata, è necessario innanzitutto creare la soluzione SiteColumnProjectItem completando [procedura dettagliata: creazione di un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).  
  
 Sono inoltre necessari i componenti seguenti nel computer di sviluppo per completare questa procedura dettagliata:  
  
- Edizioni supportate di Windows, SharePoint e Visual Studio.
  
- Visual Studio SDK. Questa procedura dettagliata Usa il **progetto VSIX** modello nel SDK per creare un pacchetto VSIX per distribuire l'elemento del progetto. Per altre informazioni, vedere [estendere gli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
  Conoscenza dei concetti seguenti è utile, ma non obbligatorio, completare la procedura dettagliata:  
  
- Procedure guidate per i modelli di progetto ed elemento in Visual Studio. Per altre informazioni, vedere [procedura: usare procedure guidate con modelli di progetto](../extensibility/how-to-use-wizards-with-project-templates.md) e il <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaccia.  
  
- Colonne del sito in SharePoint. Per altre informazioni, vedere [colonne](http://go.microsoft.com/fwlink/?LinkId=183547).  
  
## <a name="understand-the-wizard-components"></a>Informazioni sui componenti di procedura guidata
 La procedura guidata illustrata in questa procedura dettagliata contiene diversi componenti. Nella tabella seguente vengono descritti questi componenti.  
  
|Componente|Descrizione|  
|---------------|-----------------|  
|Implementazione della procedura guidata|Si tratta di una classe, denominata `SiteColumnProjectWizard`, che implementa il <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaccia. Questa interfaccia definisce i metodi che Visual Studio viene chiamato quando inizia e termina e in determinati momenti durante la procedura guidata viene eseguita la procedura guidata.|  
|Creazione guidata dell'interfaccia utente|Si tratta di una finestra basata su WPF, denominata `WizardWindow`. In questa finestra include due controlli utente, denominati `Page1` e `Page2`. Questi controlli utente rappresentano le due pagine della procedura guidata.<br /><br /> In questa procedura dettagliata, il <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> metodo di implementazione della procedura guidata consente di visualizzare la procedura guidata dell'interfaccia utente.|  
|Modello di dati guidata|Questa è una classe intermedia, denominata `SiteColumnWizardModel`, che fornisce un livello tra l'interfaccia utente della procedura guidata e l'implementazione della procedura guidata. In questo esempio utilizza questa classe per consentire la separazione dell'implementazione e la procedura guidata dell'interfaccia utente tra loro; Questa classe non è un componente obbligatorio per tutte le procedure guidate.<br /><br /> In questa procedura dettagliata, l'implementazione della procedura guidata passa un `SiteColumnWizardModel` oggetto per la finestra della procedura guidata quando viene visualizzata la procedura guidata dell'interfaccia utente. La procedura guidata dell'interfaccia utente usa i metodi di questo oggetto per salvare i valori dei controlli nell'interfaccia utente e per eseguire attività quali verifica che l'URL del sito di input sia valido. Dopo che l'utente termina la procedura guidata, l'implementazione della procedura guidata Usa la `SiteColumnWizardModel` oggetto per determinare lo stato finale dell'interfaccia utente.|  
|Gestione di firma di progetto|Si tratta di una classe helper denominata `ProjectSigningManager`, che viene usato per l'implementazione della procedura guidata per creare un nuovo file snk in ogni nuova istanza del progetto.|  
|SharePoint (comandi)|Questi sono metodi che vengono utilizzati dal modello di dati guidata per effettuare chiamate nel sito di SharePoint locale, mentre è in esecuzione la procedura guidata. Poiché i comandi di SharePoint devono destinati a .NET Framework 3.5, questi comandi vengono implementati in un assembly diverso rispetto al resto del codice della procedura guidata.|  
  
## <a name="create-the-projects"></a>Creare i progetti
 Per completare questa procedura dettagliata, è necessario aggiungere più progetti alla soluzione creata in SiteColumnProjectItem [procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md):  
  
- Un progetto WPF. Si implementeranno i <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaccia e definire la procedura guidata dell'interfaccia utente in questo progetto.  
  
- Un progetto libreria di classi che definisce i comandi di SharePoint. Questo progetto deve avere come destinazione.NET Framework 3.5.  
  
  Avviare la procedura dettagliata mediante la creazione di progetti.  
  
#### <a name="to-create-the-wpf-project"></a>Per creare il progetto WPF
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], aprire la soluzione SiteColumnProjectItem.  
  
2.  In **Esplora soluzioni**, aprire il menu di scelta rapida per il **SiteColumnProjectItem** nodo della soluzione, scegliere **Add**, quindi scegliere **nuovo progetto**.  
  
3.  In cima il **Aggiungi nuovo progetto** finestra di dialogo, assicurarsi che **.NET Framework 4.5** viene scelto nell'elenco delle versioni di .NET Framework.  
  
4.  Espandere la **Visual c#** nodo o il **Visual Basic** nodo, scegliere il **Windows** nodo.  
  
5.  Nell'elenco dei modelli di progetto, scegliere **libreria di controlli utente WPF**, denominare il progetto **ProjectTemplateWizard**, quindi scegliere il **OK** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il **ProjectTemplateWizard** progetto alla soluzione e apre il file UserControl1.xaml predefinito.  
  
6.  Eliminare il file UserControl1.xaml dal progetto.  
  
#### <a name="to-create-the-sharepoint-commands-project"></a>Per creare il progetto di comandi di SharePoint  
  
1.  Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il nodo della soluzione SiteColumnProjectItem, scegliere **Add**, quindi scegliere **nuovo progetto**.  
  
2.  In cima il **Aggiungi nuovo progetto** finestra di dialogo, scegliere **.NET Framework 3.5** nell'elenco delle versioni di .NET Framework.  
  
3.  Espandere il **Visual c#** nodo o il **Visual Basic** nodo, quindi scegliere il **Windows** nodo.  
  
4.  Scegliere il **libreria di classi** modello di progetto, denominare il progetto **SharePointCommands**, quindi scegliere il **OK** pulsante.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il **SharePointCommands** progetto alla soluzione e apre il file di codice predefinita Class1.  
  
5.  Eliminare il file di codice Class1 dal progetto.  
  
## <a name="configure-the-projects"></a>Configurare i progetti
 Prima di creare la procedura guidata, è necessario aggiungere alcuni file di codice e i riferimenti ad assembly per i progetti.  
  
#### <a name="to-configure-the-wizard-project"></a>Per configurare il progetto della procedura guidata  
  
1.  Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **ProjectTemplateWizard** nodo del progetto e quindi scegliere **proprietà**.  
  
2.  Nel **creazione progetti**, scegliere il **Application** scheda per un progetto Visual c# o la **compilare** scheda per un progetto Visual Basic.  
  
3.  Assicurarsi che il framework di destinazione sia impostato su .NET Framework 4.5, non .NET Framework 4.5 Client Profile.  
  
     Per altre informazioni, vedere [Procedura: Destinare una versione di .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
4.  Aprire il menu di scelta rapida per il **ProjectTemplateWizard** del progetto, scegliere **Add**, quindi scegliere **nuovo elemento**.  
  
5.  Scegliere il **finestra (WPF)** voce, denominare l'elemento **nome WizardWindow**, quindi scegliere il **Aggiungi** pulsante.  
  
6.  Aggiungere due **controllo utente (WPF)** gli elementi al progetto e denominarli **Page1** e **Page2**.  
  
7.  Aggiungere quattro file di codice al progetto e fornire loro i nomi seguenti:  
  
    -   SiteColumnProjectWizard  
  
    -   SiteColumnWizardModel  
  
    -   ProjectSigningManager  
  
    -   CommandIds  
  
8.  Aprire il menu di scelta rapida per il **ProjectTemplateWizard** nodo di progetto e quindi scegliere **Aggiungi riferimento**.  
  
9. Espandere la **gli assembly** nodo, scegliere il **estensioni** nodo e quindi selezionare le caselle di controllo accanto agli assembly seguenti:  
  
    -   EnvDTE  
  
    -   Interop  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.10.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
10. Scegliere il **OK** pulsante per aggiungere gli assembly al progetto.  
  
11. Nella **Esplora soluzioni**, sotto il **riferimenti** cartella per il **ProjectTemplateWizard** del progetto, scegliere **EnvDTE**.  
  
12. Nel **le proprietà** finestra, modificare il valore della **incorpora tipi di interoperabilità** proprietà **False**.  
  
13. Se si sta sviluppando un progetto Visual Basic, importare lo spazio dei nomi ProjectTemplateWizard nel progetto usando il **Progettazione progetti**.  
  
     Per altre informazioni, vedere [procedura: aggiungere o rimuovere spazi dei nomi importati &#40;Visual Basic&#41;](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md).  
  
#### <a name="to-configure-the-sharepointcommands-project"></a>Per configurare il progetto SharePointcommands
  
1.  Nelle **Esplora soluzioni**, scegliere il **SharePointCommands** nodo del progetto.  
  
2.  Nella barra dei menu, scegliere **Project**, **Aggiungi elemento esistente**.  
  
3.  Nel **Aggiungi elemento esistente** della finestra di dialogo passare alla cartella che contiene i file di codice per il progetto ProjectTemplateWizard e quindi scegliere il **CommandIds** file di codice.  
  
4.  Scegliere la freccia accanto al **Add** pulsante e quindi scegliere il **Aggiungi come collegamento** opzione nel menu visualizzato.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aggiunge il file di codice per il **SharePointCommands** progetto come collegamento. Il file di codice si trova nella **ProjectTemplateWizard** anche progetto, ma il codice nel file viene compilato nel **SharePointCommands** progetto.  
  
5.  Nel **SharePointCommands** del progetto, aggiungere un altro file di codice denominato comandi.  
  
6.  Scegliere il progetto SharePointCommands e quindi nella barra dei menu scegliere **Project** > **Aggiungi riferimento**.  
  
7.  Espandere la **gli assembly** nodo, scegliere il **estensioni** nodo e quindi selezionare le caselle di controllo accanto agli assembly seguenti:  
  
    -   Microsoft. SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
8.  Scegliere il **OK** pulsante per aggiungere gli assembly al progetto.  
  
## <a name="create-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>Creare il modello di procedura guidata, manager firma e gli ID di comando di SharePoint
 Aggiungere codice al progetto ProjectTemplateWizard per implementare i componenti seguenti nell'esempio:  
  
- Gli ID di comando di SharePoint. Queste stringhe di identificano i comandi di SharePoint che utilizza la procedura guidata. Più avanti in questa procedura dettagliata si aggiungerà codice al progetto SharePointCommands per implementare i comandi.  
  
- Il modello di dati guidata.  
  
- Firma il project manager.  
  
  Per altre informazioni su questi componenti, vedere [informazioni sui componenti della procedura guidata](#wizardcomponents).  
  
#### <a name="to-define-the-sharepoint-command-ids"></a>Per definire gli ID di comando di SharePoint
  
1.  Nel progetto ProjectTemplateWizard, aprire il file di codice CommandIds e quindi sostituire l'intero contenuto di questo file con il codice seguente.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb#5)]  
  
#### <a name="to-create-the-wizard-model"></a>Per creare il modello di procedura guidata  
  
1.  Aprire il codice SiteColumnWizardModel e sostituire l'intero contenuto di questo file con il codice seguente.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]  
  
#### <a name="to-create-the-project-signing-manager"></a>Per creare il project manager firma  
  
1.  Aprire il file di codice ProjectSigningManager e quindi sostituire l'intero contenuto di questo file con il codice seguente.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb#8)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs#8)]  
  
## <a name="create-the-wizard-ui"></a>Creazione guidata dell'interfaccia utente
 Aggiungere XAML per definire l'interfaccia utente della finestra della procedura guidata e i due controlli utente che forniscono l'interfaccia utente per le pagine della procedura guidata e aggiungere il codice per definire il comportamento dei controlli finestra e utente. La procedura guidata che si crea è simile alla procedura guidata predefinita per i progetti di SharePoint in Visual Studio.  
  
> [!NOTE]  
>  Nei passaggi seguenti, il progetto avrà alcuni errori di compilazione dopo l'aggiunta XAML o codice al progetto. Questi errori scompare quando si aggiunge codice nei passaggi successivi.  
  
#### <a name="to-create-the-wizard-window-ui"></a>Per creare la finestra della procedura guidata dell'interfaccia utente
  
1.  Nel progetto ProjectTemplateWizard, aprire il menu di scelta rapida per il file WizardWindow e quindi scegliere **aprire** per aprire la finestra nella finestra di progettazione.  
  
2.  Nella visualizzazione della finestra di progettazione XAML, sostituire il XAML corrente con il XAML seguente. il XAML definisce un'interfaccia utente che include un'intestazione, un <xref:System.Windows.Controls.Grid> che contiene le pagine della procedura guidata e pulsanti di navigazione nella parte inferiore della finestra.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml#10)]  
  
    > [!NOTE]  
    >  La finestra che viene creata in questo XAML viene ottenuta il <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> classe di base. Quando si aggiunge una finestra di dialogo WPF personalizzata in Visual Studio, è consigliabile che la finestra di dialogo si deriva da questa classe sono coerenti con l'applicazione di stili con altre finestre di dialogo di Visual Studio ed evitare problemi di finestra di dialogo modale che potrebbero verificarsi in caso contrario. Per altre informazioni, vedere [creazione e la gestione delle finestre di dialogo modale](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes).  
  
3.  Se si sta sviluppando un progetto Visual Basic, rimuovere il `ProjectTemplateWizard` dello spazio dei nomi dal `WizardWindow` nome di classe nel `x:Class` attributo del `Window` elemento. Questo elemento è nella prima riga della finestra di XAML. Al termine, la prima riga dovrebbe essere simile all'esempio seguente.  
  
    ```xml  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  Aprire il file code-behind per il file WizardWindow.  
  
5.  Sostituire il contenuto di questo file, ad eccezione di `using` dichiarazioni all'inizio del file, con il codice seguente.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb#4)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs#4)]  
  
#### <a name="to-create-the-first-wizard-page-ui"></a>Per creare la prima pagina dell'interfaccia utente
  
1.  Nel progetto ProjectTemplateWizard, aprire il menu di scelta rapida per il file Page1.xaml e quindi scegliere **aprire** per aprire il controllo utente nella finestra di progettazione.  
  
2.  Nella visualizzazione della finestra di progettazione XAML, sostituire il XAML corrente con il XAML seguente. il XAML definisce un'interfaccia utente che include una casella di testo in cui gli utenti possono immettere l'URL dei siti locali che si desiderano utilizzare per il debug. L'interfaccia utente include anche i pulsanti di opzione con cui gli utenti possono specificare se il progetto è in modalità sandbox.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml#11)]  
  
3.  Se si sviluppa un progetto Visual Basic, rimuovere il `ProjectTemplateWizard` dello spazio dei nomi dal `Page1` nome di classe nel `x:Class` attributo del `UserControl` elemento. Questa è la prima riga il XAML. Al termine, la prima riga dovrebbe essere simile al seguente.  
  
    ```xml  
    <UserControl x:Class="Page1"  
    ```  
  
4.  Sostituire il contenuto del file Page1.xaml, fatta eccezione per il `using` dichiarazioni all'inizio del file, con il codice seguente.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs#2)]  
  
#### <a name="to-create-the-second-wizard-page-ui"></a>Per creare la seconda pagina della procedura guidata dell'interfaccia utente
  
1.  Nel progetto ProjectTemplateWizard, aprire il menu di scelta rapida per il file Page2. XAML e quindi scegliere **aprire**.  
  
     Il controllo utente viene visualizzato nella finestra di progettazione.  
  
2.  Nella visualizzazione XAML, sostituire il XAML corrente con il XAML seguente. il XAML definisce un'interfaccia utente che include un elenco di riepilogo a discesa per scegliere il tipo di base della colonna del sito, una casella combinata per la specifica di un gruppo predefinito o personalizzato in cui si desidera visualizzare la colonna del sito nella raccolta e una casella di testo per specificare il nome della colonna del sito.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml#12)]  
  
3.  Se si sviluppa un progetto Visual Basic, rimuovere il `ProjectTemplateWizard` dello spazio dei nomi dal `Page2` nome di classe nel `x:Class` attributo del `UserControl` elemento. Questa è la prima riga il XAML. Al termine, la prima riga dovrebbe essere simile al seguente.  
  
    ```xml  
    <UserControl x:Class="Page2"  
    ```  
  
4.  Sostituire il contenuto del file code-behind per il file Page2. XAML, ad eccezione di `using` dichiarazioni all'inizio del file, con il codice seguente.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb#3)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs#3)]  
  
## <a name="implement-the-wizard"></a>Implementare la procedura guidata
 Definire la funzionalità principale della procedura guidata mediante l'implementazione di <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaccia. Questa interfaccia definisce i metodi che Visual Studio viene chiamato quando inizia e termina e in determinati momenti durante la procedura guidata viene eseguita la procedura guidata.  
  
#### <a name="to-implement-the-wizard"></a>Per implementare la procedura guidata  
  
1.  Nel progetto ProjectTemplateWizard, aprire il codice SiteColumnProjectWizard.  
  
2.  Sostituire l'intero contenuto di questo file con il codice seguente.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]  
  
## <a name="create-the-sharepoint-commands"></a>Creare i comandi di SharePoint
 Creare due comandi personalizzati che effettuano chiamate nel modello a oggetti server SharePoint. Un unico comando determina se l'URL del sito che l'utente digita nella procedura guidata è valido. Dei due comandi Ottiene tutti i tipi di campo dal sito di SharePoint specificato in modo che gli utenti possono selezionare quello da usare come base per le nuove colonne del sito.  
  
#### <a name="to-define-the-sharepoint-commands"></a>Per definire i comandi di SharePoint  
  
1.  Nel **SharePointCommands** del progetto, aprire il file di codice i comandi.  
  
2.  Sostituire l'intero contenuto di questo file con il codice seguente.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb#9)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs#9)]  
  
## <a name="checkpoint"></a>Checkpoint  
 A questo punto della procedura dettagliata, tutto il codice per la procedura guidata è ora nel progetto. Compilare il progetto per assicurarsi che venga compilata senza errori.  
  
#### <a name="to-build-your-project"></a>Per compilare il progetto  
  
1.  Nella barra dei menu scegliere **Compila** > **Compila soluzione**.  
  
## <a name="removing-the-keysnk-file-from-the-project-template"></a>Rimozione del file snk dal modello di progetto
 Nelle [procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md), il modello di progetto creato contiene un file snk utilizzato per firmare ogni istanza di progetto colonna del sito. Questo file snk è più necessario perché la procedura guidata genera ora un nuovo file snk per ogni progetto. Rimuovere il file snk dal modello di progetto e rimuovere i riferimenti a questo file.  
  
#### <a name="to-remove-the-keysnk-file-from-the-project-template"></a>Per rimuovere il file snk dal modello di progetto  
  
1.  In **Esplora soluzioni**, sotto il **SiteColumnProjectTemplate** nodo, aprire il menu di scelta rapida per il **snk** file e quindi scegliere **eliminare**.  
  
2.  Nella finestra di dialogo di conferma visualizzata, scegliere il **OK** pulsante.  
  
3.  Sotto il **SiteColumnProjectTemplate** nodo, aprire il file SiteColumnProjectTemplate e quindi rimuovere l'elemento seguente da quest'ultimo.  
  
    ```xml  
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
    ```  
  
4.  Salvare e chiudere il file.  
  
5.  Sotto il **SiteColumnProjectTemplate** nodo, aprire il file csproj o ProjectTemplate e quindi rimuovere il segue `PropertyGroup` elemento da quest'ultimo.  
  
    ```xml  
    <PropertyGroup>  
      <SignAssembly>true</SignAssembly>  
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
    </PropertyGroup>  
    ``` 
  
6.  Rimuovere il seguente `None` elemento.  
  
    ```xml  
    <None Include="key.snk" />  
    ```  
  
7.  Salvare e chiudere il file.  
  
## <a name="associating-the-wizard-with-the-project-template"></a>Associazione della procedura guidata con il modello di progetto
 Ora che è stata implementata la procedura guidata, è necessario associare la procedura guidata con le **colonne del sito** modello di progetto. Esistono tre procedure, che è necessario completare per eseguire questa operazione:  
  
1.  Firmare l'assembly della procedura guidata con un nome sicuro.  
  
2.  Ottenere la chiave pubblica token per l'assembly della procedura guidata.  
  
3.  Aggiungere un riferimento all'assembly della procedura guidata nel file con estensione vstemplate per il **colonne del sito** modello di progetto.  
  
#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Per firmare l'assembly della procedura guidata con un nome sicuro  
  
1.  Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il **ProjectTemplateWizard** del progetto e quindi scegliere **proprietà**.  
  
2.  Nel **Signing** scheda, seleziona la **firmare l'assembly** casella di controllo.  
  
3.  Nel **Scegli un file chiave con nome sicuro** casella di riepilogo  **\<nuovo... >**.  
  
4.  Nel **Crea chiave con nome sicuro** finestra di dialogo immettere un nome per il nuovo file di chiave, deselezionare le **Proteggi file di chiave con una password** casella di controllo e quindi scegliere il **OK** pulsante.  
  
5.  Aprire il menu di scelta rapida per il **ProjectTemplateWizard** del progetto e quindi scegliere **compilazione** per creare il file ProjectTemplateWizard. dll.  
  
#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Per ottenere il token di chiave pubblica per l'assembly della procedura guidata  
  
1.  Nel **dal Menu Start**, scegliere **tutti i programmi**, scegliere **Microsoft Visual Studio**, scegliere **Visual Studio Tools**e quindi scegliere  **Prompt dei comandi sviluppatore**.  
  
     Verrà visualizzata la finestra del Prompt dei comandi di Visual Studio.  
  
2.  Eseguire il comando seguente, sostituendo *PathToWizardAssembly* con il percorso completo per l'assembly compilato ProjectTemplateWizard. dll per il progetto ProjectTemplateWizard nel computer di sviluppo:  
  
    ```cmd  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     Il token di chiave pubblica per l'assembly ProjectTemplateWizard. dll viene scritto nella finestra del Prompt dei comandi di Visual Studio.  
  
3.  Mantenere aperta la finestra del Prompt dei comandi di Visual Studio. È necessario il token di chiave pubblica durante la procedura seguente.  
  
#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Per aggiungere un riferimento all'assembly della procedura guidata nel file con estensione vstemplate  
  
1.  Nelle **Esplora soluzioni**, espandere il **SiteColumnProjectTemplate** nodo del progetto e aprire il file SiteColumnProjectTemplate.  
  
2.  Verso la fine del file, aggiungere quanto segue `WizardExtension` elemento tra il `</TemplateContent>` e `</VSTemplate>` tag. Sostituire il *il token* pari al `PublicKeyToken` attributo con il token di chiave pubblica ottenuto nella procedura precedente.  
  
    ```xml  
    <WizardExtension>  
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>  
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     Per altre informazioni sul `WizardExtension` elemento, vedere [elemento WizardExtension &#40;modelli di Visual Studio&#41;](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).  
  
3.  Salvare e chiudere il file.  
  
## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>Aggiungere parametri sostituibili nel file Elements. XML nel modello di progetto
 Aggiungere parametri sostituibili diversi per il *Elements. XML* file nel progetto SiteColumnProjectTemplate. Questi parametri vengono inizializzati nel `RunStarted` nel metodo il `SiteColumnProjectWizard` classe definita in precedenza. Quando un utente crea un progetto colonna del sito, Visual Studio sostituisce automaticamente questi parametri, il *Elements* file nel nuovo progetto con i valori che vengono specificati nella procedura guidata.  
  
 Un parametro sostituibile è un token che inizia e finisce con il simbolo di dollaro ($). Oltre a definire i propri parametri sostituibili, è possibile usare i parametri predefiniti che vengono definiti e inizializzati dal sistema del progetto SharePoint. Per altre informazioni, vedere [parametri sostituibili](../sharepoint/replaceable-parameters.md).  
  
#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Per aggiungere parametri sostituibili nel file Elements. Xml
  
1.  Nel progetto SiteColumnProjectTemplate, sostituire il contenuto del *Elements* file con il codice XML seguente.  
  
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
  
     Il nuovo codice XML modificano i valori del `Name`, `DisplayName`, `Type`, e `Group` attributi a parametri sostituibili personalizzati.  
  
2.  Salvare e chiudere il file.  
  
## <a name="add-the-wizard-to-the-vsix-package"></a>Aggiungere la procedura guidata per il pacchetto VSIX
 Per distribuire la procedura guidata con il pacchetto VSIX che contiene il modello di progetto colonna del sito, aggiungere i riferimenti al progetto della procedura guidata e il progetto di comandi di SharePoint al file vsixmanifest nel progetto VSIX.  
  
#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Per aggiungere la procedura guidata per il pacchetto VSIX  
  
1.  Nella **Esplora soluzioni**, nella **SiteColumnProjectItem** del progetto, aprire il menu di scelta rapida per il **vsixmanifest** file e quindi scegliere **Open**.  
  
     Visual Studio apre il file nell'editor del manifesto.  
  
2.  Nel **asset** della scheda dell'editor, scegliere il **New** pulsante.  
  
     Il **Aggiungi nuovo Asset** verrà visualizzata la finestra di dialogo.  
  
3.  Nel **tipo** casella di riepilogo **Microsoft.VisualStudio.Assembly**.  
  
4.  Nel **origine** casella di riepilogo **un progetto nella soluzione corrente**.  
  
5.  Nel **progetto** scegliere **ProjectTemplateWizard**, quindi scegliere il **OK** pulsante.  
  
6.  Nel **asset** della scheda dell'editor, scegliere il **New** nuovamente clic sul pulsante.  
  
     Il **Aggiungi nuovo Asset** verrà visualizzata la finestra di dialogo.  
  
7.  Nel **tipo** elenco, immettere **v4**.  
  
8.  Nel **origine** casella di riepilogo **un progetto nella soluzione corrente**.  
  
9. Nel **Project** scegliere il **SharePointCommands** del progetto e quindi scegliere il **OK** pulsante.  
  
10. Nella barra dei menu, scegliere **compilare** > **Compila soluzione**, quindi assicurarsi che la soluzione venga compilata senza errori.  
  
## <a name="test-the-wizard"></a>Testare la procedura guidata
 A questo punto si è pronti testare la procedura guidata. Innanzitutto, avviare il debug della soluzione SiteColumnProjectItem nell'istanza sperimentale di Visual Studio. Testare quindi la procedura guidata per il progetto colonna del sito nell'istanza sperimentale di Visual Studio. Infine, compilare ed eseguire il progetto per verificare che la colonna del sito funziona come previsto.  
  
#### <a name="to-start-debugging-the-solution"></a>Per avviare il debug della soluzione  
  
1.  Riavviare Visual Studio con credenziali amministrative e quindi aprire la soluzione SiteColumnProjectItem.  
  
2.  Nel progetto ProjectTemplateWizard, aprire il codice SiteColumnProjectWizard e quindi aggiungere un punto di interruzione per la prima riga del codice nel `RunStarted` (metodo).  
  
3.  Nella barra dei menu, scegliere **Debug** > **eccezioni**.  
  
4.  Nel **eccezioni** finestra di dialogo, assicurarsi che le **generata** e **User-unhandled** caselle di controllo per **eccezioni Common Language Runtime**vengono cancellati e quindi scegliere il **OK** pulsante.  
  
5.  Avviare il debug scegliendo il **F5** chiave o, nella barra dei menu, scegliendo **Debug** > **Avvia debug**.  
  
     Visual Studio installa l'estensione %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Site Column\1.0 e avvia un'istanza sperimentale di Visual Studio. Si testerà l'elemento del progetto in questa istanza di Visual Studio.  
  
#### <a name="to-test-the-wizard-in-visual-studio"></a>Per testare la procedura guidata in Visual Studio  
  
1. Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **File** > **New** > **progetto**.  
  
2. Espandere la **Visual c#** nodo o il **Visual Basic** nodo (a seconda del linguaggio che supporta il modello di progetto), espandere il **SharePoint** nodo e quindi scegliere il **2010** nodo.  
  
3. Nell'elenco dei modelli di progetto, scegliere **colonne del sito**, denominare il progetto **SiteColumnWizardTest**, quindi scegliere il **OK** pulsante.  
  
4. Verificare che il codice in altra istanza di Visual Studio si arresta nel punto di interruzione impostato in precedenza nel `RunStarted` (metodo).  
  
5. Continuare il debug del progetto scegliendo il **F5** chiave o, nella barra dei menu, scegliendo **Debug** > **continua**.  
  
6. Nel **Personalizzazione guidata SharePoint**, immettere l'URL del sito che si desidera utilizzare per il debug e quindi scegliere il **successivo** pulsante.  
  
7. Nella seconda pagina della finestra di **Personalizzazione guidata SharePoint**, effettuare le selezioni seguenti:  
  
   - Nel **tipo** casella di riepilogo **booleano**.  
  
   - Nel **gruppo** casella di riepilogo **Custom Sì/No colonne**.  
  
   - Nel **nome** casella, immettere **My Sì/No colonna**e quindi scegliere il **fine** pulsante.  
  
     Nelle **Esplora soluzioni**, un nuovo progetto viene visualizzato e contiene un elemento del progetto denominato **Field1**, e Visual Studio apre il progetto *Elements* file nell'editor.  
  
8. Verificare che *Elements* contiene i valori specificati nella procedura guidata.  
  
#### <a name="to-test-the-site-column-in-sharepoint"></a>Per testare la colonna del sito in SharePoint  
  
1.  Nell'istanza sperimentale di Visual Studio, scegliere il **F5** chiave.  
  
     La colonna del sito è incluso nel pacchetto e distribuzione di SharePoint del sito che il **URL sito** specifica proprietà del progetto. Il browser viene visualizzata la pagina predefinita del sito.  
  
    > [!NOTE]  
    >  Se il **debug degli Script disabilitato** verrà visualizzata la finestra di dialogo, scegliere il **Yes** per continuare il debug del progetto.  
  
2.  Nel **Azioni sito** menu, scegliere **Impostazioni sito**.  
  
3.  Nella pagina Impostazioni sito sotto **Galleries**, scegliere il **le colonne del sito** collegamento.  
  
4.  Nell'elenco delle colonne del sito, verificare che un **colonne Sì/No personalizzate** gruppo contiene una colonna denominata **My Sì/No colonna**e quindi chiudere il browser web.  
  
## <a name="clean-up-the-development-computer"></a>Pulire il computer di sviluppo
 Dopo aver completato l'elemento del progetto di test, rimuovere il modello di progetto dall'istanza sperimentale di Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Per pulire il computer di sviluppo  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **degli strumenti** > **estensioni e aggiornamenti**.  
  
     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.  
  
2.  Nell'elenco delle estensioni, scegliere **colonne del sito**, quindi scegliere il **Disinstalla** pulsante.  
  
3.  Nella finestra di dialogo visualizzata, scegliere il **Yes** per confermare che si desidera disinstallare l'estensione e quindi scegliere il **Riavvia ora** pulsante per completare la disinstallazione.  
  
4.  Chiudere l'istanza sperimentale di Visual Studio sia l'istanza in cui la soluzione CustomActionProjectItem è aperta.  
  
     Per informazioni su come distribuire [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] le estensioni, vedere [spedizione di estensioni di Visual Studio](/visualstudio/extensibility/shipping-visual-studio-extensions).  
  
## <a name="see-also"></a>Vedere anche
 [Procedura dettagliata: Creare un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Definire tipi di elemento di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creazione di modelli di elementi e modelli di progetto per elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Riferimenti allo schema dei modelli di Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [Procedura: Usare procedure guidate con modelli di progetto](../extensibility/how-to-use-wizards-with-project-templates.md)  
  
