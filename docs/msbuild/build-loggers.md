---
title: Logger di compilazione | Microsoft Docs
description: Usare MSBuild logger per gestire e personalizzare l'output della compilazione e visualizzare messaggi, errori o avvisi in risposta a eventi di compilazione specifici.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 7ac40c5ab5f836fee3b0f98a0339138fbf02eb0fe0ce6e64f552f9c8e5c86a18
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121428640"
---
# <a name="build-loggers"></a>Logger di compilazione

I logger consentono di personalizzare l'output della compilazione e visualizzare messaggi, errori o avvisi in risposta a specifici eventi di compilazione. Ogni logger viene implementato come classe .NET che implementa l'interfaccia <xref:Microsoft.Build.Framework.ILogger>, definita nell'assembly *Microsoft.Build.Framework.dll*.

È possibile implementare un logger in due modi:

- Implementare direttamente l'interfaccia <xref:Microsoft.Build.Framework.ILogger>.
- Derivare la classe dalla classe di supporto <xref:Microsoft.Build.Utilities.Logger>, definita nell'assembly *Microsoft.Build.Utilities.dll*. La classe <xref:Microsoft.Build.Utilities.Logger> implementa <xref:Microsoft.Build.Framework.ILogger> e fornisce le implementazioni predefinite di alcuni membri di <xref:Microsoft.Build.Framework.ILogger>.

  Questo argomento illustra come scrivere un logger semplice che deriva dalla classe <xref:Microsoft.Build.Utilities.Logger> e descrive i messaggi visualizzati sulla console in risposta a specifici eventi di compilazione.

## <a name="register-for-events"></a>Eseguire la registrazione per gli eventi

Lo scopo di un logger è quello di raccogliere informazioni sullo stato di avanzamento della compilazione, così come riportate dal motore di compilazione, e di organizzarle in maniera utile. Tutti i logger devono eseguire l'override del metodo <xref:Microsoft.Build.Utilities.Logger.Initialize%2A>, che corrisponde alla posizione in cui il logger registra gli eventi. In questo esempio il logger registra gli eventi <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> e <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs" id="Snippet2":::

## <a name="respond-to-events"></a>Rispondere agli eventi

Il logger è stato registrato per eventi specifici e dovrà gestire questi eventi ogni volta che si verificano. Per gli eventi <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> e <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>, il logger scrive semplicemente una breve frase e il nome del file di progetto interessato dall'evento. Tutti i messaggi provenienti dal logger vengono scritti nella finestra della console.

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs" id="Snippet3":::

## <a name="respond-to-logger-verbosity-values"></a>Rispondere ai valori di dettaglio del logger

In alcuni casi, può essere necessario registrare le informazioni di un evento solo se l'opzione **-verbosity** di MSBuild.exe contiene un determinato valore. In questo esempio, il gestore eventi registra un messaggio solo se la proprietà , impostata dall'opzione <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A> **-verbosity,** è uguale a <xref:Microsoft.Build.Framework.LoggerVerbosity> `Detailed` .

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs" id="Snippet4":::

## <a name="specify-a-logger"></a>Specificare un logger

Dopo aver compilato il logger in un assembly, è necessario indicare MSBuild usare tale logger durante le compilazioni. Questa operazione viene eseguita usando **l'opzione -logger** *conMSBuild.exe*. Per altre informazioni sulle opzioni disponibili per *MSBuild.exe*, vedere [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md).

La riga di comando seguente compila il progetto *MyProject.csproj* e usa la classe logger implementata in *SimpleLogger.dll*. **L'opzione -nologo** nasconde il banner e il messaggio di copyright e l'opzione **-noconsolelogger** disabilita il logger di console MSBuild predefinito.

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll
```

La riga di comando seguente compila il progetto con lo stesso logger, ma con un livello di `Verbosity` impostato su `Detailed`.

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll -verbosity:Detailed
```

## <a name="example-1"></a>Esempio 1

### <a name="description"></a>Descrizione

L'esempio seguente contiene il codice completo per il logger.

### <a name="code"></a>Codice

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs" id="Snippet1":::

## <a name="example-2"></a>Esempio 2

### <a name="description"></a>Descrizione

L'esempio seguente illustra l'implementazione di un logger che scrive il log in un file, anziché visualizzarlo nella finestra di console.

### <a name="code"></a>Codice

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_BasicLogger/CS/msbuild_BasicLogger.cs" id="Snippet1":::

## <a name="see-also"></a>Vedi anche

- [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)
