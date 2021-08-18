---
title: Avvio di una compilazione all'interno dell'IDE | Microsoft Docs
description: Informazioni su come usare Microsoft.VisualStudio.Shell.Interop.IVsBuildManagerAccessor per avviare le compilazioni per i sistemi di progetto personalizzati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- build
ms.assetid: 936317aa-63b7-4eb0-b9db-b260a0306196
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: e8c13ca9d8c5cbbb42e11ca9c17d4c5b1381dcba
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093627"
---
# <a name="start-a-build-from-within-the-ide"></a>Avvio di una compilazione all'interno dell'IDE

I sistemi di progetto personalizzati devono usare <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildManagerAccessor> per avviare le compilazioni. In questo argomento vengono descritti i motivi dei requisiti e la procedura da seguire.

## <a name="parallel-builds-and-threads"></a>Compilazioni parallele e thread

 Visual Studio le compilazioni parallele, che richiedono l'accesso alle risorse comuni. I sistemi di progetto sono in grado di eseguire le compilazioni in modo asincrono, ma non devono chiamare le funzioni di compilazione dall'interno di callback.

 Se il sistema di progetto modifica le variabili di ambiente, è necessario impostare il valore NodeAffinity della compilazione su OutOfProc. Il requisito implica che non è possibile usare oggetti host, poiché richiedono il nodo in-process.

## <a name="use-ivsbuildmanageraccessor"></a>Uso di IVSBuildManagerAccessor

 Il codice riportato di seguito illustra un metodo che può essere usato da un sistema di progetto per avviare una compilazione:

```csharp

public bool Build(Project project, bool isDesignTimeBuild)
{
    // Get the accessor from the IServiceProvider interface for the
    // project system
    IVsBuildManagerAccessor accessor =
        serviceProvider.GetService(typeof(SVsBuildManagerAccessor)) as
        IVsBuildManagerAccessor;
    bool releaseUIThread = false;
    try
    {
        if(accessor != null)
        {
            // Claim the UI thread under the following conditions:
            // 1. The build must use a resource that uses the UI thread
            // or,
            // 2. The build requires the in-proc node AND waits on the
            // UI thread for the build to complete
            if(NeedsUIThread)
            {
                int result = accessor.ClaimUIThreadForBuild();
                if(result != S_OK)
                {
                     // Not allowed to claim the UI thread right now
                     return false;
                }
                releaseUIThread = true;
             }
             if(isDesignTimeBuild)
             {
// Start the design time build
                  int result = accessor.BeginDesignTimeBuild();
                  if(result != S_OK)
                  {
                      // Not allowed to begin a design-time build at
                      // this time. Try again later.
                      return false;
                  }
             }
         }
         bool buildSucceeded = false;
         // perform project-system specific build set up tasks
         // Create your BuildRequestData
         // This assumes a IHostServices variable (hostServices) set
   // to your host services. If you don't use a project instance
         // (you build from a file for example) then use another
         // constructor.
         BuildRequestData requestData = new
             BuildRequestData(project.CreateProjectInstance(),
             "myTarget", hostServices,
             BuildRequestData.BuildRequestDataFlags.None);
         // Mark your your submission as Pending
         BuildSubmission submission =
              BuildManager.DefaultBuildManager.
              PendBuildRequest(requestData);
         // Register the loggers in BuildLoggers
         if (accessor != null)
         {
               foreach (ILogger logger in BuildLoggers)
               {
                    accessor.RegisterLogger(submission.SubmissionId,
                        logger);
               }
         }
         BuildResult buildResult = submission.Execute();
         return buildResult;
     }
     // Clean up resources
     finally
     {
         if(accessor != null)
         {
             // Unregister the loggers, if necessary.
             accessor.UnregisterLoggers(submission.SubmissionId);
             // Release the UI thread, if used
             if(releaseUIThread)
             {
                  accessor.ReleaseUIThreadForBuild();
             }
             // End the design time build, if used
             if(isDesignTimeBuild)
             {
                  accessor.EndDesignTimeBuild();
             }
         }
     }
}
```
