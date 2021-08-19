---
title: Salvataggio di dati in Project file | Microsoft Docs
description: Informazioni sulle interfacce fornite da Managed Package Framework per salvare e recuperare dati specifici del sottotipo nel file di progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 4e215954edfafa1463739431e0b422ae7521ab35
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158385"
---
# <a name="save-data-in-project-files"></a>Salvare i dati nei file di progetto
Un sottotipo di progetto può salvare e recuperare dati specifici del sottotipo nel file di progetto. Managed Package Framework (MPF) fornisce due interfacce per eseguire questa attività:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>L'interfaccia consente di accedere ai valori delle proprietà **MSBuild** sezione del file di progetto. I metodi forniti da possono essere chiamati da qualsiasi utente ogni volta che l'utente deve <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> caricare o salvare i dati correlati alla compilazione.

- l'oggetto viene usato per rendere persistenti i dati <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> non correlati alla compilazione nel codice XML in formato libero. I metodi forniti da vengono chiamati da ogni volta che è necessario rendere persistenti i dati non correlati alla compilazione <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nel file di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto.

  Per altre informazioni su come rendere persistenti i dati correlati alla compilazione e non alla compilazione, vedere Rendere persistenti i dati nel [file MSBuild progetto](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).

## <a name="save-and-retrieve-build-related-data"></a>Salvare e recuperare i dati correlati alla compilazione

### <a name="to-save-a-build-related-data-in-the-project-file"></a>Per salvare i dati correlati alla compilazione nel file di progetto

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

### <a name="to-retrieve-build-related-data-from-the-project-file"></a>Per recuperare i dati correlati alla compilazione dal file di progetto

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

## <a name="save-and-retrieve-non-build-related-data"></a>Salvare e recuperare dati non correlati alla compilazione

### <a name="to-save-non-build-related-data-in-the-project-file"></a>Per salvare i dati non correlati alla compilazione nel file di progetto

1. Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> il metodo per determinare se un frammento XML è stato modificato dopo l'ultimo salvataggio nel file corrente.

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

### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>Per recuperare dati non correlati alla compilazione nel file di progetto

1. Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> il metodo per inizializzare le proprietà dell'estensione di progetto e altri dati indipendenti dalla compilazione. Questo metodo viene chiamato se non sono presenti dati di configurazione XML nel file di progetto.

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
> Tutti gli esempi di codice forniti in questo argomento sono parti di un esempio più ampio negli [esempi di VSSDK.](https://github.com/Microsoft/VSSDK-Extensibility-Samples)

## <a name="see-also"></a>Vedi anche
- [Rendere persistenti i dati nel file MSBuild progetto](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
