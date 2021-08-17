---
title: Verifica dei sottotipi di un Project in fase di esecuzione | Microsoft Docs
description: Informazioni su come fare in modo che il pacchetto VSPackage verifichi la presenza di un sottotipo di progetto personalizzato specificato da cui dipende.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b797d8b13ec9f4c8a2d968fa0e363e74b5fa465c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122056719"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Verificare i sottotipi di un progetto in fase di esecuzione
Un VSPackage che dipende da un sottotipo di progetto personalizzato deve includere la logica per cercare il sottotipo in modo che possa non riuscire correttamente se il sottotipo non è presente. Nella procedura seguente viene illustrato come verificare la presenza di un sottotipo specificato.

### <a name="to-verify-the-presence-of-a-subtype"></a>Per verificare la presenza di un sottotipo

1. Ottenere la gerarchia del progetto dagli oggetti progetto e soluzione come oggetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> aggiungendo il codice seguente al pacchetto VSPackage.

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

2. Eseguire il cast della gerarchia <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> all'interfaccia .

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. Ottenere l'elenco dei GUID del tipo di progetto richiamando <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A> .

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. Controllare nell'elenco il GUID del sottotipo specificato.

    ```csharp
    // Replace the string "MyGUID" with the GUID of the subtype.
    string guidMySubtype = "MyGUID";
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)
    {
        // The specified subtype is present.
    }
    ```

## <a name="see-also"></a>Vedi anche
- [Project sottotipi](../extensibility/internals/project-subtypes.md)
- [Project di sottotipi](../extensibility/internals/project-subtypes-design.md)
- [Proprietà e metodi estesi dai sottotipi di progetto](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
