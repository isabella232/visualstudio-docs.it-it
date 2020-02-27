---
title: Logger di compilazione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a00bbb8ce239275ff140dbedf2157e4cdc41d44c
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634526"
---
# <a name="build-loggers"></a>Logger di compilazione

I logger consentono di personalizzare l'output della compilazione e visualizzare messaggi, errori o avvisi in risposta a specifici eventi di compilazione. Ogni logger viene implementato come classe .NET che implementa l'interfaccia <xref:Microsoft.Build.Framework.ILogger>, definita nell'assembly *Microsoft.Build.Framework.dll*.

È possibile implementare un logger in due modi:

- Implementare direttamente l'interfaccia <xref:Microsoft.Build.Framework.ILogger>.
- Derivare la classe dalla classe di supporto <xref:Microsoft.Build.Utilities.Logger>, definita nell'assembly *Microsoft.Build.Utilities.dll*. La classe <xref:Microsoft.Build.Utilities.Logger> implementa <xref:Microsoft.Build.Framework.ILogger> e fornisce le implementazioni predefinite di alcuni membri di <xref:Microsoft.Build.Framework.ILogger>.

  Questo argomento illustra come scrivere un logger semplice che deriva dalla classe <xref:Microsoft.Build.Utilities.Logger> e descrive i messaggi visualizzati sulla console in risposta a specifici eventi di compilazione.

## <a name="register-for-events"></a>Eseguire la registrazione per gli eventi

Lo scopo di un logger è quello di raccogliere informazioni sullo stato di avanzamento della compilazione, così come riportate dal motore di compilazione, e di organizzarle in maniera utile. Tutti i logger devono eseguire l'override del metodo <xref:Microsoft.Build.Utilities.Logger.Initialize%2A>, che corrisponde alla posizione in cui il logger registra gli eventi. In questo esempio il logger registra gli eventi <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> e <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.

[!code-csharp[msbuild_SimpleConsoleLogger#2](../msbuild/codesnippet/CSharp/build-loggers_1.cs)]

## <a name="respond-to-events"></a>Rispondere agli eventi

Il logger è stato registrato per eventi specifici e dovrà gestire questi eventi ogni volta che si verificano. Per gli eventi <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> e <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>, il logger scrive semplicemente una breve frase e il nome del file di progetto interessato dall'evento. Tutti i messaggi provenienti dal logger vengono scritti nella finestra della console.

[!code-csharp[msbuild_SimpleConsoleLogger#3](../msbuild/codesnippet/CSharp/build-loggers_2.cs)]

## <a name="respond-to-logger-verbosity-values"></a>Rispondere ai valori di dettaglio del logger

In alcuni casi, può essere necessario registrare le informazioni di un evento solo se l'opzione **-verbosity** di MSBuild.exe contiene un determinato valore. In questo esempio, il gestore dell'evento <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> registra un messaggio solo se la proprietà <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A>, impostata dall'opzione **-verbosity** , è uguale a <xref:Microsoft.Build.Framework.LoggerVerbosity>`Detailed`.

[!code-csharp[msbuild_SimpleConsoleLogger#4](../msbuild/codesnippet/CSharp/build-loggers_3.cs)]

## <a name="specify-a-logger"></a>Specificare un logger

Una volta compilato il logger in un assembly, è necessario indicare a MSBuild di usare tale logger durante le compilazioni. Questa operazione può essere eseguita usando l'opzione **-logger** con *MSBuild.exe*. Per altre informazioni sulle opzioni disponibili per *MSBuild.exe*, vedere [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md).

La riga di comando seguente compila il progetto *MyProject.csproj* e usa la classe logger implementata in *SimpleLogger.dll*. L'opzione **-nologo** nasconde il banner e il messaggio di copyright e l'opzione **-noconsolelogger** Disabilita il logger della console MSBuild predefinito.

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll
```

La riga di comando seguente compila il progetto con lo stesso logger, ma con un livello di `Verbosity` impostato su `Detailed`.

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll -verbosity:Detailed
```

## <a name="example"></a>Esempio

### <a name="description"></a>Descrizione

L'esempio seguente contiene il codice completo per il logger.

### <a name="code"></a>Codice

[!code-csharp[msbuild_SimpleConsoleLogger#1](../msbuild/codesnippet/CSharp/build-loggers_4.cs)]

## <a name="example"></a>Esempio

### <a name="description"></a>Descrizione

L'esempio seguente illustra l'implementazione di un logger che scrive il log in un file, anziché visualizzarlo nella finestra di console.

### <a name="code"></a>Codice

[!code-csharp[msbuild_BasicLogger#1](../msbuild/codesnippet/CSharp/build-loggers_5.cs)]

## <a name="see-also"></a>Vedere anche

- [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)
