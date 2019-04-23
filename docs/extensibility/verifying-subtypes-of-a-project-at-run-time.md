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
ms.openlocfilehash: 6ec71ce9be704566640a90c9187abe77f5cc3fe3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60101600"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Verificare i sottotipi di un progetto in fase di esecuzione
Un pacchetto VSPackage che dipende da un sottotipo di progetto personalizzati deve includere logica da cercare in modo che si può arrestare normalmente se non è presente il sottotipo di sottotipo. La procedura seguente viene illustrato come verificare la presenza di un sottotipo specificato.

### <a name="to-verify-the-presence-of-a-subtype"></a>Per verificare la presenza di un sottotipo

1. Ottenere la gerarchia del progetto dagli oggetti di progetto e soluzione come un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oggetto aggiungendo il codice seguente al pacchetto VSPackage.

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

2. Eseguire il cast della gerarchia per il <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> interfaccia.

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. Ottiene l'elenco di GUID del tipo di progetto richiamando il <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>.

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. Controllare l'elenco per il GUID del sottotipo specificato.

    ```csharp
    // Replace the string "MyGUID" with the GUID of the subtype.
    string guidMySubtype = "MyGUID";
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)
    {
        // The specified subtype is present.
    }
    ```

## <a name="see-also"></a>Vedere anche
- [Sottotipi di progetto](../extensibility/internals/project-subtypes.md)
- [Progettazione di sottotipi di progetto](../extensibility/internals/project-subtypes-design.md)
- [Le proprietà e metodi estesi dai sottotipi di progetto](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)