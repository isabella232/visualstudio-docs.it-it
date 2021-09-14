---
title: Gestione dei Windows universali | Microsoft Docs
description: Per supportare le Windows universali, le Visual Studio che gestiscono i progetti devono essere consapevoli della struttura del progetto di app Windows universali.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d6e34a8cb8da8158eae9e6c245da45fa37d59b4e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709457"
---
# <a name="manage-universal-windows-projects"></a>Gestire i progetti Windows universali

Le Windows universali sono app che hanno come destinazione sia Windows 8.1 che Windows Phone 8.1, consentendo agli sviluppatori di usare codice e altri asset in entrambe le piattaforme. Il codice e le risorse condivise vengono mantenuti in un progetto condiviso, mentre il codice e le risorse specifici della piattaforma vengono mantenuti in progetti separati, uno per Windows e l'altro per Windows Phone. Per altre informazioni sulle app Windows universali, vedere [App Windows universali](/windows/uwp/get-started/create-uwp-apps). Visual Studio che gestiscono i progetti devono essere consapevoli del fatto che i progetti di app Windows universali hanno una struttura diversa dalle app a piattaforma singola. Questa procedura dettagliata illustra come esplorare il progetto condiviso e gestire gli elementi condivisi.

## <a name="prerequisites"></a>Prerequisiti

A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

### <a name="navigate-the-shared-project"></a>Esplorare il progetto condiviso

1. Creare un progetto VSIX C# **denominato TestUniversalProject**. (**File**  >  **Nuovo**  >  **Project** e quindi **C#**  >  **Extensibility**  >  **Visual Studio Package**). Aggiungere un **modello di** elemento di progetto Comando personalizzato (nel **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi** nuovo elemento , quindi passare  >  a **Estendibilità**. Assegnare al file il nome **TestUniversalProject**.

2. Aggiungere un riferimento a *Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll* *eMicrosoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll* (nella **sezione** Estensioni).

3. Aprire *TestUniversalProject.cs* e aggiungere le `using` direttive seguenti:

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

4. Nella classe `TestUniversalProject` aggiungere un campo privato che punta alla finestra **Output.**

    ```csharp
    public sealed class TestUniversalProject
    {
        IVsOutputWindowPane output;
    . . .
    }
    ```

5. Impostare il riferimento al riquadro di output all'interno del costruttore TestUniversalProject:

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

6. Rimuovere il codice esistente dal `ShowMessageBox` metodo :

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
    }
    ```

7. Ottenere l'oggetto DTE, che verrà utilizzato per diversi scopi in questa procedura dettagliata. Assicurarsi inoltre che una soluzione sia caricata quando si fa clic sul pulsante di menu.

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

8. Trovare il progetto condiviso. Il progetto condiviso è un contenitore puro. non compila né produce output. Il metodo seguente trova il primo progetto condiviso nella soluzione cercando <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> l'oggetto con la funzionalità del progetto condiviso.

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

9. Nel metodo restituisce la didascalia (il nome del progetto visualizzato nella Esplora soluzioni `ShowMessageBox` ) del progetto condiviso. 

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

10. Ottenere il progetto di piattaforma attivo. I progetti di piattaforma sono i progetti che contengono risorse e codice specifici della piattaforma. Il metodo seguente usa il nuovo campo <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy> per ottenere il progetto di piattaforma attivo.

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

11. Nel metodo `ShowMessageBox` restituisce la didascalia del progetto di piattaforma attivo.

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
    > Se l'utente ha aperto un progetto di app Windows universale C++ nell'istanza sperimentale, il codice precedente genera un'eccezione. Questo è un problema noto Per evitare l'eccezione, sostituire il `foreach` blocco precedente con il codice seguente:

    ```csharp
    var importingProjects = sharedAssetsProject.EnumImportingProjects();
    for (int i = 0; i < importingProjects.Count; ++i)
    {
        yield return importingProjects[i];
    }
    ```

13. Nel metodo `ShowMessageBox` restituisce la didascalia di ogni progetto di piattaforma. Inserire il codice seguente dopo la riga che restituisce la didascalia del progetto di piattaforma attivo. In questo elenco vengono visualizzati solo i progetti di piattaforma caricati.

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

14. Modificare il progetto di piattaforma attivo. Il metodo seguente imposta il progetto attivo usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A> .

    ```csharp
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)
    {
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);
    }
    ```

15. Nel metodo `ShowMessageBox` modificare il progetto di piattaforma attivo. Inserire questo codice all'interno del `foreach` blocco .

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

16. Provare a questo punto. Premere F5 per avviare l'istanza sperimentale. Creare un progetto di app dell'hub universale C# nell'istanza sperimentale (nella finestra di dialogo Nuovo **Project** **Visual C#**  >  **Windows**  >  **Windows 8**  >  **App hub**  >  **universale**). Dopo aver caricato la soluzione, passare al **menu** Strumenti e fare clic su **Richiama TestUniversalProject** e quindi controllare il testo nel **riquadro Output.** Verrà visualizzata una schermata simile alla seguente:

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    ```

