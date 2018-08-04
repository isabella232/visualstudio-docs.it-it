---
title: Introduzione a analizzatori di Roslyn | Microsoft Docs
ms.date: 04/02/2018
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 12c1bba1d07ab695f265425d6aeae6806589dcd4
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497849"
---
# <a name="get-started-with-roslyn-analyzers"></a>Iniziare con gli analizzatori di Roslyn

Con gli analizzatori di codice in tempo reale, basato sul progetto in Visual Studio, gli autori di API possono essere spedite analisi del codice specifico di dominio come parte di ai pacchetti NuGet. Poiché gli analizzatori sono basate su .NET Compiler Platform (nome in codice "Roslyn"), possono produrre avvisi nel codice mentre si digita, anche prima di aver completato la riga (non è più in attesa per compilare il codice per individuare i problemi). Inoltre, gli analizzatori possono emergere una correzione automatica del codice tramite il prompt dei lampadina di Visual Studio per consentire la pulizia del codice immediatamente.

## <a name="get-started"></a>Introduzione

[Procedura dettagliata e introduzione di analizzatori di Roslyn codice in tempo reale](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Aggiungere codice corregge procedura dettagliata: ottenere le correzioni degli utenti ai problemi di Analizzatore](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Introduzione e una procedura dettagliata dell'analizzatore reali di comunicare con](http://channel9.msdn.com/events/Build/2015/3-725)

[Analizzatore Roslyn reali](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) che è anche possibile guardare come un [parlare](http://channel9.msdn.com/events/Build/2015/3-725)

[Alcuni esempi su github, raggruppati in tre tipi di analizzatori](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Introduzione e panoramica di alcuni analizzatori parlare](http://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="see-also"></a>Vedere anche

- [Panoramica di analizzatori di Roslyn](../code-quality/roslyn-analyzers-overview.md)
- [Più documentazione nel sito github OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Regole FxCop implementate con analizzatori di Roslyn su GitHub](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)