---
title: Introduzione a analizzatori di Roslyn | Microsoft Docs
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb224d1c84f9216ed303c919118af4997be2405c
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66835900"
---
# <a name="get-started-with-roslyn-analyzers"></a>Iniziare con gli analizzatori di Roslyn

Con gli analizzatori di codice in tempo reale, basato sul progetto in Visual Studio, gli autori di API possono essere spedite analisi del codice specifico di dominio come parte di ai pacchetti NuGet. Poiché gli analizzatori sono basate su .NET Compiler Platform (nome in codice "Roslyn"), possono produrre avvisi nel codice mentre si digita, anche prima di aver completato la riga (non è più in attesa per compilare il codice per individuare i problemi). Inoltre, gli analizzatori possono emergere una correzione automatica del codice tramite il prompt dei lampadina di Visual Studio per consentire la pulizia del codice immediatamente.

## <a name="get-started"></a>Introduzione

[Panoramica di analizzatori di Roslyn](../code-quality/roslyn-analyzers-overview.md)

[Esercitazione: Scrivere il primo analizzatore e la correzione codice](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[Aggiungere le correzioni del codice procedura dettagliata: Fornire le correzioni degli utenti per i problemi di Analizzatore](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Analizzatore Roslyn reali](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) che è anche possibile guardare come un [parlare](https://channel9.msdn.com/events/Build/2015/3-725)

[Alcuni esempi su GitHub, raggruppati in tre tipi di analizzatori](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)


## <a name="see-also"></a>Vedere anche

- [Riferimento di versione pacchetto della piattaforma del compilatore .NET](roslyn-version-support.md)
- [Più documentazione nel sito GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Regole FxCop implementate con analizzatori di Roslyn](http://roslynanalyzersstatus.azurewebsites.net/)
