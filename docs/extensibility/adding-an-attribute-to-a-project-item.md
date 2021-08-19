---
title: Aggiunta di un attributo a un Project item | Microsoft Docs
description: Informazioni su come aggiungere un attributo a un elemento di progetto in Visual Studio usando i metodi di interoperabilità della shell GetItemAttribute e SetItemAttribute.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: df176c3e52407656b66a58ac65e733e7907e59e7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133497"
---
# <a name="add-an-attribute-to-a-project-item"></a>Aggiungere un attributo a un elemento di progetto
I metodi <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> ottengono e impostano il valore degli attributi di un elemento di progetto. SetItemAttribute crea l'attributo se non esiste già, aggiungendolo ai metadati dell'elemento di progetto.

## <a name="add-an-attribute-to-a-project-item"></a>Aggiungere un attributo a un elemento di progetto

- Nel codice seguente vengono utilizzati <xref:EnvDTE.DTE> l'oggetto di automazione e <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> il metodo per aggiungere un attributo a un elemento di progetto. L'ID dell'elemento di progetto viene ottenuto dal nome dell'elemento di progetto "program.cs". L'attributo "MyAttribute" viene aggiunto a questo elemento di progetto e viene assegnato il valore "MyValue".

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

## <a name="see-also"></a>Vedi anche
- [Rendere persistenti i dati nel file MSBuild progetto](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
