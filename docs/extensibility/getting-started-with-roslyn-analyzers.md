---
title: Introduzione con gli analizzatori Roslyn | Microsoft Docs
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d572c49f7d528b9dbb624bf31ad5e28dc3799aa
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012243"
---
# <a name="get-started-with-roslyn-analyzers"></a>Introduzione agli analizzatori Roslyn

Con gli analizzatori di codice dinamici basati su progetti in Visual Studio, gli autori di API possono inviare analisi del codice specifiche del dominio come parte dei pacchetti NuGet. Poiché questi analizzatori sono basati sulla .NET Compiler Platform (nome in codice "Roslyn"), possono produrre avvisi nel codice mentre si digita anche prima di aver terminato la riga (non è più in attesa di compilare il codice per individuare i problemi). Gli analizzatori possono anche visualizzare una correzione automatica del codice tramite il prompt della lampadina di Visual Studio per consentire di pulire immediatamente il codice.

## <a name="get-started"></a>Introduzione

[Panoramica degli analizzatori Roslyn](../code-quality/roslyn-analyzers-overview.md)

[Esercitazione: compilare il primo analizzatore con correzione del codice](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[Procedura dettagliata per aggiungere correzioni di codice: fornire correzioni agli utenti per i problemi dell'analizzatore](/archive/msdn-magazine/2015/february/csharp-adding-a-code-fix-to-your-roslyn-analyzer)

[Real World Roslyn Analyzer](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) , che puoi guardare anche come una [discussione](https://channel9.msdn.com/events/Build/2015/3-725)

[Alcuni esempi su GitHub, raggruppati in tre tipi di analizzatori](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>Vedere anche

- [Riferimento per la versione del pacchetto .NET Compiler Platform](roslyn-version-support.md)
- [Altri documenti sul sito di GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Regole FxCop implementate con gli analizzatori Roslyn](../code-quality/fxcop-rule-port-status.md)