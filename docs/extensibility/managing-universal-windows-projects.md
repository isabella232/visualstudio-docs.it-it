---
title: Gestione di progetti Windows universali - Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc6894bcfe3bfab3b0246d716b0bd85152ad17e2
ms.sourcegitcommit: 5c804c42d24d35dcf2ba195aba9ce07031743f62
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "81744946"
---
# <a name="manage-universal-windows-projects"></a>Gestire progetti Windows universali

Le app di Windows universali sono app destinate a Windows 8.1 e Windows Phone 8.1, consentendo agli sviluppatori di usare codice e altre risorse su entrambe le piattaforme. Il codice condiviso e le risorse vengono mantenuti in un progetto condiviso, mentre il codice specifico della piattaforma e le risorse vengono mantenute in progetti separati, uno per Windows e l'altro per Windows Phone. Per ulteriori informazioni sulle app di Windows universali, vedere [App di Windows universali](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx). Le estensioni di Visual Studio che gestiscono i progetti devono tenere presente che i progetti di app Windows universali hanno una struttura diversa dalle app a piattaforma singola. In questa procedura dettagliata viene illustrato come esplorare il progetto condiviso e gestire gli elementi condivisi.

## <a name="prerequisites"></a>Prerequisiti

A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It's included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

### <a name="navigate-the-shared-project"></a>Esplorare il progetto condiviso

1. Creare un progetto VSIX di C, denominato **TestUniversalProject**. (**File** > **Nuovo** > **progetto** e quindi pacchetto di estensibilità di Visual**Studio**di**estensibilità** >  **c'è** > ). Aggiungere un modello di elemento di progetto **Comando personalizzato** (in **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi** > **nuovo elemento**, quindi scegliere **Estensibilità**). Assegnare al file il nome **TestUniversalProject**.

2. Aggiungere un riferimento a *Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll* e *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll* (nella sezione **Extensions).**

3. Aprire *TestUniversalProject.cs* e `using` aggiungere le direttive seguenti:Open TestUniversalProject.cs and add the following directives:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.PlatformUI;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using System.Collections.Generic;
    using System.IO;
    using System.Windows.Forms;
    ```

4. Nella `TestUniversalProject` classe aggiungere un campo privato che punta alla finestra **Output.In** the class add a private field pointing to the Output window.

    ```csharp
    public sealed class TestUniversalProject
    {
        IVsOutputWindowPane output;
    . . .
    }
    ```

5. Impostare il riferimento al riquadro di output all'interno del costruttore TestUniversalProject:Set the reference to the output pane inside TestUniversalProject constructor:

    ```csharp
    private TestUniversalProject(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);
            EventHandler eventHandler = this.ShowMessageBox;
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);
            commandService.AddCommand(menuItem);
        }

        // get a reference to the Output window
        output = (IVsOutputWindowPane)ServiceProvider.GetService(typeof(SVsGeneralOutputWindowPane));
    }
    ```

6. Rimuovere il codice `ShowMessageBox` esistente dal metodo:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
    }
    ```

