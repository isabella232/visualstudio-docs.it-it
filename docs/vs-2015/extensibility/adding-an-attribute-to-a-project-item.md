---
title: Aggiunta di un attributo a un elemento di progetto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1740ac4dfdeb64d5b4b2b0aab264845de9c186dd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117616"
---
# <a name="adding-an-attribute-to-a-project-item"></a>Aggiunta di un attributo a un elemento di progetto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I metodi <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> ottenere e impostare il valore degli attributi di un elemento del progetto. SetItemAttribute crea l'attributo se non esiste già, aggiungerlo ai metadati dell'elemento di progetto.  
  
## <a name="adding-an-attribute-to-a-project-item"></a>Aggiunta di un attributo a un elemento del progetto  
  
#### <a name="to-add-an-attribute-to-a-project-item"></a>Per aggiungere un attributo a un elemento del progetto  
  
- Il codice seguente usa il <xref:EnvDTE.DTE> oggetto di automazione e <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> metodo per aggiungere un attributo a un elemento del progetto. L'ID di elemento di progetto viene ottenuto dal nome di elemento di progetto "program.cs". L'attributo "MyAttribute" viene aggiunto a questo elemento del progetto e assegnato il valore "MyValue".  
  
    ```  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution =     (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath =         (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(  
            itemId, "MyAttribute", "MyValue");  
    }  
  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Salvataggio permanente dei dati nel file di progetto MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
