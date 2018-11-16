---
title: Gestione di progetti Windows universali | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b2c10232b917e8343ace8d1a31fcd3609ecdfb95
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783779"
---
# <a name="managing-universal-windows-projects"></a>Gestione di progetti Windows universale
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le app Windows universali sono le app destinate a Windows 8.1 e Windows Phone 8.1, consentendo agli sviluppatori di utilizzare il codice e altri asset su entrambe le piattaforme. Il codice condiviso e le risorse vengono mantenute in un progetto condiviso, mentre il codice specifico della piattaforma e le risorse vengono mantenute in progetti separati, uno per Windows e l'altro per Windows Phone. Per altre informazioni sulle App Windows universali, vedere [le app Windows universali](http://msdn.microsoft.com/library/windows/apps/dn609832.aspx). Estensioni di Visual Studio che gestiscono i progetti devono essere consapevoli che i progetti di app universali di Windows dispongono di una struttura che differisce dalle App a singola piattaforma. Questa procedura dettagliata illustra come spostare il progetto condiviso e gestire gli elementi condivisi.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="navigate-the-shared-project"></a>Passare al progetto condiviso  
  
1.  Creare un progetto VSIX c# denominato **TestUniversalProject**. (**File, nuovo, progetto** e quindi **il pacchetto di Visual Studio c#, estendibilità,**). Aggiungi un **comando personalizzato** modello di elemento di progetto (in Esplora soluzioni fare doppio clic sul nodo del progetto e selezionare **Aggiungi / nuovo elemento**, quindi passare a **estendibilità**). Denominare il file **TestUniversalProject**.  
  
2.  Aggiungere un riferimento a Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll e Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll (nelle **estensioni** sezione).  
  
3.  Aprire TestUniversalProject.cs e aggiungere il codice seguente `using` istruzioni:  
  
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
  
4.  Nella classe TestUniversalProject aggiungere un campo privato che punta al **Output** finestra.  
  
    ```csharp  
    public sealed class TestUniversalProject   
    {  
        IVsOutputWindowPane output;  
    . . .  
    }  
    ```  
  
5.  Impostare il riferimento al riquadro di output all'interno di TestUniversalProject costruttore:  
  
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
  
6.  Rimuovere il codice esistente dal `ShowMessageBox` metodo:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)   
    {  
    }  
    ```  
  
7.  Ottiene l'oggetto DTE, che verrà usato per scopi diversi in questa procedura dettagliata. Assicurarsi inoltre che viene caricata una soluzione quando si fa clic sul pulsante di menu.  
  
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
  
8.  Trovare il progetto condiviso. Progetto condiviso è un contenitore puro; non creare o generare output. Il metodo seguente consente di trovare il primo progetto condiviso nella soluzione cercando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oggetto che è in grado di progetto condiviso.  
  
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
  
9. Nel `ShowMessageBox` metodo, la didascalia di output (il nome del progetto visualizzato nei **Esplora soluzioni**) del progetto condiviso.  
  
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
  
10. Ottenere il progetto di piattaforma attiva. I progetti della piattaforma sono i progetti che contengono le risorse e codice specifico della piattaforma. Il metodo seguente usa il nuovo campo <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7> per ottenere il progetto di piattaforma attiva.  
  
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
  
11. Nel `ShowMessageBox` metodo, la didascalia del progetto di piattaforma attiva di output.  
  
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
  
12. Eseguire l'iterazione attraverso i progetti di piattaforma. Il metodo seguente ottiene tutti i progetti (piattaforma) importazione dal progetto condiviso.  
  
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
    >  Se l'utente ha aperto un progetto di app Windows universale C++ nell'istanza sperimentale, il codice precedente genera un'eccezione. Si tratta di un problema noto. Per evitare l'eccezione, sostituire il `foreach` blocco sopra con il codice seguente:  
  
    ```csharp  
    var importingProjects = sharedAssetsProject.EnumImportingProjects();  
    for (int i = 0; i < importingProjects.Count; ++i)  
    {  
        yield return importingProjects[i];  
    }   
    ```  
  
13. Nel `ShowMessageBox` metodo, la didascalia di ogni progetto della piattaforma di output. Inserire il codice seguente dopo la riga che genera la didascalia del progetto di piattaforma attiva. In questo elenco vengono visualizzati solo i progetti di piattaforma che vengono caricati.  
  
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
  
14. Modificare il progetto di piattaforma attiva. Il metodo seguente imposta il progetto attivo usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>.  
  
    ```csharp  
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)  
    {  
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);  
    }  
    ```  
  
15. Nel `ShowMessageBox` metodo, modificare il progetto della piattaforma attiva. Inserire questo codice all'interno di `foreach` blocco.  
  
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
  
16. Provare ora a eseguire l'operazione. Premere F5 per avviare l'istanza sperimentale. Creare un progetto di app universali hub c# nell'istanza sperimentale (nelle **nuovo progetto** della finestra di dialogo **Visual c# / Windows / Windows 8 / universale / App Hub**). Dopo il caricamento della soluzione, passare al **strumenti** menu e fare clic su **TestUniversalProject richiamare**, quindi selezionare il testo nel **Output** riquadro. Il risultato dovrebbe essere simile al seguente:  
  
    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    ```  
  