7. Ottenere l'oggetto DTE, che verrà utilizzato per diversi scopi in questa procedura dettagliata. Inoltre, assicurarsi che una soluzione viene caricata quando si fa clic sul pulsante di menu.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (EnvDTE.DTE)this.ServiceProvider.GetService(typeof(EnvDTE.DTE));
        if (dte.Solution != null)
        {
            . . .
        }
        else
        {
            MessageBox.Show("No solution is open");
            return;
        }
    }
    ```

8. Trovare il progetto condiviso. Il progetto condiviso è un contenitore puro; non compila né produce output. Il metodo seguente trova il primo progetto condiviso <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> nella soluzione cercando l'oggetto con la funzionalità di progetto condivisa.

    ```csharp
    private IVsHierarchy FindSharedProject()
    {
        var sln = (IVsSolution)this.ServiceProvider.GetService(typeof(SVsSolution));
        Guid empty = Guid.Empty;
        IEnumHierarchies enumHiers;

        //get all the projects in the solution
        ErrorHandler.ThrowOnFailure(sln.GetProjectEnum((uint)__VSENUMPROJFLAGS.EPF_LOADEDINSOLUTION, ref empty, out enumHiers));
        foreach (IVsHierarchy hier in ComUtilities.EnumerableFrom(enumHiers))
        {
            if (PackageUtilities.IsCapabilityMatch(hier, "SharedAssetsProject"))
            {
                return hier;
            }
        }
        return null;
    }
    ```

9. Nel `ShowMessageBox` metodo restituisce la didascalia (il nome del progetto visualizzato in **Esplora soluzioni)** del progetto condiviso.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));

        if (dte.Solution != null)
        {
            var sharedHier = this.FindSharedProject();
            if (sharedHier != null)
            {
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,
                     (int)__VSHPROPID.VSHPROPID_Caption);
                output.OutputStringThreadSafe(string.Format("Found shared project: {0}\n", sharedCaption));
            }
            else
            {
                MessageBox.Show("Solution has no shared project");
                return;
            }
        }
        else
        {
            MessageBox.Show("No solution is open");
            return;
        }
    }
    ```

10. Ottenere il progetto della piattaforma attiva. I progetti di piattaforma sono i progetti che contengono risorse e codice specifici della piattaforma. Il metodo seguente utilizza <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy> il nuovo campo per ottenere il progetto di piattaforma attivo.

    ```csharp
    private IVsHierarchy GetActiveProjectContext(IVsHierarchy hierarchy)
    {
        IVsHierarchy activeProjectContext;
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,
             (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, out activeProjectContext))
        {
            return activeProjectContext;
        }
        else
        {
            return null;
        }
    }
    ```

