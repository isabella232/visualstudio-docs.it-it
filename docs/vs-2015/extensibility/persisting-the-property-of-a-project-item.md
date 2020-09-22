---
title: Salvataggio permanente della proprietà di un elemento di progetto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4adcf0f5c5770f5d3ffc0e0ed9bffdb108869c7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839516"
---
# <a name="persisting-the-property-of-a-project-item"></a>Salvataggio permanente della proprietà di un elemento di progetto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile che si desideri salvare in modo permanente una proprietà aggiunta a un elemento del progetto, ad esempio l'autore di un file di origine. Questa operazione può essere eseguita archiviando la proprietà nel file di progetto.  
  
 Il primo passaggio per salvare in modo permanente una proprietà in un file di progetto consiste nell'ottenere la gerarchia del progetto come <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaccia. È possibile ottenere questa interfaccia tramite l'automazione o tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> . Una volta ottenuta l'interfaccia, è possibile utilizzarla per determinare l'elemento del progetto attualmente selezionato. Una volta ottenuto l'ID dell'elemento del progetto, è possibile usare <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> per aggiungere la proprietà.  
  
 Nelle procedure seguenti viene resa permanente la proprietà VsPkg.cs `Author` con il valore `Tom` nel file di progetto.  
  
### <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>Per ottenere la gerarchia del progetto con l'oggetto DTE  
  
1. Aggiungere il codice seguente al pacchetto VSPackage:  
  
    ```csharp  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    ```  
  
### <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Per salvare in modo permanente la proprietà dell'elemento di progetto con l'oggetto DTE  
  
1. Aggiungere il codice seguente al codice specificato nel metodo nella procedura precedente:  
  
    ```csharp  
    IVsBuildPropertyStorage buildPropertyStorage =   
        hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath = (string)project.ProjectItems.Item(  
            "VsPkg.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");  
    }  
    ```  
  
### <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>Per ottenere la gerarchia del progetto utilizzando IVsMonitorSelection  
  
1. Aggiungere il codice seguente al pacchetto VSPackage:  
  
    ```csharp  
    IVsHierarchy hierarchy = null;  
    IntPtr hierarchyPtr = IntPtr.Zero;  
    IntPtr selectionContainer = IntPtr.Zero;  
    uint itemid;  
  
    // Retrieve shell interface in order to get current selection  
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;  
    if (monitorSelection == null)  
        throw new InvalidOperationException();  
  
    try  
    {  
        // Get the current project hierarchy, project item, and selection container for the current selection  
        // If the selection spans multiple hierachies, hierarchyPtr is Zero  
        IVsMultiItemSelect multiItemSelect = null;  
        ErrorHandler.ThrowOnFailure(  
            monitorSelection.GetCurrentSelection(  
                out hierarchyPtr, out itemid,   
                out multiItemSelect, out selectionContainer));  
  
        // We only care if there is only one node selected in the tree  
        if (!(itemid == VSConstants.VSITEMID_NIL ||   
            hierarchyPtr == IntPtr.Zero ||  
            multiItemSelect != null ||  
            itemid == VSConstants.VSITEMID_SELECTION))  
        {  
            hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr)  
                as IVsHierarchy;  
        }  
    }  
    finally  
    {  
        if (hierarchyPtr != IntPtr.Zero)  
            Marshal.Release(hierarchyPtr);  
        if (selectionContainer != IntPtr.Zero)  
            Marshal.Release(selectionContainer);  
    }  
    ```  
  
2. 
  
### <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Per salvare in modo permanente la proprietà dell'elemento di progetto selezionata, data la gerarchia del progetto  
  
1. Aggiungere il codice seguente al codice specificato nel metodo nella procedura precedente:  
  
    ```  
    IVsBuildPropertyStorage buildPropertyStorage =   
        hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");  
    }  
    ```  
  
### <a name="to-verify-that-the-property-is-persisted"></a>Per verificare che la proprietà sia permanente  
  
1. Avviare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e quindi aprire o creare una soluzione.  
  
2. Selezionare l'elemento del progetto VsPkg.cs in **Esplora soluzioni**.  
  
3. Usare un punto di interruzione o determinare in altro modo che il pacchetto VSPackage sia caricato e che SetItemAttribute sia in esecuzione.  
  
    > [!NOTE]
    > È possibile autocaricare un pacchetto VSPackage nel contesto dell'interfaccia utente <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid> . Per altre informazioni, vedere [caricamento dei pacchetti VSPackage](../extensibility/loading-vspackages.md).  
  
4. Chiudere [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e aprire il file di progetto nel blocco note. Il \<Author> tag dovrebbe essere visualizzato con il valore Tom, come indicato di seguito:  
  
    ```  
    <Compile Include="VsPkg.cs">  
        <Author>Tom</Author>  
    </Compile>  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti personalizzati](../extensibility/internals/custom-tools.md)
