---
title: Verifica dei sottotipi di un progetto in fase di esecuzione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5a64cdb11231649b49f9c0322a241c807d94fe76
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55011104"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Verificare i sottotipi di un progetto in fase di esecuzione
Un pacchetto VSPackage che dipende da un sottotipo di progetto personalizzati deve includere logica da cercare in modo che si può arrestare normalmente se non è presente il sottotipo di sottotipo. La procedura seguente viene illustrato come verificare la presenza di un sottotipo specificato.  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>Per verificare la presenza di un sottotipo  
  
1.  Ottenere la gerarchia del progetto dagli oggetti di progetto e soluzione come un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oggetto aggiungendo il codice seguente al pacchetto VSPackage.  
  
    ```csharp  
    EnvDTE.DTE dte;  
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
  
    EnvDTE.Project project;  
    project = dte.Solution.Projects.Item(1);  
  
    IVsSolution solution;  
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
  
    IVsHierarchy hierarchy;  
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);  
  
    ```  
  
2.  Eseguire il cast della gerarchia per il <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> interfaccia.  
  
    ```csharp  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3.  Ottiene l'elenco di GUID del tipo di progetto richiamando il <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>.  
  
    ```csharp  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4.  Controllare l'elenco per il GUID del sottotipo specificato.  
  
    ```csharp  
    // Replace the string "MyGUID" with the GUID of the subtype.  
    string guidMySubtype = "MyGUID";  
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)  
    {  
        // The specified subtype is present.  
    }  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Sottotipi di progetto](../extensibility/internals/project-subtypes.md)   
 [Progettazione di sottotipi di progetto](../extensibility/internals/project-subtypes-design.md)   
 [Le proprietà e metodi estesi dai sottotipi di progetto](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)