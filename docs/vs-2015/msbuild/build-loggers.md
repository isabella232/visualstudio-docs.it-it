---
title: Logger di compilazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2908c8217070196de1b2d3cd4f1c5f8d8f2868a5
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59658890"
---
# <a name="build-loggers"></a>Logger di compilazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I logger consentono di personalizzare l'output della compilazione e visualizzare messaggi, errori o avvisi in risposta a specifici eventi di compilazione. Ogni logger viene implementato come classe .NET che implementa l'interfaccia <xref:Microsoft.Build.Framework.ILogger>, definita nell'assembly Microsoft.Build.Framework.dll.  
  
 È possibile implementare un logger in due modi:  
  
- Implementare direttamente l'interfaccia <xref:Microsoft.Build.Framework.ILogger>.  
  
- Derivare la classe dalla classe di supporto <xref:Microsoft.Build.Utilities.Logger>, definita nell'assembly Microsoft.Build.Utilities.dll. La classe <xref:Microsoft.Build.Utilities.Logger> implementa <xref:Microsoft.Build.Framework.ILogger> e fornisce le implementazioni predefinite di alcuni membri di <xref:Microsoft.Build.Framework.ILogger>.  
  
  Questo argomento illustra come scrivere un logger semplice che deriva dalla classe <xref:Microsoft.Build.Utilities.Logger> e descrive i messaggi visualizzati sulla console in risposta a specifici eventi di compilazione.  
  
## <a name="registering-for-events"></a>Registrazione per gli eventi  
 Lo scopo di un logger è quello di raccogliere informazioni sullo stato di avanzamento della compilazione, così come riportate dal motore di compilazione, e di organizzarle in maniera utile. Tutti i logger devono eseguire l'override del metodo <xref:Microsoft.Build.Utilities.Logger.Initialize%2A>, che corrisponde alla posizione in cui il logger registra gli eventi. In questo esempio il logger registra gli eventi <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> e <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#2](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs#2)]  
  
## <a name="responding-to-events"></a>Risposta agli eventi  
 Il logger è stato registrato per eventi specifici e dovrà gestire questi eventi ogni volta che si verificano. Per gli eventi <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> e <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>, il logger scrive semplicemente una breve frase e il nome del file di progetto interessato dall'evento. Tutti i messaggi provenienti dal logger vengono scritti nella finestra della console.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#3](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs#3)]  
  
## <a name="responding-to-logger-verbosity-values"></a>Risposta ai valori di dettaglio del logger  
 In alcuni casi, è possibile che si voglia registrare le informazioni di un evento solo se l'opzione **/verbosity** di MSBuild.exe contiene un determinato valore. In questo esempio, il gestore dell'evento <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> registra un messaggio solo se la proprietà <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A>, impostata dall'opzione **/verbosity** , è uguale a <xref:Microsoft.Build.Framework.LoggerVerbosity>`Detailed`.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#4](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs#4)]  
  
## <a name="specifying-a-logger"></a>Definizione di un logger  
 Dopo aver compilato il logger in un assembly, è necessario indicare a [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] di usare il logger durante le compilazioni. Questa operazione può essere eseguita usando l'opzione **/logger** con MSBuild.exe. Per altre informazioni sulle opzioni disponibili per MSBuild.exe, vedere [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md).  
  
 La riga di comando seguente compila il progetto `MyProject.csproj` e usa la classe logger implementata in `SimpleLogger.dll`. L'opzione **/nologo** nasconde l'intestazione e il messaggio del copyright, mentre l'opzione **/noconsolelogger** disattiva il logger di console predefinito di [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll  
```  
  
 La riga di comando seguente compila il progetto con lo stesso logger, ma con un livello di `Verbosity` impostato su `Detailed`.  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll /verbosity:Detailed  
```  
  
## <a name="example"></a>Esempio  
  
### <a name="description"></a>Description  
 L'esempio seguente contiene il codice completo per il logger.  
  
### <a name="code"></a>Codice  
 [!code-csharp[msbuild_SimpleConsoleLogger#1](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs#1)]  
  
### <a name="comments"></a>Commenti  
  
## <a name="example"></a>Esempio  
  
### <a name="description"></a>Description  
 L'esempio seguente illustra l'implementazione di un logger che scrive il log in un file, anziché visualizzarlo nella finestra di console.  
  
### <a name="code"></a>Codice  
 [!code-csharp[msbuild_BasicLogger#1](../snippets/csharp/VS_Snippets_Misc/msbuild_BasicLogger/CS/msbuild_BasicLogger.cs#1)]  
  
### <a name="comments"></a>Commenti  
  
## <a name="see-also"></a>Vedere anche  
 [Obtaining Build Logs](../msbuild/obtaining-build-logs-with-msbuild.md)  (Recupero di log di compilazione)  
 [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)