### <a name="manage-the-shared-items-in-the-platform-project"></a>Gestire gli elementi condivisi nel progetto di piattaforma  
  
1.  Trovare gli elementi condivisi nel progetto di piattaforma. Gli elementi nel progetto condiviso vengono visualizzati nel progetto di piattaforma come elementi condivisi. Non è possibile visualizzarli nella **Esplora soluzioni**, ma è possibile seguire la gerarchia di progetto per trovarli. Il metodo seguente illustra la gerarchia e raccoglie tutti gli elementi condivisi. Facoltativamente, restituisce la didascalia di ciascun elemento. Gli elementi condivisi sono identificati dalla proprietà nuova <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7>.  
  
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
  
2.  Nel `ShowMessageBox` metodo, aggiungere il codice seguente per esaminare gli elementi di gerarchia del progetto di piattaforma. Inserirlo all'interno di `foreach` blocco.  
  
    ```csharp  
    output.OutputStringThreadSafe("Walk the active platform project:\n");  
    var sharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ```  
  
3.  Leggere gli elementi condivisi. Gli elementi condivisi vengono visualizzati nel progetto di piattaforma come i file collegati nascosti, e può leggere tutte le proprietà come normali file collegati. Il codice seguente legge il percorso completo del primo elemento condiviso.  
  
    ```csharp  
    var sharedItemId = sharedItemIds[0];  
    string fullPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));  
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));  
    ```  
  
4.  Provare ora a eseguire l'operazione. Premere F5 per avviare l'istanza sperimentale. Creare un progetto di app universali hub c# nell'istanza sperimentale (nelle **nuovo progetto** nella finestra di dialogo **Visual c# / Windows / Windows 8 / universale / App Hub**) andare alla **strumenti** menu e scegliere **richiamare TestUniversalProject**, quindi selezionare il testo nel **Output** riquadro. Il risultato dovrebbe essere simile al seguente:  
  
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
  
### <a name="detecting-changes-in-platform-projects-and-shared-projects"></a>Rilevamento delle modifiche nei progetti di piattaforma e condivisi  
  
1. È possibile utilizzare gli eventi di gerarchia e di progetto per rilevare le modifiche in progetti condivisi, proprio come per i progetti di piattaforma. Tuttavia, gli elementi del progetto nel progetto condiviso non sono visibili, il che significa che alcuni eventi non vengono attivati quando vengono modificati gli elementi di progetto condiviso.  
  
    Prendere in considerazione la sequenza di eventi quando viene rinominato un file in un progetto:  
  
   1. Il nome del file viene modificato sul disco.  
  
   2. Il file di progetto viene aggiornato per includere il nuovo nome del file.  
  
      Gli eventi di gerarchia (ad esempio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>) a livello generale tenere traccia delle modifiche visualizzate nell'interfaccia utente, come nel **Esplora soluzioni**. Gli eventi di gerarchia di prendere in considerazione un'operazione di ridenominazione di file composta da un'operazione di eliminazione di file e quindi un'aggiunta di file. Tuttavia, quando vengono modificati gli articoli invisibili, il sistema di eventi di gerarchia viene attivato un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> evento, ma non un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> evento. Di conseguenza, se si rinomina un file in un progetto di piattaforma, si otterrà entrambe <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>, ma se si rinomina un file in un progetto condiviso, viene visualizzato solo <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>.  
  
      Per tenere traccia delle modifiche negli elementi di progetto, è possibile gestire gli eventi dell'elemento progetto DTE (quelli disponibili in <xref:EnvDTE.ProjectItemsEventsClass>). Tuttavia, se si sta gestendo un numero elevato di eventi, è possibile ottenere prestazioni migliori che gestisce gli eventi in <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>. In questa procedura dettagliata verrà illustrato solo gli eventi di gerarchia e gli eventi DTE. In questa procedura aggiungere un listener di eventi per un progetto condiviso e un progetto di piattaforma. Quindi, quando si rinomina un file in un progetto condiviso e un altro file in un progetto di piattaforma, è possibile visualizzare gli eventi che vengono generati per ogni operazione di ridenominazione.  
  
      In questa procedura aggiungere un listener di eventi per un progetto condiviso e un progetto di piattaforma. Quindi, quando si rinomina un file in un progetto condiviso e un altro file in un progetto di piattaforma, è possibile visualizzare gli eventi che vengono generati per ogni operazione di ridenominazione.  
  
