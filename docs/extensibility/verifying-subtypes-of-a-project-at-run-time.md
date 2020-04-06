---
title: Verifica dei sottotipi di un progetto in fase di esecuzione Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0d739a9f8734dd8941e3254d03364cbf4c77350
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698175"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Verificare i sottotipi di un progetto in fase di esecuzioneVerify subtypes of a project at run time
Un pacchetto VSPackage che dipende da un sottotipo di progetto personalizzato deve includere la logica per cercare tale sottotipo in modo che possa non riuscire normalmente se il sottotipo non è presente. Nella procedura seguente viene illustrato come verificare la presenza di un sottotipo specificato.

### <a name="to-verify-the-presence-of-a-subtype"></a>Per verificare la presenza di un sottotipo

1. Ottenere la gerarchia del progetto dagli <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oggetti di progetto e soluzione come oggetto aggiungendo il codice seguente al pacchetto VSPackage.Get the project hierarchy from the project and solution objects as a object by adding the following code to your VSPackage.

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

2. Eseguire il cast <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> della gerarchia all'interfaccia.

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. Ottenere l'elenco dei GUID di tipo <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>di progetto richiamando il file .

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
- [Proprietà e metodi estesi dai sottotipi di progetto](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
