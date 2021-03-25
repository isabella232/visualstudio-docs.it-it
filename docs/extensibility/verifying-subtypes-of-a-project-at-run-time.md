---
title: Verifica dei sottotipi di un progetto in fase di esecuzione | Microsoft Docs
description: Informazioni su come fare in modo che il pacchetto VSPackage verifichi la presenza di un sottotipo di progetto personalizzato specificato da cui dipende.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c52d3297ce4903cb8f8e7cb2f9ab5169d21ac94e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062603"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Verificare i sottotipi di un progetto in fase di esecuzione
Un VSPackage che dipende da un sottotipo di progetto personalizzato deve includere la logica per cercare tale sottotipo, in modo che possa avere esito negativo correttamente se il sottotipo non è presente. Nella procedura riportata di seguito viene illustrato come verificare la presenza di un sottotipo specificato.

### <a name="to-verify-the-presence-of-a-subtype"></a>Per verificare la presenza di un sottotipo

1. Ottenere la gerarchia del progetto dagli oggetti del progetto e della soluzione come <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oggetto aggiungendo il codice seguente al pacchetto VSPackage.

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

2. Eseguire il cast della gerarchia all' <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> interfaccia.

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. Ottenere l'elenco dei GUID del tipo di progetto richiamando <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A> .

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

## <a name="see-also"></a>Vedi anche
- [Sottotipi di progetto](../extensibility/internals/project-subtypes.md)
- [Progettazione sottotipi di progetto](../extensibility/internals/project-subtypes-design.md)
- [Proprietà e metodi estesi dai sottotipi di progetto](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
