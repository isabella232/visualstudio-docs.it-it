---
title: Attività iniziali con Roslyn Analyzers | Microsoft Docs
description: Usare queste risorse per iniziare a usare gli analizzatori Roslyn in Visual Studio; include un'esercitazione e diversi esempi.
ms.custom: SEO-VS-2020
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d5210da636a32ecdbd67e16260db63853451c774c3004b02035b966d98e5ceff
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414740"
---
# <a name="get-started-with-roslyn-analyzers"></a>Introduzione a Analizzatori Roslyn

Con gli analizzatori di codice basati su progetto in tempo reale Visual Studio, gli autori di API possono spedire l'analisi del codice specifica del dominio come parte dei NuGet pacchetti. Poiché questi analizzatori sono basati sul .NET Compiler Platform (denominato in codice "Roslyn"), possono generare avvisi nel codice durante la digitazione anche prima di aver completato la riga (non più in attesa di compilare il codice per individuare i problemi). Gli analizzatori possono anche visualizzare una correzione automatica del codice tramite il prompt Visual Studio lampadina per consentire la pulizia immediata del codice.

## <a name="get-started"></a>Introduzione

[Panoramica degli analizzatori Roslyn](../code-quality/roslyn-analyzers-overview.md)

[Esercitazione: compilare il primo analizzatore con correzione del codice](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[Procedura dettagliata per l'aggiunta di correzioni di codice: fornire agli utenti correzioni per i problemi dell'analizzatore](/archive/msdn-magazine/2015/february/csharp-adding-a-code-fix-to-your-roslyn-analyzer)

[Analizzatore Roslyn reale](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) che è anche possibile guardare come [conversazione](https://channel9.msdn.com/events/Build/2015/3-725)

[Diversi esempi su GitHub, raggruppati in tre tipi di analizzatori](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento sulla versione del pacchetto della piattaforma del compilatore .NET](roslyn-version-support.md)
- [Altri documenti nel sito GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Regole FxCop implementate con gli analizzatori Roslyn](../code-quality/fxcop-rule-port-status.md)