2. Aggiungere un listener di eventi. Aggiungere un nuovo file di classe al progetto e chiamarlo HierarchyEventListener.cs.  
  
3. Aprire il file HierarchyEventListener.cs e aggiungere quanto segue usando istruzioni:  
  
   ```csharp  
   using Microsoft.VisualStudio.Shell.Interop;  
   using Microsoft.VisualStudio;  
   using System.IO;  
  
   ```  
  
4. Disporre le `HierarchyEventListener` implementano <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>:  
  
   ```csharp  
   class HierarchyEventListener : IVsHierarchyEvents  
   { }  
  
   ```  
  
5. Implementare i membri di <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>, come nel codice riportato di seguito.  
  
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
  
6. Nella stessa classe aggiungere un altro gestore eventi per l'evento DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>, che si verifica ogni volta che viene rinominato un elemento del progetto.  
  
   ```csharp  
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)  
   {  
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",  
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));  
   }  
   ```  
  
7. Effettuare l'iscrizione per gli eventi di gerarchia. È necessario iscriversi separatamente per ogni progetto che si esegue il monitoraggio. Aggiungere il codice seguente in `ShowMessageBox`, uno per il progetto condiviso e l'altro per uno dei progetti di piattaforma.  
  
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
  
8. Effettuare l'iscrizione per l'evento di elemento di progetto DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>. Aggiungere il codice seguente dopo che collegherà il secondo listener.  
  
   ```csharp  
   // hook up DTE events for project items  
   Events2 dteEvents = (Events2)dte.Events;  
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;  
  
   ```  
  
9. Modificare l'elemento condiviso. Non è possibile modificare gli elementi condivisi in un progetto di piattaforma. In alternativa, è necessario modificarli nel progetto condiviso che è il titolare effettivo di questi elementi. È possibile ottenere l'ID dell'elemento corrispondente nel progetto condiviso con <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>, fornendo il percorso completo dell'elemento condiviso. È quindi possibile modificare l'elemento condiviso. La modifica viene propagata per i progetti di piattaforma.  
  
    > [!IMPORTANT]
    >  È necessario trovare o meno un elemento del progetto è un elemento condiviso prima della modifica.  
  
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
  
10. Chiamare questo metodo dopo tutto l'altro codice in `ShowMessageBox` per modificare il nome del file l'elemento nel progetto condiviso. Inserire questo dopo il codice che ottiene il percorso completo dell'elemento nel progetto condiviso.  
  
    ```csharp  
    // change the file name of an item in a shared project  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));   
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));  
    this.ModifyFileNameInProject(sharedHier, fullPath);  
    ```  
  
11. Compilare ed eseguire il progetto. Creare un'app universale hub c# nell'istanza sperimentale, passare al **degli strumenti** menu e fare clic su **richiamare TestUniversalProject**e controllare il testo nel riquadro di output generale. Il nome del primo elemento condiviso progetto (si presume che sia il file app. XAML) deve essere modificato e verificare che il <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> ha generato l'evento. In questo caso, poiché la ridenominazione di App. XAML provoca App.xaml.cs da rinominare anche, dovrebbe essere quattro eventi (due per ogni progetto della piattaforma). (Gli eventi DTE non rilevare gli elementi nel progetto condiviso). Si dovrebbe visualizzare due <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> eventi (uno per ognuno dei progetti di piattaforma), ma non <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> gli eventi.  
  
12. Ora provare a rinominare un file in un progetto di piattaforma ed è possibile visualizzare la differenza tra gli eventi che vengono generate. Aggiungere il codice seguente nel `ShowMessageBox` dopo la chiamata a `ModifyFileName`.  
  
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
  
13. Compilare ed eseguire il progetto. Creare un progetto universale c# nell'istanza sperimentale, passare al **degli strumenti** menu e fare clic su **richiamare TestUniversalProject**e controllare il testo nel riquadro di output generale. Dopo la ridenominazione di file nel progetto di piattaforma, dovrebbe essere sia un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> eventi e un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> evento. Dopo aver modificato il file non causato da nessun altro file da modificare e poiché le modifiche agli elementi in un progetto di piattaforma non vengono propagate in qualsiasi punto, è solo uno di questi eventi.