11. Nel `ShowMessageBox` metodo, restituire la didascalia del progetto di piattaforma attiva.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));

        if (dte.Solution != null)
        {
            var sharedHier = this.FindSharedProject();
            if (sharedHier != null)
            {
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,
                     (int)__VSHPROPID.VSHPROPID_Caption);
                output.OutputStringThreadSafe(string.Format("Shared project: {0}\n", sharedCaption));

                var activePlatformHier = this.GetActiveProjectContext(sharedHier);
                if (activePlatformHier != null)
                {
                    string activeCaption = HierarchyUtilities.GetHierarchyProperty<string>(activePlatformHier,
                         (uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_Caption);
                    output.OutputStringThreadSafe(string.Format("Active platform project: {0}\n", activeCaption));
                }
                else
                {
                    MessageBox.Show("Shared project has no active platform project");
                }
            }
            else
            {
                MessageBox.Show("Solution has no shared project");
            }
        }
        else
        {
            MessageBox.Show("No solution is open");
        }
    }
    ```

12. Scorrere i progetti della piattaforma. Il metodo seguente ottiene tutti i progetti di importazione (piattaforma) dal progetto condiviso.

    ```csharp
    private IEnumerable<IVsHierarchy> EnumImportingProjects(IVsHierarchy hierarchy)
    {
        IVsSharedAssetsProject sharedAssetsProject;
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,
            (int)__VSHPROPID7.VSHPROPID_SharedAssetsProject, out sharedAssetsProject)
            && sharedAssetsProject != null)
        {
            foreach (IVsHierarchy importingProject in sharedAssetsProject.EnumImportingProjects())
            {
                yield return importingProject;
            }
        }
    }
    ```

    > [!IMPORTANT]
    > Se nell'istanza sperimentale è stato aperto un progetto di app di Windows universale di C, il codice precedente genera un'eccezione. Questo è un problema noto Per evitare l'eccezione, sostituire il `foreach` blocco precedente con quanto segue:

    ```csharp
    var importingProjects = sharedAssetsProject.EnumImportingProjects();
    for (int i = 0; i < importingProjects.Count; ++i)
    {
        yield return importingProjects[i];
    }
    ```

13. Nel `ShowMessageBox` metodo, restituire la didascalia di ogni progetto di piattaforma. Inserire il codice seguente dopo la riga che restituisce la didascalia del progetto di piattaforma attiva. Solo i progetti di piattaforma caricati vengono visualizzati in questo elenco.

    ```csharp
    output.OutputStringThreadSafe("Platform projects:\n");

    IEnumerable<IVsHierarchy> projects = this.EnumImportingProjects(sharedHier);

    bool isActiveProjectSet = false;
    foreach (IVsHierarchy platformHier in projects)
    {
        string platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,
            (int)__VSHPROPID.VSHPROPID_Caption);
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));
    }
    ```

14. Modificare il progetto della piattaforma attiva. Il metodo riportato di <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>seguito imposta il progetto attivo utilizzando .

    ```csharp
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)
    {
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);
    }
    ```

15. Nel `ShowMessageBox` metodo, modificare il progetto della piattaforma attiva. Inserire questo codice `foreach` all'interno del blocco.

    ```csharp
    bool isActiveProjectSet = false;
    string platformCaption = null;
    foreach (IVsHierarchy platformHier in projects)
    {
        platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,
             (int)__VSHPROPID.VSHPROPID_Caption);
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));

        // if this project is neither the shared project nor the current active platform project,
        // set it to be the active project
        if (!isActiveProjectSet && platformHier != activePlatformHier)
        {
            this.SetActiveProjectContext(sharedHier, platformHier);
            activePlatformHier = platformHier;
            isActiveProjectSet = true;
        }
    }
    output.OutputStringThreadSafe("set active project: " + platformCaption +'\n');
    ```

16. Ora provalo. Premere F5 per avviare l'istanza sperimentale. Creare un progetto di app dell'hub universale di C' nell'istanza sperimentale (nella finestra di dialogo Nuovo **progetto,** **App hub universale**di**Windows** > **8** > **Universal** > di **Visual Cè** > ). Dopo aver caricato la soluzione, passare al menu **Strumenti** e scegliere **Richiama TestUniversalProject**, quindi controllare il testo nel riquadro **Output** . Verrà visualizzata una schermata simile alla seguente:

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    ```

### <a name="manage-the-shared-items-in-the-platform-project"></a>Gestire gli elementi condivisi nel progetto di piattaformaManage the shared items in the platform project

1. Trovare gli elementi condivisi nel progetto della piattaforma. Gli elementi nel progetto condiviso vengono visualizzati nel progetto di piattaforma come elementi condivisi. Non è possibile visualizzarli in **Esplora soluzioni**, ma è possibile esaminare la gerarchia del progetto per trovarli. Il metodo seguente illustra la gerarchia e raccoglie tutti gli elementi condivisi. Facoltativamente restituisce la didascalia di ogni elemento,. Gli elementi condivisi sono identificati <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_IsSharedItem>dalla nuova proprietà .

    ```csharp
    private void InspectHierarchyItems(IVsHierarchy hier, uint itemid, int level, List<uint> itemIds, bool getSharedItems, bool printItems)
    {
        string caption = HierarchyUtilities.GetHierarchyProperty<string>(hier, itemid, (int)__VSHPROPID.VSHPROPID_Caption);
        if (printItems)
            output.OutputStringThreadSafe(string.Format("{0}{1}\n", new string('\t', level), caption));

        // if getSharedItems is true, inspect only shared items; if it's false, inspect only unshared items
        bool isSharedItem;
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID7.VSHPROPID_IsSharedItem, out isSharedItem)
            && (isSharedItem == getSharedItems))
        {
            itemIds.Add(itemid);
        }

        uint child;
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID.VSHPROPID_FirstChild, Unbox.AsUInt32, out child)
            && child != (uint)VSConstants.VSITEMID.Nil)
        {
            this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);

            while (HierarchyUtilities.TryGetHierarchyProperty(hier, child, (int)__VSHPROPID.VSHPROPID_NextSibling, Unbox.AsUInt32, out child)
                && child != (uint)VSConstants.VSITEMID.Nil)
            {
                this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);
            }
        }
    }
    ```

