---
title: Persistenza della proprietà di un Project item | Microsoft Docs
description: Informazioni su come rendere persistente una proprietà aggiunta a un elemento di progetto archiviando la proprietà nel file di progetto nel tipo di progetto esteso.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: how-to
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e201b60ea4634c6960d6e98c64214deadd62a6b7608cb73d15b71bf2a497254f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121305282"
---
# <a name="persist-the-property-of-a-project-item"></a>Rendere persistente la proprietà di un elemento di progetto
È possibile rendere persistente una proprietà aggiunta a un elemento di progetto, ad esempio l'autore di un file di origine. A tale scopo, archiviare la proprietà nel file di progetto.

 Il primo passaggio per rendere persistente una proprietà in un file di progetto consiste nell'ottenere la gerarchia del progetto come <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaccia. È possibile ottenere questa interfaccia tramite Automazione o <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> tramite . Dopo aver ottenuto l'interfaccia , è possibile usarla per determinare quale elemento di progetto è attualmente selezionato. Dopo aver creato l'ID dell'elemento di progetto, è possibile <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> usare per aggiungere la proprietà .

 Nelle procedure seguenti la proprietà *VsPkg.cs* viene mantenuta `Author` con il valore nel file di `Tom` progetto.

## <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>Per ottenere la gerarchia del progetto con l'oggetto DTE

1. Aggiungere il codice seguente al pacchetto VSPackage:

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

## <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Per rendere persistente la proprietà dell'elemento di progetto con l'oggetto DTE

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

## <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>Per ottenere la gerarchia del progetto usando IVsMonitorSelection

1. Aggiungere il codice seguente al pacchetto VSPackage:

    ```csharp
    IVsHierarchy hierarchy = null;
    IntPtr hierarchyPtr = IntPtr.Zero;
    IntPtr selectionContainer = IntPtr.Zero;
    uint itemid;

    // Retrieve shell interface in order to get current selection
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;
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

## <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Per rendere persistente la proprietà dell'elemento di progetto selezionato, data la gerarchia del progetto

1. Aggiungere il codice seguente al codice specificato nel metodo nella procedura precedente:

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

3. Usare un punto di interruzione o determinare in altro modo che il pacchetto VSPackage è caricato e che SetItemAttribute viene eseguito.

   > [!NOTE]
   > È possibile caricare automaticamente un VSPackage nel contesto dell'interfaccia <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid> utente. Per altre informazioni, vedere [Caricare pacchetti VSPackage.](../extensibility/loading-vspackages.md)

4. Chiudere [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e quindi aprire il file di progetto in Blocco note. Verrà visualizzato il \<Author> tag con il valore Tom, come indicato di seguito:

   ```xml
   <Compile Include="VsPkg.cs">
       <Author>Tom</Author>
   </Compile>
   ```

## <a name="see-also"></a>Vedi anche

- [Strumenti personalizzati](../extensibility/internals/custom-tools.md)
