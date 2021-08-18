---
title: Abilitare o installare analizzatori .NET di terze parti
ms.date: 08/03/2018
description: Informazioni su come abilitare analizzatori .NET di terze parti da .NET SDK o installare questi analizzatori come NuGet pacchetto.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- .NET analyzers
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 25d98bfd0ddbc691c6fbc1ce22a129f9c6cfa692
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122091279"
---
# <a name="enable-or-install-first-party-net-analyzers"></a>Abilitare o installare analizzatori .NET di terze parti

## <a name="overview"></a>Panoramica

Gli analizzatori della piattaforma del compilatore .NET (Roslyn) ispezionano il codice C# o Visual Basic per individuare problemi di stile e di qualità del codice. Gli analizzatori .NET di prima parte sono indipendenti dalla **piattaforma di destinazione.** Ciò significa che il progetto non deve avere come destinazione una piattaforma .NET specifica. Gli analizzatori funzionano per i progetti `net5.0` che hanno come destinazione e versioni precedenti di .NET, ad esempio `netcoreapp` , e `netstandard` `net472` .

È possibile abilitare o installare gli analizzatori .NET di prima parte in uno dei modi seguenti:

- **Abilitare da .NET SDK:** a partire da Visual Studio 2019 16.8 e .NET 5.0, questi analizzatori sono inclusi in [.NET SDK.](/dotnet/fundamentals/code-analysis/overview) L'analisi è abilitata per impostazione predefinita per i progetti che hanno come destinazione .NET 5.0 o versione successiva. È possibile abilitare l'analisi del codice nei progetti che hanno come destinazione versioni precedenti di .NET impostando la proprietà [EnableNETAnalyzers](/dotnet/core/project-sdk/msbuild-props#enablenetanalyzers) di MSBUILD su `true` . È anche possibile disabilitare l'analisi del codice per il progetto impostando `EnableNETAnalyzers` su `false` .

- Installa come pacchetto **NuGet:** se non si vuole passare a .NET 5+ SDK o se si preferisce un modello basato su pacchetti di NuGet, gli analizzatori sono disponibili anche nel pacchetto `Microsoft.CodeAnalysis.NetAnalyzers` [NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) in Visual Studio 2019.  Si potrebbe preferire un modello basato su pacchetto per gli aggiornamenti delle versioni su richiesta. Se si è in Visual Studio 2017, installare invece la versione più recente `2.9.x` `Microsoft.CodeAnalysis.FxCopAnalyzers` [del NuGet versione.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/)

> [!NOTE]
> È consigliabile abilitare gli analizzatori da .NET SDK anziché installare il pacchetto `Microsoft.CodeAnalysis.NetAnalyzers` [NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers), quando possibile. L'abilitazione degli analizzatori da .NET SDK garantisce di ottenere automaticamente le correzioni di bug e i nuovi analizzatori non appena si aggiorna l'SDK. Nel modello NuGet è necessario aggiornare il pacchetto NuGet ogni volta che si desiderano le correzioni di bug più recenti. Il NuGet viene aggiornato più frequentemente.

## <a name="see-also"></a>Vedi anche

- [Panoramica degli analizzatori di codice in Visual Studio](roslyn-analyzers-overview.md)
- [Usare gli analizzatori del codice in Visual Studio](use-roslyn-analyzers.md)
- [Eseguire la migrazione dall'analisi legacy agli analizzatori .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Eseguire la migrazione dagli analizzatori FxCop agli analizzatori .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md)