### <a name="manage-the-shared-items-in-the-platform-project"></a>Gestire gli elementi condivisi nel progetto di piattaforma

1. Trovare gli elementi condivisi nel progetto della piattaforma. Gli elementi nel progetto condiviso vengono visualizzati nel progetto della piattaforma come elementi condivisi. Non è possibile visualizzare i progetti nella Esplora soluzioni **,** ma è possibile eseguire una ricerca nella gerarchia del progetto. Il metodo seguente illustra la gerarchia e raccoglie tutti gli elementi condivisi. Restituisce facoltativamente la didascalia di ogni elemento. Gli elementi condivisi sono identificati dalla nuova proprietà <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_IsSharedItem> .

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

2. Nel metodo aggiungere il codice seguente per visualizzare gli elementi della gerarchia `ShowMessageBox` del progetto della piattaforma. Inserirlo all'interno del `foreach` blocco .

    ```csharp
    output.OutputStringThreadSafe("Walk the active platform project:\n");
    var sharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ```

3. Leggere gli elementi condivisi. Gli elementi condivisi vengono visualizzati nel progetto della piattaforma come file collegati nascosti ed è possibile leggere tutte le proprietà come file collegati ordinari. Il codice seguente legge il percorso completo del primo elemento condiviso.

    ```csharp
    var sharedItemId = sharedItemIds[0];
    string fullPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));
    ```

4. Provare a questo punto. Premere **F5 per** avviare l'istanza sperimentale. Creare un progetto di app dell'hub universale C# nell'istanza sperimentale (nella finestra di dialogo Nuovo **Project** **Visual C#** Windows Windows 8 App hub universale ) passare al menu Strumenti e fare clic su  >    >    >    >   **Richiama TestUniversalProject** e   quindi controllare il testo nel riquadro Output. Verrà visualizzata una schermata simile alla seguente:

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

1. È possibile usare gli eventi di gerarchia e di progetto per rilevare le modifiche nei progetti condivisi, proprio come per i progetti di piattaforma. Tuttavia, gli elementi di progetto nel progetto condiviso non sono visibili, il che significa che determinati eventi non vengono generati quando vengono modificati gli elementi di progetto condivisi.

    Si consideri la sequenza di eventi quando un file in un progetto viene rinominato:

   1. Il nome del file viene modificato su disco.

   2. Il file di progetto viene aggiornato per includere il nuovo nome del file.

      Gli eventi di gerarchia ,ad esempio , in genere rilevano le modifiche visualizzate nell'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> utente, come nel **Esplora soluzioni**. Gli eventi di gerarchia considerano un'operazione di ridenominazione di file costituita da un'eliminazione di file e quindi da un'aggiunta di file. Tuttavia, quando vengono modificati elementi invisibili, il sistema di eventi della gerarchia genera un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> evento ma non un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> evento. Pertanto, se si rinomina un file in un progetto di piattaforma, si ottengono entrambi e , ma se si rinomina un file in un progetto condiviso, si <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> ottiene solo <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> .

      Per tenere traccia delle modifiche negli elementi di progetto, è possibile gestire gli eventi degli elementi di progetto DTE (quelli trovati in <xref:EnvDTE.ProjectItemsEventsClass> ). Tuttavia, se si gestisce un numero elevato di eventi, è possibile ottenere prestazioni migliori per la gestione degli eventi in <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> . In questa procedura dettagliata vengono visualizzati solo gli eventi della gerarchia e gli eventi DTE. In questa procedura si aggiunge un listener di eventi a un progetto condiviso e a un progetto di piattaforma. Quindi, quando si rinomina un file in un progetto condiviso e un altro file in un progetto di piattaforma, è possibile visualizzare gli eventi generati per ogni operazione di ridenominazione.

      In questa procedura si aggiunge un listener di eventi a un progetto condiviso e a un progetto di piattaforma. Quindi, quando si rinomina un file in un progetto condiviso e un altro file in un progetto di piattaforma, è possibile visualizzare gli eventi generati per ogni operazione di ridenominazione.

