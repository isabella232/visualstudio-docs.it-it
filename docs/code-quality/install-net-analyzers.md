---
title: Abilitare o installare gli analizzatori .NET di terze parti
ms.date: 08/03/2018
description: Informazioni su come abilitare gli analizzatori .NET di terze parti da .NET SDK o installare questi analizzatori come pacchetto NuGet.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- .NET analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f7dfa1c79af832cc54d9aee72eeafbf20bbde707
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398416"
---
# <a name="enable-or-install-first-party-net-analyzers"></a>Abilitare o installare gli analizzatori .NET di terze parti

## <a name="overview"></a>Panoramica

Gli analizzatori della piattaforma del compilatore .NET (Roslyn) ispezionano il codice C# o Visual Basic per individuare problemi di stile e di qualità del codice. Gli analizzatori .NET della prima entità sono **indipendenti dalla piattaforma di destinazione**. Ovvero non è necessario che il progetto sia destinato a una piattaforma .NET specifica. Gli analizzatori funzionano per i progetti destinati a e per le `net5.0` versioni precedenti di .NET, ad esempio `netcoreapp` , `netstandard` e `net472` .

È possibile abilitare o installare gli analizzatori .NET della prima entità in uno dei modi seguenti:

- **Abilita da .NET SDK**: a partire da Visual Studio 2019 16,8 e .NET 5,0, questi analizzatori sono [inclusi in .NET SDK](/dotnet/fundamentals/code-analysis/overview). Per impostazione predefinita, l'analisi è abilitata per i progetti destinati a .NET 5,0 o versione successiva. È possibile abilitare l'analisi del codice per i progetti destinati a versioni precedenti di .NET impostando la `EnableNETAnalyzers` proprietà su `true` . È anche possibile disabilitare l'analisi del codice per il progetto impostando `EnableNETAnalyzers` su `false` .

- **Installare come pacchetto NuGet**: se non si vuole passare a .NET 5 + SDK o se si preferisce un modello basato su pacchetti NuGet, gli analizzatori sono anche disponibili nel `Microsoft.CodeAnalysis.NetAnalyzers` [pacchetto nuget](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) in Visual Studio 2019.  Per gli aggiornamenti delle versioni su richiesta potrebbe essere preferibile un modello basato su pacchetti. Se si è in Visual Studio 2017, installare invece la `2.9.x` versione più recente del `Microsoft.CodeAnalysis.FxCopAnalyzers` [pacchetto NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) .

> [!NOTE]
> È consigliabile abilitare gli analizzatori di .NET SDK anziché installare il `Microsoft.CodeAnalysis.NetAnalyzers` [pacchetto NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers), quando possibile. L'abilitazione degli analizzatori di .NET SDK consente di ottenere automaticamente le correzioni di bug e i nuovi analizzatori dell'analizzatore appena si aggiorna l'SDK.

## <a name="see-also"></a>Vedere anche

- [Panoramica degli analizzatori di codice in Visual Studio](roslyn-analyzers-overview.md)
- [Usare gli analizzatori del codice in Visual Studio](use-roslyn-analyzers.md)
- [Eseguire la migrazione dall'analisi legacy agli analizzatori .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Eseguire la migrazione dagli analizzatori FxCop agli analizzatori .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md)
