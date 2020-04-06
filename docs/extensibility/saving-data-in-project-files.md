---
title: Salvataggio dei dati nei file di progetto Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5fd6cfaa450bc268665ae0f58109c99002da6152
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701351"
---
# <a name="save-data-in-project-files"></a>Salvare i dati nei file di progetto
Un sottotipo di progetto può salvare e recuperare dati specifici del sottotipo nel file di progetto. Il Framework di pacchetto gestito (MPF) fornisce due interfacce per eseguire questa attività:The Managed Package Framework (MPF) provides two interfaces to accomplish this task:

- L'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> consente di accedere ai valori delle proprietà dalla sezione **MSBuild** del file di progetto. I metodi <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> forniti da possono essere chiamati da qualsiasi utente ogni volta che l'utente deve caricare o salvare i dati correlati alla compilazione.

- L'oggetto <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> viene utilizzato per rendere persistenti i dati non correlati alla compilazione in formato XML in formato libero. I metodi <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> forniti da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vengono chiamati da ogni volta che è necessario rendere persistenti i dati non correlati alla compilazione nel file di progetto.

  Per altre informazioni su come rendere persistenti i dati relativi alla compilazione e alla compilazione, vedere Rendere persistenti i dati nel file di progetto MSBuild.For more information on how to persist build and non-build related data, see [Persist data in the MSBuild project file](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).

## <a name="save-and-retrieve-build-related-data"></a>Salvare e recuperare i dati correlati alla compilazioneSave and retrieve build related data

### <a name="to-save-a-build-related-data-in-the-project-file"></a>Per salvare i dati correlati a una compilazione nel file di progettoTo save a build related data in the project file

- Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> il metodo per salvare un percorso completo del file di progetto.

    ```
    private SpecializedProject project;
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;
    string newFullPath = GetNewFullPath();
    // Set a full path of the project file.
    ErrorHandler.ThrowOnFailure(projectStorage.SetPropertyValue(
        "MSBuildProjectDirectory",
        String.Empty,
        (uint)_PersistStorageType.PST_PROJECT_FILE, newFullPath));
    ```

### <a name="to-retrieve-build-related-data-from-the-project-file"></a>Per recuperare i dati correlati alla compilazione dal file di progettoTo retrieve build related data from the project file

- Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> il metodo per recuperare un percorso completo del file di progetto.

    ```
    private SpecializedProject project;
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;
    string fullPath;
    // Get a full path of the project file.
    ErrorHandler.ThrowOnFailure(projectStorage.GetPropertyValue(
        "MSBuildProjectDirectory",
        String.Empty,
        (uint)_PersistStorageType.PST_PROJECT_FILE, out fullPath));
    ```

## <a name="save-and-retrieve-non-build-related-data"></a>Salvare e recuperare dati non correlati alla compilazioneSave and retrieve non-build related data

### <a name="to-save-non-build-related-data-in-the-project-file"></a>Per salvare dati non correlati alla compilazione nel file di progettoTo save non-build related data in the project file

1. Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> il metodo per determinare se un frammento XML è stato modificato dall'ultimo salvataggio nel file corrente.

    ```
    public int IsFragmentDirty(uint storage, out int pfDirty)
    {
        pfDirty = 0;
        switch (storage)
        {
            case (uint)_PersistStorageType.PST_PROJECT_FILE:
            {
                if (isDirty)
                    pfDirty |= 1;
                break;
            }
            case (uint)_PersistStorageType.PST_USER_FILE:
            {
                // We do not store anything in the user file.
                break;
            }
        }

        // Forward the call to inner flavor(s)
        if (pfDirty == 0 && innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).IsFragmentDirty(storage, out pfDirty);

        return VSConstants.S_OK;

    }
    ```

2. Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> il metodo per salvare i dati XML nel file di progetto.

    ```
    public int Save(ref Guid guidFlavor, uint storage, out string pbstrXMLFragment, int fClearDirty)
    {
        pbstrXMLFragment = null;

        if (IsMyFlavorGuid(ref guidFlavor))
        {
            switch (storage)
            {
                case (uint)_PersistStorageType.PST_PROJECT_FILE:
                {
                    // Create XML for our data.
                    XmlDocument doc = new XmlDocument();
                    XmlNode root = doc.CreateElement(this.GetType().Name);

                    XmlNode node = doc.CreateElement(targetsTag);
                    node.AppendChild(doc.CreateTextNode(this.TargetsToExecute));
                    root.AppendChild(node);

                    node = doc.CreateElement(updateTargetsTag);
                    node.AppendChild(doc.CreateTextNode(this.UpdateTargetList.ToString()));
                    root.AppendChild(node);

                    doc.AppendChild(root);
                    // Get XML fragment representing our data
                    pbstrXMLFragment = doc.InnerXml;

                    if (fClearDirty != 0)
                        isDirty = false;
                    break;
                }
                case (uint)_PersistStorageType.PST_USER_FILE:
                {
                    // We do not store anything in the user file.
                    break;
                }
            }
        }

        // Forward the call to inner flavor(s)
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).Save(ref guidFlavor, storage, out pbstrXMLFragment, fClearDirty);

        return VSConstants.S_OK;
    }
    ```

### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>Per recuperare dati non correlati alla compilazione nel file di progettoTo retrieve non-build related data in the project file

1. Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> il metodo per inizializzare le proprietà di estensione del progetto e altri dati indipendenti dalla compilazione. Questo metodo viene chiamato se non sono presenti dati di configurazione XML nel file di progetto.

    ```
    public int InitNew(ref Guid guidFlavor, uint storage)
    {
        //Return,if it is our guid.
        if (IsMyFlavorGuid(ref guidFlavor))
            return VSConstants.S_OK;

        //Forward the call to inner flavor(s).
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).InitNew(ref guidFlavor, storage);

        return VSConstants.S_OK;
    ```

2. Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> il metodo per caricare i dati XML dal file di progetto.

    ```
    public int Load(ref Guid guidFlavor, uint storage, string pszXMLFragment)
    {
        if (IsMyFlavorGuid(ref guidFlavor))
        {
            switch (storage)
            {
                case (uint)_PersistStorageType.PST_PROJECT_FILE:
                {
                    // Load our data from the XML fragment.
                    XmlDocument doc = new XmlDocument();
                    XmlNode node = doc.CreateElement(this.GetType().Name);
                    node.InnerXml = pszXMLFragment;
                    if (node == null
                        || node.FirstChild == null
                        || node.FirstChild.ChildNodes.Count == 0
                        || node.FirstChild.ChildNodes[0].Name != targetsTag)
                        break;
                    this.TargetsToExecute = node.FirstChild.ChildNodes[0].InnerText;

                    if (node.FirstChild.ChildNodes.Count <= 1
                        || node.FirstChild.ChildNodes[1].Name != updateTargetsTag)
                        break;
                    this.UpdateTargetList = bool.Parse(node.FirstChild.ChildNodes[1].InnerText);
                    break;
                }
                case (uint)_PersistStorageType.PST_USER_FILE:
                {
                    // We do not store anything in the user file.
                    break;
                }
            }
        }

        // Forward the call to inner flavor(s)
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).Load(ref guidFlavor, storage, pszXMLFragment);

        return VSConstants.S_OK;
    }
    ```

> [!NOTE]
> Tutti gli esempi di codice forniti in questo argomento sono parti di un esempio più esaustivo negli [esempi VSSDK.](https://github.com/Microsoft/VSSDK-Extensibility-Samples)

## <a name="see-also"></a>Vedere anche
- [Rendere persistenti i dati nel file di progetto MSBuildPersist data in the MSBuild project file](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
