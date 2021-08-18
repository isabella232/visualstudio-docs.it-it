---
title: API MSBuild | Microsoft Docs
description: Informazioni sulla superficie di attacco dell'API pubblica MSBuild in modo che il programma possa eseguire compilazioni e ispezionare i progetti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 5ab75ae34fbea3b8423e074b3c5120459c681169
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115772"
---
# <a name="use-the-msbuild-api"></a>Uso dell'API MSBuild

MSBuild fornisce una superficie dell'API pubblica per consentire al programma di eseguire le compilazioni e verificare i progetti. Le versioni recenti delle API MSBuild sono disponibili nei pacchetti NuGet seguenti:

| Nome del pacchetto | Descrizione |
| ------------ | ----------- |
| [Microsoft.Build](https://www.nuget.org/packages/Microsoft.Build) | Contiene l'assembly Microsoft.Build usato per creare, modificare e valutare MSBuild progetti.|
| [Microsoft.Build.Framework](https://www.nuget.org/packages/Microsoft.Build.Framework)| Contiene l'assembly MSBuild framework comune usato da altri MSBuild assembly. |
| [Microsoft.Build.Runtime](https://www.nuget.org/packages/Microsoft.Build.Runtime) | Recapita una copia eseguibile completa MSBuild. Fare riferimento a questo pacchetto solo se l'applicazione deve caricare progetti o eseguire compilazioni in-process senza richiedere l'installazione di MSBuild. La corretta valutazione dei progetti che usano questo pacchetto richiede l'aggregazione di componenti aggiuntivi (come i compilatori) in una directory dell'applicazione. |
| [Microsoft.Build.Tasks.Core](https://www.nuget.org/packages/Microsoft.Build.Tasks.Core) | Contiene l'assembly Microsoft.Build.Tasks che implementa le attività di uso comune MSBuild. |
| [Microsoft.Build.Utilities.Core](https://www.nuget.org/packages/Microsoft.Build.Utilities.Core) | Contiene l'assembly Microsoft.Build.Utilities usato per implementare attività MSBuild personalizzate. |

Inoltre, NuGet ospita anche un assembly legacy, [Microsoft.Build.Engine](https://www.nuget.org/packages/Microsoft.Build.Engine), che è deprecato.

Esistono diverse versioni dell'API MSBuild e per le versioni 15 e 16 sono disponibili due forme distinte degli assembly nei pacchetti NuGet, una compilata con .NET Framework e un'altra compilata con .NET Core, che è un subset della superficie dell'API .NET Framework.  La versione .NET Core di MSBuild viene usata quando si richiama il comando e quando si usa MSBuild `dotnet` nei sistemi Mac e Linux.

La documentazione per l'API MSBuild è disponibile tramite [Browser API .NET](/dotnet/api)o esplorando gli spazi dei nomi nell'elenco seguente.

::: moniker range="vs-2017"
| Spazio dei nomi | Si applica a | Descrizione |
|-----------| -----------| ----------- |
| [Microsoft.build.construction](/dotnet/api/Microsoft.Build.Construction?view=msbuild-15&preserve-view=true) | Tutti |  Contiene i tipi utilizzati dal modello a oggetti MSBuild per costruire le radici del progetto con valori non valutati. Ogni radice di progetto corrisponde a un file di progetto o targets. |
| [Microsoft.Build.Definition](/dotnet/api/Microsoft.Build.Definition?view=msbuild-15&preserve-view=true) | Tutti | Contiene la `ProjectOptions` classe , che supporta la costruzione del progetto. |
| [Microsoft.Build.Evaluation](/dotnet/api/Microsoft.Build.Evaluation?view=msbuild-15&preserve-view=true) | Tutti | Contiene i tipi utilizzati dal modello a oggetti MSBuild per valutare i progetti. Ogni progetto è associato a una o più radici di progetto. |
| [Microsoft.Build.Evaluation.Context](/dotnet/api/Microsoft.Build.Evaluation.Context?view=msbuild-15&preserve-view=true) | Tutti | Contiene la `EvaluationContext` classe , utilizzata per archiviare lo stato di valutazione tra le chiamate. |
| [Microsoft.build.exceptions](/dotnet/api/Microsoft.Build.Exceptions?view=msbuild-15&preserve-view=true) | Tutti | Contiene i tipi di eccezione che è possibile generare durante il processo di compilazione. |
| [Microsoft.Build.Execution](/dotnet/api/Microsoft.Build.Execution?view=msbuild-15&preserve-view=true) | Tutti | Contiene i tipi utilizzati dal modello a oggetti MSBuild per compilare i progetti. |
| [Microsoft.Build.Framework](/dotnet/api/Microsoft.Build.Framework?view=msbuild-15&preserve-view=true) | Tutti | Contiene i tipi che definiscono come avviene l'interazione di attività e logger con il motore MSBuild.|
| [Microsoft.Build.Framework.Profiler](/dotnet/api/Microsoft.Build.Framework.Profiler?view=msbuild-15&preserve-view=true) | Tutti | Contiene i tipi che supportano la profilatura delle prestazioni. |
| [Microsoft.Build.Framework.XamlTypes](/dotnet/api/Microsoft.Build.Framework.XamlTypes?view=msbuild-15&preserve-view=true) | .NET Framework solo | Contiene classi usate per rappresentare i tipi XAML analizzati da file, regole e altre origini. |
| [Microsoft.Build.Globbing](/dotnet/api/Microsoft.Build.Globbing?view=msbuild-15&preserve-view=true) | Tutti | Contiene classi che supportano l'elaborazione con caratteri jolly. |
| [Microsoft.Build.Globbing.Extensions](/dotnet/api/Microsoft.Build.Globbing.Extensions?view=msbuild-15&preserve-view=true) | Tutti | Contiene tipi che supportano le estensioni per l'elaborazione di caratteri jolly. |
| [Microsoft.Build. Graph](/dotnet/api/Microsoft.Build.Graph?view=msbuild-15&preserve-view=true) | Tutti | Contiene tipi che supportano `-graph` l'opzione MSBuild. |
| [Microsoft.Build.Logging](/dotnet/api/Microsoft.Build.Logging?view=msbuild-15&preserve-view=true) | Tutti | Contiene i tipi utilizzati per la registrazione dello stato di avanzamento di una compilazione. |
| [Microsoft.Build.ObjectModelRemoting](/dotnet/api/Microsoft.Build.ObjectModelRemoting?view=msbuild-15&preserve-view=true) | Tutti | Contiene tipi che supportano la comunicazione remota in MSBuild. |
| [Microsoft.Build.Tasks](/dotnet/api/Microsoft.Build.Tasks?view=msbuild-15&preserve-view=true) | Tutti | Contiene l'implementazione di tutte le attività disponibili in MSBuild. |
| [Microsoft.Build.Tasks.Deployment.Bootstrapper](/dotnet/api/Microsoft.Build.Tasks.Deployment.Bootstrapper?view=msbuild-15&preserve-view=true) | .NET Framework solo | Contiene classi usate internamente da MSBuild. |
| [Microsoft.Build.Tasks.Deployment.ManifestUtilities](/dotnet/api/Microsoft.Build.Tasks.Deployment.ManifestUtilities?view=msbuild-15&preserve-view=true) | .NET Framework solo | Contiene le classi usate da MSBuild.|
| [Microsoft.Build.Tasks.Hosting](/dotnet/api/Microsoft.Build.Tasks.Hosting?view=msbuild-15&preserve-view=true) | Tutti | Contiene classi usate internamente da MSBuild. |
| [Microsoft.Build.Tasks.Xaml](/dotnet/api/Microsoft.Build.Tasks.Xaml?view=msbuild-15&preserve-view=true) | .NET Framework solo | Contiene classi correlate alle attività di compilazione XAML. |
| [Microsoft.Build.Utilities](/dotnet/api/Microsoft.Build.Utilities?view=msbuild-15&preserve-view=true) | Tutti | Contiene classi helper che è possibile usare per creare logger e attività MSBuild personalizzati.|
:::moniker-end
:::moniker range=">=vs-2019"
| Spazio dei nomi | Si applica a | Descrizione |
|-----------| -----------| ----------- |
| [Microsoft.build.construction](/dotnet/api/Microsoft.Build.Construction?view=msbuild-16&preserve-view=true) | Tutti |  Contiene i tipi utilizzati dal modello a oggetti MSBuild per costruire le radici del progetto con valori non valutati. Ogni radice di progetto corrisponde a un file di progetto o targets. |
| [Microsoft.Build.Definition](/dotnet/api/Microsoft.Build.Definition?view=msbuild-16&preserve-view=true) | Tutti | Contiene la `ProjectOptions` classe , che supporta la costruzione del progetto. |
| [Microsoft.Build.Evaluation](/dotnet/api/Microsoft.Build.Evaluation?view=msbuild-16&preserve-view=true) | Tutti | Contiene i tipi utilizzati dal modello a oggetti MSBuild per valutare i progetti. Ogni progetto è associato a una o più radici di progetto. |
| [Microsoft.Build.Evaluation.Context](/dotnet/api/Microsoft.Build.Evaluation.Context?view=msbuild-16&preserve-view=true) | Tutti | Contiene la `EvaluationContext` classe , utilizzata per archiviare lo stato di valutazione tra le chiamate. |
| [Microsoft.build.exceptions](/dotnet/api/Microsoft.Build.Exceptions?view=msbuild-16&preserve-view=true) | Tutti | Contiene i tipi di eccezione che è possibile generare durante il processo di compilazione. |
| [Microsoft.Build.Execution](/dotnet/api/Microsoft.Build.Execution?view=msbuild-16&preserve-view=true) | Tutti | Contiene i tipi utilizzati dal modello a oggetti MSBuild per compilare i progetti. |
| [Microsoft.Build.Framework](/dotnet/api/Microsoft.Build.Framework?view=msbuild-16&preserve-view=true) | Tutti | Contiene i tipi che definiscono come avviene l'interazione di attività e logger con il motore MSBuild.|
| [Microsoft.Build.Framework.Profiler](/dotnet/api/Microsoft.Build.Framework.Profiler?view=msbuild-16&preserve-view=true) | Tutti | Contiene i tipi che supportano la profilatura delle prestazioni. |
| [Microsoft.Build.Framework.XamlTypes](/dotnet/api/Microsoft.Build.Framework.XamlTypes?view=msbuild-16&preserve-view=true) | .NET Framework solo | Contiene classi usate per rappresentare i tipi XAML analizzati da file, regole e altre origini. |
| [Microsoft.Build.Globbing](/dotnet/api/Microsoft.Build.Globbing?view=msbuild-16&preserve-view=true) | Tutti | Contiene classi che supportano l'elaborazione con caratteri jolly. |
| [Microsoft.Build.Globbing.Extensions](/dotnet/api/Microsoft.Build.Globbing.Extensions?view=msbuild-16&preserve-view=true) | Tutti | Contiene tipi che supportano estensioni per l'elaborazione con caratteri jolly. |
| [Microsoft.Build. Graph](/dotnet/api/Microsoft.Build.Graph?view=msbuild-16&preserve-view=true) | Tutti | Contiene tipi che supportano l MSBuild `-graph` switch. |
| [Microsoft.Build.Logging](/dotnet/api/Microsoft.Build.Logging?view=msbuild-16&preserve-view=true) | Tutti | Contiene i tipi utilizzati per la registrazione dello stato di avanzamento di una compilazione. |
| [Microsoft.Build.ObjectModelRemoting](/dotnet/api/Microsoft.Build.ObjectModelRemoting?view=msbuild-16&preserve-view=true) | Tutti | Contiene tipi che supportano la comunicazione remota in MSBuild. |
| [Microsoft.Build.Tasks](/dotnet/api/Microsoft.Build.Tasks?view=msbuild-16&preserve-view=true) | Tutti | Contiene l'implementazione di tutte le attività disponibili in MSBuild. |
| [Microsoft.Build.Tasks.Deployment.Bootstrapper](/dotnet/api/Microsoft.Build.Tasks.Deployment.Bootstrapper?view=msbuild-16&preserve-view=true) | .NET Framework solo | Contiene classi usate internamente da MSBuild. |
| [Microsoft.Build.Tasks.Deployment.ManifestUtilities](/dotnet/api/Microsoft.Build.Tasks.Deployment.ManifestUtilities?view=msbuild-16&preserve-view=true) | .NET Framework solo | Contiene le classi usate da MSBuild.|
| [Microsoft.Build.Tasks.Hosting](/dotnet/api/Microsoft.Build.Tasks.Hosting?view=msbuild-16&preserve-view=true) | Tutti | Contiene classi usate internamente da MSBuild. |
| [Microsoft.Build.Tasks.Xaml](/dotnet/api/Microsoft.Build.Tasks.Xaml?view=msbuild-16&preserve-view=true) | .NET Framework solo | Contiene classi correlate alle attività di compilazione XAML. |
| [Microsoft.Build.Utilities](/dotnet/api/Microsoft.Build.Utilities?view=msbuild-16&preserve-view=true) | Tutti | Contiene classi helper che è possibile usare per creare logger e attività MSBuild personalizzati.|
:::moniker-end

Nella tabella precedente All nella colonna Si applica a indica che i tipi nello spazio dei nomi sono disponibili nelle versioni .NET Framework e .NET Core dell'API MSBuild.