2. Nel `ShowMessageBox` metodo aggiungere il codice seguente per esaminare gli elementi della gerarchia del progetto di piattaforma. Inserirlo `foreach` all'interno del blocco.

    ```csharp
    output.OutputStringThreadSafe("Walk the active platform project:\n");
    var sharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ```

3. Leggere gli elementi condivisi. Gli elementi condivisi vengono visualizzati nel progetto della piattaforma come file collegati nascosti ed è possibile leggere tutte le proprietà come normali file collegati. Il codice seguente legge il percorso completo del primo elemento condiviso.

    ```csharp
    var sharedItemId = sharedItemIds[0];
    string fullPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));
    ```

4. Ora provalo. Premere **F5** per avviare l'istanza sperimentale. Creare un progetto di app dell'hub universale di C' nell'istanza sperimentale (nella finestra di dialogo **Nuovo progetto,** Visual **Cè** > **Windows** > **8** > **Universal** > **Hub App**) passare al menu **Strumenti** e fare clic su **Richiama TestUniversalProject**, quindi controllare il testo nel riquadro **Output** . Verrà visualizzata una schermata simile alla seguente:

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    Walk the active platform project:
        HubApp.WindowsPhone
            <HubApp.Shared>
                App.xaml
                    App.xaml.cs
                Assets
                    DarkGray.png
                    LightGray.png
                    MediumGray.png
                Common
                    NavigationHelper.cs
                    ObservableDictionary.cs
                    RelayCommand.cs
                    SuspensionManager.cs
                DataModel
                    SampleData.json
                    SampleDataSource.cs
                HubApp.Shared.projitems
                Strings
                    en-US
                        Resources.resw
            Assets
                HubBackground.theme-dark.png
                HubBackground.theme-light.png
                Logo.scale-240.png
                SmallLogo.scale-240.png
                SplashScreen.scale-240.png
                Square71x71Logo.scale-240.png
                StoreLogo.scale-240.png
                WideLogo.scale-240.png
            HubPage.xaml
                HubPage.xaml.cs
            ItemPage.xaml
                ItemPage.xaml.cs
            Package.appxmanifest
            Properties
                AssemblyInfo.cs
            References
                .NET for Windows Store apps
                HubApp.Shared
                Windows Phone 8.1
            SectionPage.xaml
                SectionPage.xaml.cs
    ```

### <a name="detect-changes-in-platform-projects-and-shared-projects"></a>Rilevare le modifiche nei progetti di piattaforma e nei progetti condivisi

1. È possibile utilizzare la gerarchia e gli eventi di progetto per rilevare le modifiche nei progetti condivisi, come per i progetti di piattaforma. Tuttavia, gli elementi di progetto nel progetto condiviso non sono visibili, il che significa che alcuni eventi non vengono attivati quando vengono modificati gli elementi di progetto condivisi.

    Si consideri la sequenza di eventi quando un file in un progetto viene rinominato:Consider the sequence of events when a file in a project is renamed:

   1. Il nome del file viene modificato sul disco.

   2. Il file di progetto viene aggiornato per includere il nuovo nome del file.

      Gli eventi della <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>gerarchia ( ad esempio, ) tengono in genere traccia delle modifiche visualizzate nell'interfaccia utente, come in **Esplora soluzioni**. Gli eventi di gerarchia considerano un'operazione di ridenominazione di file costituita da un'eliminazione di file e quindi da un'aggiunta di file. Tuttavia, quando gli elementi invisibili vengono <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> modificati, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> sistema di eventi della gerarchia genera un evento ma non un evento. Pertanto, se si rinomina un file in <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>un progetto di piattaforma, si ottengono entrambi <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>e , ma se si rinomina un file in un progetto condiviso, si ottiene solo .

      Per tenere traccia delle modifiche negli elementi di progetto, <xref:EnvDTE.ProjectItemsEventsClass>è possibile gestire gli eventi degli elementi di progetto DTE (quelli disponibili in ). Tuttavia, se si gestiscono un numero elevato di eventi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>è possibile ottenere prestazioni migliori gestendo gli eventi in . In questa procedura dettagliata vengono illustrati solo gli eventi della gerarchia e gli eventi DTE. In questa procedura si aggiunge un listener di eventi a un progetto condiviso e un progetto di piattaforma. Quindi, quando si rinomina un file in un progetto condiviso e un altro file in un progetto di piattaforma, è possibile visualizzare gli eventi che vengono generati per ogni operazione di ridenominazione.

      In questa procedura si aggiunge un listener di eventi a un progetto condiviso e un progetto di piattaforma. Quindi, quando si rinomina un file in un progetto condiviso e un altro file in un progetto di piattaforma, è possibile visualizzare gli eventi che vengono generati per ogni operazione di ridenominazione.

2. Aggiungere un listener di eventi. Aggiungere un nuovo file di classe al progetto e chiamarlo *HierarchyEventListener.cs*.

3. Aprire il file *di HierarchyEventListener.cs* e aggiungere le seguenti direttive using:

   ```csharp
   using Microsoft.VisualStudio.Shell.Interop;
   using Microsoft.VisualStudio;
   using System.IO;
   ```

4. Fare `HierarchyEventListener` in <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>modo che la classe implementi :

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   { }
   ```

