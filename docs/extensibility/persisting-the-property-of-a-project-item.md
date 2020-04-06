---
title: Persistenza della proprietà di un elemento di progetto Documenti Microsoft
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15c280f15436a5e27bcc0dcc4d2fb9e9bdd82933
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702214"
---
# <a name="persist-the-property-of-a-project-item"></a>Rendere persistente la proprietà di un elemento di progettoPersist the property of a project item
È possibile rendere persistente una proprietà aggiunta a un elemento di progetto, ad esempio l'autore di un file di origine. A tale scopo, è possibile archiviare la proprietà nel file di progetto.

 Il primo passaggio per rendere persistente una proprietà in un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> file di progetto consiste nell'ottenere la gerarchia del progetto come interfaccia. È possibile ottenere questa interfaccia utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>l'automazione o utilizzando . Una volta ottenuta l'interfaccia, è possibile utilizzarla per determinare quale elemento di progetto è attualmente selezionato. Una volta che si dispone dell'ID dell'elemento di progetto, è possibile utilizzare <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> per aggiungere la proprietà.

 Nelle procedure seguenti, la *VsPkg.cs* proprietà `Author` VsPkg.cs `Tom` viene mantenuta con il valore nel file di progetto.

## <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>Per ottenere la gerarchia del progetto con l'oggetto DTE

1. Aggiungere il codice seguente al pacchetto VSPackage:Add the following code to your VSPackage:

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

## <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Per rendere persistente la proprietà dell'elemento di progetto con l'oggetto DTETo persist the project item property with the DTE object

1. Aggiungere il codice seguente al codice specificato nel metodo della procedura precedente:

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

## <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>Per ottenere la gerarchia del progetto utilizzando IVsMonitorSelectionTo obtain the project hierarchy using IVsMonitorSelection

1. Aggiungere il codice seguente al pacchetto VSPackage:Add the following code to your VSPackage:

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

## <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Per rendere persistente la proprietà dell'elemento di progetto selezionato, data la gerarchia del progettoTo persist the selected project item property, given the project hierarchy

1. Aggiungere il codice seguente al codice specificato nel metodo della procedura precedente:

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-verify-that-the-property-is-persisted"></a>Per verificare che la proprietà sia persistente

1. Avviare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e quindi aprire o creare una soluzione.

2. Selezionare l'elemento di progetto VsPkg.cs in **Esplora soluzioni**.

3. Utilizzare un punto di interruzione o determinare in altro modo che il pacchetto VSPackage viene caricato e che SetItemAttribute viene eseguito.

   > [!NOTE]
   > È possibile caricare automaticamente un pacchetto <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>VSPackage nel contesto dell'interfaccia utente. Per ulteriori informazioni, vedere [Caricare VSPackage](../extensibility/loading-vspackages.md).

4. Chiudere [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e aprire il file di progetto nel Blocco note. Verrà visualizzato \<il tag Author> con il valore Tom, come indicato di seguito:You should see the Author> tag with the value Tom, as follows:

   ```xml
   <Compile Include="VsPkg.cs">
       <Author>Tom</Author>
   </Compile>
   ```

## <a name="see-also"></a>Vedere anche

- [Strumenti personalizzati](../extensibility/internals/custom-tools.md)
