---
title: Guida introduttiva agli analizzatori di Roslyn Documenti Microsoft
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc975ff4f142b85297c20f16ac399fce588c093b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711265"
---
# <a name="get-started-with-roslyn-analyzers"></a>Introduzione agli analizzatori Roslyn

Con analizzatori di codice in tempo reale e basati su progetti in Visual Studio, gli autori di API possono spedire l'analisi del codice specifica del dominio come parte dei pacchetti NuGet. Poiché questi analizzatori sono alimentati dalla piattaforma del compilatore .NET (nome in codice "Roslyn"), possono produrre avvisi nel codice durante la digitazione anche prima di aver completato la riga (non più in attesa di compilare il codice per individuare i problemi). Gli analizzatori possono anche esporre una correzione automatica del codice tramite il prompt lampadina di Visual Studio per consentire di pulire immediatamente il codice.

## <a name="get-started"></a>Introduzione

[Panoramica degli analizzatori Roslyn](../code-quality/roslyn-analyzers-overview.md)

[Esercitazione: compilare il primo analizzatore con correzione del codice](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[Aggiungere le correzioni di codice Procedura dettagliata: fornire agli utenti correzioni per i problemi dell'analizzatoreAdd code fixes Walkthrough: Provide users fixes for analyzer issues](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Analizzatore Roslyn del mondo reale](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) che puoi anche guardare come un [discorso](https://channel9.msdn.com/events/Build/2015/3-725)

[Diversi esempi su GitHub, raggruppati in tre tipi di analizzatori](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>Vedere anche

- [Informazioni di riferimento sulla versione del pacchetto della piattaforma del compilatore .NET.NET compiler platform package version reference](roslyn-version-support.md)
- [Altri documenti sul sito GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Regole FxCop implementate con gli analizzatori Roslyn](../code-quality/fxcop-rule-port-status.md)
