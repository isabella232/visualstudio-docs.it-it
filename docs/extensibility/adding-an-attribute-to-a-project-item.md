---
title: Aggiunta di un attributo a un elemento di progetto Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740198"
---
# <a name="add-an-attribute-to-a-project-item"></a>Aggiungere un attributo a un elemento di progettoAdd an attribute to a project item
I <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> metodi <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> e ottenere e impostare il valore degli attributi di un elemento di progetto. SetItemAttribute crea l'attributo se non esiste già, aggiungendolo ai metadati dell'elemento di progetto.

## <a name="add-an-attribute-to-a-project-item"></a>Aggiungere un attributo a un elemento di progettoAdd an attribute to a project item

- Il codice seguente <xref:EnvDTE.DTE> usa l'oggetto di automazione e il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> metodo per aggiungere un attributo a un elemento di progetto. L'ID dell'elemento di progetto viene ottenuto dal nome dell'elemento di progetto "program.cs". L'attributo "MyAttribute" viene aggiunto a questo elemento di progetto e viene assegnato il valore "MyValue".

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
- [Rendere persistenti i dati nel file di progetto MSBuildPersist data in the MSBuild project file](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
