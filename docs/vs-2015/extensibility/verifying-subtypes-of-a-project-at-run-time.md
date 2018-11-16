---
title: Verifica dei sottotipi di un progetto in fase di esecuzione | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 892ba25ff70f62f77016bea1b88436c4f5a6a5b0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779892"
---
# <a name="verifying-subtypes-of-a-project-at-run-time"></a>Verifica dei sottotipi di un progetto in fase di esecuzione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un pacchetto VSPackage che dipende da un sottotipo di progetto personalizzati deve includere logica da cercare in modo che si può arrestare normalmente se non è presente il sottotipo di sottotipo. La procedura seguente viene illustrato come verificare la presenza di un sottotipo specificato.  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>Per verificare la presenza di un sottotipo  
  
1.  Ottenere la gerarchia del progetto dagli oggetti di progetto e soluzione come un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oggetto aggiungendo il codice seguente al pacchetto VSPackage.  
  
    ```  
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
  
    ```  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3.  Ottiene l'elenco di GUID del tipo di progetto richiamando il <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>.  
  
    ```  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4.  Controllare l'elenco per il GUID del sottotipo specificato.  
  
    ```  
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
 [Proprietà e metodi estesi dai sottotipi di progetto](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

