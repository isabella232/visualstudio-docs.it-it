---
title: Salvataggio dei dati nei file di progetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 53e227b2fdf97c406a86b31cee2a3c450948ee6b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434785"
---
# <a name="save-data-in-project-files"></a>Salvare i dati nei file di progetto
Un sottotipo di progetto è possibile salvare e recuperare i dati specifici del sottotipo nel file di progetto. Il Framework di pacchetto gestito (MPF) sono disponibili due interfacce per portare a termine questa attività:

- Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> interfaccia consente ai valori delle proprietà di accesso dal **MSBuild** sezione del file di progetto. I metodi forniti da <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> può essere chiamato da qualsiasi utente ogni volta che l'utente dovrà di caricamento o salvataggio compila i dati correlati.

- Il <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> viene usato per rendere persistenti i dati correlati-build non in XML Freeform. I metodi forniti dalla <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> vengono chiamati dal [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ogni volta che [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] deve rendere persistenti i dati correlati di non compilazione nel file di progetto.

  Per altre informazioni su come mantenere build e i dati correlati non-build, vedere [rendere persistenti i dati nel file di progetto MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).

## <a name="save-and-retrieve-build-related-data"></a>Salvare e recuperare i dati correlati di compilazione

### <a name="to-save-a-build-related-data-in-the-project-file"></a>Per salvare una compilazione correlati i dati nel file di progetto

- Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> metodo per salvare un percorso completo del file di progetto.

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

### <a name="to-retrieve-build-related-data-from-the-project-file"></a>Per build di recuperare i dati correlati dal file di progetto

- Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> metodo per recuperare un percorso completo del file di progetto.

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

## <a name="save-and-retrieve-non-build-related-data"></a>Salvare e recuperare i dati correlati non-build

### <a name="to-save-non-build-related-data-in-the-project-file"></a>Per salvare-build non correlati i dati nel file di progetto

1. Implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> metodo per determinare se un frammento XML è stato modificato dall'ultimo salvato nel relativo file corrente.

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

2. Implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> metodo per salvare i dati XML nel file di progetto.

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

### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>Per recuperare i dati correlati di non compilazione nel file di progetto

1. Implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> metodo per inizializzare le proprietà di estensione di progetto e altri dati indipendenti dalla compilazione. Questo metodo viene chiamato se non sono presenti dati di configurazione XML presenti nel file di progetto.

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

2. Implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> per caricare i dati XML dal file di progetto.

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
> Tutti gli esempi di codice forniti in questo argomento sono parti di un esempio più esaustivo in [esempi di VSSDK](https://aka.ms/vs2015sdksamples).

## <a name="see-also"></a>Vedere anche
- [Rendere persistenti i dati nel file di progetto MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)