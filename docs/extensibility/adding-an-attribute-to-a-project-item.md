---
title: Aggiunta di un attributo a un elemento di progetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 059eef0b6a215f1f02c77df63f777fbfda5dff19
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80740198"
---
# <a name="add-an-attribute-to-a-project-item"></a>Aggiungere un attributo a un elemento di progetto
I metodi <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> ottengono e impostano il valore degli attributi di un elemento di progetto. SetItemAttribute crea l'attributo se non esiste già, aggiungendolo ai metadati dell'elemento di progetto.

## <a name="add-an-attribute-to-a-project-item"></a>Aggiungere un attributo a un elemento di progetto

- Il codice seguente usa l' <xref:EnvDTE.DTE> oggetto di automazione e il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> metodo per aggiungere un attributo a un elemento di progetto. L'ID dell'elemento del progetto viene ottenuto dal nome dell'elemento del progetto "program.cs". L'attributo "attributo" viene aggiunto a questo elemento di progetto e viene specificato il valore "valore".

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        uint itemId;
        string fullPath = (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;
        hierarchy.ParseCanonicalName(fullPath, out itemId);
        buildPropertyStorage.SetItemAttribute(itemId, "MyAttribute", "MyValue");
    }

    ```

## <a name="see-also"></a>Vedere anche
- [Mantieni i dati nel file di progetto MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
