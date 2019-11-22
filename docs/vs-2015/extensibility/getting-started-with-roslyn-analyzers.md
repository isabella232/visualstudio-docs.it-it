---
title: Introduzione con gli analizzatori Roslyn | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2d45491fe031c01a31812f5ed4944f76d059cd60
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300020"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Introduzione agli analizzatori Roslyn
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con gli analizzatori di codice dinamici basati su progetti in Visual Studio, gli autori di API possono inviare analisi del codice specifiche del dominio come parte dei pacchetti NuGet.  Poiché questi analizzatori sono basati sulla .NET Compiler Platform (nome in codice "Roslyn"), possono produrre avvisi nel codice mentre si digita anche prima di aver terminato la riga (non è più in attesa di compilare il codice per individuare i problemi).  Gli analizzatori possono anche esporre una correzione automatica del codice tramite il prompt di Visual Studio Light Bulb per consentire la pulizia immediata del codice

## <a name="getting-started"></a>Introduzione
[Introduzione e procedura dettagliata degli analizzatori del codice in tempo reale di Roslyn](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Aggiunta di correzioni al codice procedura dettagliata: fornire correzioni agli utenti per i problemi dell'analizzatore](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Introduzione e procedura dettagliata della discussione di Real World Analyzer](https://channel9.msdn.com/events/Build/2015/3-725)

[Real World Roslyn Analyzer](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) , che puoi guardare anche come una [discussione](https://channel9.msdn.com/events/Build/2015/3-725)

[Alcuni esempi su GitHub, raggruppati in tre tipi di analizzatori](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Introduzione e presentazione di alcuni analizzatori Talk](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>Altre risorse
[Altri documenti sul sito di GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[Regole FxCop implementate con gli analizzatori Roslyn in GitHub](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
