---
title: Abilitare o installare gli analizzatori .NET
ms.date: 08/03/2018
description: Informazioni su come abilitare gli analizzatori .NET da .NET SDK o installare questi analizzatori come pacchetto NuGet.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- .NET analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a14d89caba498a07c2447f9df1109e4da9f6a466
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/25/2020
ms.locfileid: "96112239"
---
# <a name="enable-or-install-net-analyzers"></a>Abilitare o installare gli analizzatori .NET

## <a name="overview"></a>Panoramica

Gli analizzatori della piattaforma del compilatore .NET (Roslyn) ispezionano il codice C# o Visual Basic per individuare problemi di stile e di qualità del codice. È possibile abilitare o installare questi analizzatori in uno dei modi seguenti:

- **Abilita da .NET SDK**: a partire da Visual Studio 2019 16,8 e .NET 5,0, questi analizzatori sono [inclusi in .NET SDK](/dotnet/fundamentals/code-analysis/overview). Per impostazione predefinita, l'analisi è abilitata per i progetti destinati a .NET 5,0 o versione successiva. È possibile abilitare l'analisi del codice per i progetti destinati a versioni precedenti di .NET impostando la `EnableNETAnalyzers` proprietà su `true` . È anche possibile disabilitare l'analisi del codice per il progetto impostando `EnableNETAnalyzers` su `false` .

- **Installare come pacchetto NuGet**: in alternativa, è possibile installare questi analizzatori installando il `Microsoft.CodeAnalysis.NetAnalyzers` [pacchetto nuget](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) in Visual Studio 2019. Se si è in Visual Studio 2017, installare la versione più recente `2.9.x` del `Microsoft.CodeAnalysis.FxCopAnalyzers` [pacchetto NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/).

> [!NOTE]
> È consigliabile abilitare gli analizzatori di .NET SDK anziché installare il `Microsoft.CodeAnalysis.NetAnalyzers` [pacchetto NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers), quando possibile. L'abilitazione degli analizzatori di .NET SDK consente di ottenere automaticamente le correzioni di bug e i nuovi analizzatori dell'analizzatore appena si aggiorna l'SDK.

## <a name="see-also"></a>Vedere anche

- [Panoramica degli analizzatori di codice in Visual Studio](roslyn-analyzers-overview.md)
- [Usare gli analizzatori del codice in Visual Studio](use-roslyn-analyzers.md)
- [Eseguire la migrazione dall'analisi legacy agli analizzatori .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Eseguire la migrazione da analizzatori FxCop ad analizzatori .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md)
