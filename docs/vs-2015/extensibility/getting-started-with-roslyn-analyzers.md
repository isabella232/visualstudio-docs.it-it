---
title: Guida introduttiva agli analizzatori di Roslyn Documenti Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a712697bafefcf115ce10d110c0ef3a4270c6acd
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444981"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Introduzione agli analizzatori Roslyn
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con analizzatori di codice in tempo reale e basati su progetti in Visual Studio, gli autori di API possono spedire l'analisi del codice specifica del dominio come parte dei pacchetti NuGet.  Poiché questi analizzatori sono alimentati dalla piattaforma del compilatore .NET (nome in codice "Roslyn"), possono produrre avvisi nel codice durante la digitazione anche prima di aver completato la riga (non più in attesa di compilare il codice per individuare i problemi).  Gli analizzatori possono anche esporre una correzione automatica del codice tramite il prompt lampadina di Visual Studio per consentire di pulire il codice immediatamente

## <a name="getting-started"></a>Introduzione
[Introduzione e procedura dettagliata di Roslyn Live Code Analyzers](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Aggiunta di correzioni di codice procedura dettagliata: fornire agli utenti correzioni per i problemi dell'analizzatoreAdding Code Fixes Walkthrough: Provide Users Fixes for Analyzer Issues](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Introduzione e procedura dettagliata di Real World Analyzer Talk](https://channel9.msdn.com/events/Build/2015/3-725)

[Analizzatore di Roslyn del mondo reale](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) che si può anche guardare come un [discorso](https://channel9.msdn.com/events/Build/2015/3-725)

[Diversi esempi su GitHub, raggruppati in tre tipi di analizzatori](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Introduzione e tour di pochi analizzatori Parlare](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>Risorse aggiuntive
[Altri documenti sul sito GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[Regole FxCop implementate con analizzatori Roslyn su GitHub](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