2. Aggiungere un listener di eventi. Aggiungere un nuovo file di classe al progetto e chiamarlo *HierarchyEventListener.cs*.

3. Aprire il file *HierarchyEventListener.cs* e aggiungere le direttive using seguenti:

   ```csharp
   using Microsoft.VisualStudio.Shell.Interop;
   using Microsoft.VisualStudio;
   using System.IO;
   ```

4. Fare in modo `HierarchyEventListener` che la classe <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> implementi :

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   { }
   ```

5. Implementare i membri di <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> , come nel codice seguente.

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

6. Nella stessa classe aggiungere un altro gestore eventi per l'evento DTE , che si verifica <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> ogni volta che un elemento di progetto viene rinominato.

   ```csharp
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)
   {
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));
   }
   ```

7. Iscriversi per gli eventi della gerarchia. È necessario iscriversi separatamente per ogni progetto di cui si sta tracciando. Aggiungere il codice seguente in `ShowMessageBox` , uno per il progetto condiviso e l'altro per uno dei progetti della piattaforma.

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

8. Iscriversi all'evento dell'elemento di progetto DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> . Aggiungere il codice seguente dopo aver collegato il secondo listener.

   ```csharp
   // hook up DTE events for project items
   Events2 dteEvents = (Events2)dte.Events;
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;
   ```

9. Modificare l'elemento condiviso. Non è possibile modificare gli elementi condivisi in un progetto di piattaforma. è invece necessario modificarli nel progetto condiviso che è il proprietario effettivo di questi elementi. È possibile ottenere l'ID elemento corrispondente nel progetto condiviso con , fornendogli il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> percorso completo dell'elemento condiviso. È quindi possibile modificare l'elemento condiviso. La modifica viene propagata ai progetti della piattaforma.

    > [!IMPORTANT]
    > È necessario verificare se un elemento di progetto è un elemento condiviso prima di modificarlo.

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

10. Chiamare questo metodo dopo tutto il codice in `ShowMessageBox` per modificare il nome file dell'elemento nel progetto condiviso. Inserire questo valore dopo il codice che ottiene il percorso completo dell'elemento nel progetto condiviso.

    ```csharp
    // change the file name of an item in a shared project
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));
    this.ModifyFileNameInProject(sharedHier, fullPath);
    ```

11. Compilare ed eseguire il progetto. Creare un'app dell'hub universale C# nell'istanza sperimentale, passare al **menu** Strumenti e fare clic su **Richiama TestUniversalProject** e controllare il testo nel riquadro di output generale. Il nome del primo elemento nel progetto condiviso (si prevede che sia il file *App.xaml)* deve essere modificato e si dovrebbe vedere che l'evento è <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> stato generato. In questo caso, poiché la ridenominazione di *App.xaml* comporta anche la ridenominazione di *App.xaml.cs,* dovrebbero essere visualizzati quattro eventi (due per ogni progetto di piattaforma). Gli eventi DTE non tiene traccia degli elementi nel progetto condiviso. Dovrebbero essere visualizzati due <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> eventi (uno per ogni progetto di piattaforma), ma nessun <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> evento.

12. Provare ora a rinominare un file in un progetto di piattaforma ed è possibile vedere la differenza negli eventi generati. Aggiungere il codice seguente in `ShowMessageBox` dopo la chiamata a `ModifyFileName` .

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

13. Compilare ed eseguire il progetto. Creare un Project universale C# nell'istanza sperimentale, passare al **menu** Strumenti e fare clic su **Richiama TestUniversalProject** e controllare il testo nel riquadro di output generale. Dopo la ridenominazione del file nel progetto della piattaforma, dovrebbero essere visualizzati sia un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> evento che un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> evento. Poiché la modifica del file non ha causato la modifica di altri file e poiché le modifiche agli elementi in un progetto di piattaforma non vengono propagate da nessuna parte, è presente solo uno di questi eventi.