5. Implementare i <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>membri di , come nel codice riportato di seguito.

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   {
       private IVsHierarchy hierarchy;
       IVsOutputWindowPane output;

       internal HierarchyEventListener(IVsHierarchy hierarchy, IVsOutputWindowPane outputWindow) {
            this.hierarchy = hierarchy;
            this.output = outputWindow;
       }

       int IVsHierarchyEvents.OnInvalidateIcon(IntPtr hIcon) {
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnInvalidateItems(uint itemIDParent) {
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemAdded(uint itemIDParent, uint itemIDSiblingPrev, uint itemIDAdded) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemAdded: " + itemIDAdded + "\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemDeleted(uint itemID) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemDeleted: " + itemID + "\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemsAppended(uint itemIDParent) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemsAppended\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnPropertyChanged(uint itemID, int propID, uint flags) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnPropertyChanged: item ID " + itemID + "\n");
           return VSConstants.S_OK;
       }
   }
   ```

6. Nella stessa classe aggiungere un altro <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>gestore eventi per l'evento DTE , che si verifica ogni volta che un elemento di progetto viene rinominato.

   ```csharp
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)
   {
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));
   }
   ```

7. Iscriviti agli eventi della gerarchia. Devi registrarti separatamente per ogni progetto che stai monitorando. Aggiungere il codice `ShowMessageBox`seguente in , uno per il progetto condiviso e l'altro per uno dei progetti di piattaforma.

   ```csharp
   // hook up the event listener for hierarchy events on the shared project
   HierarchyEventListener listener1 = new HierarchyEventListener(sharedHier, output);
   uint cookie1;
   sharedHier.AdviseHierarchyEvents(listener1, out cookie1);

   // hook up the event listener for hierarchy events on the
   active project
   HierarchyEventListener listener2 = new HierarchyEventListener(activePlatformHier, output);
   uint cookie2;
   activePlatformHier.AdviseHierarchyEvents(listener2, out cookie2);
   ```

8. Iscriversi all'evento <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>dell'elemento di progetto DTE . Aggiungere il codice seguente dopo aver collegato il secondo listener.

   ```csharp
   // hook up DTE events for project items
   Events2 dteEvents = (Events2)dte.Events;
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;
   ```

9. Modificare l'elemento condiviso. Non è possibile modificare gli elementi condivisi in un progetto di piattaforma; è invece necessario modificarli nel progetto condiviso che è il proprietario effettivo di questi elementi. È possibile ottenere l'ID elemento <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>corrispondente nel progetto condiviso con , assegnandogli il percorso completo dell'elemento condiviso. È quindi possibile modificare l'elemento condiviso. La modifica viene propagata ai progetti della piattaforma.

    > [!IMPORTANT]
    > È necessario scoprire se un elemento di progetto è un elemento condiviso prima di modificarlo.

     Il metodo seguente modifica il nome di un file di elemento di progetto.

    ```csharp
    private void ModifyFileNameInProject(IVsHierarchy project, string path)
    {
        int found;
        uint projectItemID;
        VSDOCUMENTPRIORITY[] priority = new VSDOCUMENTPRIORITY[1];
        if (ErrorHandler.Succeeded(((IVsProject)project).IsDocumentInProject(path, out found, priority, out projectItemID))
            && found != 0)
        {
            var name = DateTime.Now.Ticks.ToString() + Path.GetExtension(path);
            project.SetProperty(projectItemID, (int)__VSHPROPID.VSHPROPID_EditLabel, name);
            output.OutputStringThreadSafe(string.Format("Renamed {0} to {1}\n", path,name));
        }
    }
    ```

10. Chiamare questo metodo dopo tutto `ShowMessageBox` l'altro codice in per modificare il nome file dell'elemento nel progetto condiviso. Inserire questo dopo il codice che ottiene il percorso completo dell'elemento nel progetto condiviso.

    ```csharp
    // change the file name of an item in a shared project
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));
    this.ModifyFileNameInProject(sharedHier, fullPath);
    ```

11. Compilare ed eseguire il progetto. Creare un'app dell'hub universale di C' nell'istanza sperimentale, passare al menu **Strumenti** e fare clic su **Richiama TestUniversalProject**e controllare il testo nel riquadro di output generale. Il nome del primo elemento nel progetto condiviso (prevediamo che sia il file *App.xaml)* deve essere modificato e dovresti vedere che l'evento <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> è stato generato. In questo caso, poiché la ridenominazione di *App.xaml* causa anche la ridenominazione di *App.xaml.cs,* dovrebbero essere visualizzati quattro eventi (due per ogni progetto di piattaforma). Gli eventi DTE non tengono traccia degli elementi nel progetto condiviso. Dovrebbero essere <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> visualizzati due eventi (uno per <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> ognuno dei progetti di piattaforma), ma nessun evento.

12. A questo punto provare a rinominare un file in un progetto di piattaforma e si può vedere la differenza negli eventi che vengono generati. Aggiungere il codice `ShowMessageBox` seguente dopo `ModifyFileName`la chiamata a .

    ```csharp
    // change the file name of an item in a platform project
    var unsharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, unsharedItemIds, false, false);

    var unsharedItemId = unsharedItemIds[0];
    string unsharedPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(unsharedItemId, out unsharedPath));
    output.OutputStringThreadSafe(string.Format("Platform project item ID = {0}, full path = {1}\n", unsharedItemId, unsharedPath));

    this.ModifyFileNameInProject(activePlatformHier, unsharedPath);
    ```

13. Compilare ed eseguire il progetto. Creare un progetto universale di C, nell'istanza sperimentale, scegliere **Richiama TestUniversalProject**dal menu **Strumenti** e controllare il testo nel riquadro di output generale. Dopo che il file nel progetto di piattaforma <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> viene rinominato, verranno visualizzati sia un evento che un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> evento. Poiché la modifica del file non ha causato la modifica di altri file e poiché le modifiche apportate agli elementi in un progetto di piattaforma non vengono propagate da nessuna parte, esiste solo uno di questi eventi.
