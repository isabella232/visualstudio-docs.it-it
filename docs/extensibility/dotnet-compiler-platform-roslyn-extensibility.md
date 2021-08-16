---
title: .NET Compiler Platform ( &quot; Roslyn &quot; ) Extensibility | Microsoft Docs
description: Informazioni sull'.NET Compiler Platform, che consente a strumenti e sviluppatori di condividere informazioni dettagliate sui programmi dei compilatori.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b09aa03ae6af6789ddcc87dc60797af5eda3f19bcde6148dd7bfe1b568b7f0f2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121388929"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>estendibilità di .NET Compiler Platform ( &quot; Roslyn &quot; )
L'obiettivo principale del .NET Compiler Platform ("Roslyn") è l'apertura dei compilatori C# e Visual Basic e la possibilità di condividere strumenti e sviluppatori nelle informazioni dettagliate dei compilatori sui programmi. Gli strumenti di analisi del codice migliorano la qualità del codice e i generatori di codice consentono la costruzione di applicazioni. Con l'essere più intelligenti, gli strumenti hanno bisogno di accedere a una conoscenza sempre più approfondita del codice di cui dispongono solo i compilatori. Invece di essere traduttori opachi (codice sorgente in e codice oggetto in uscita), i compilatori Roslyn offrono API che è possibile usare per le attività correlate al codice negli strumenti e nelle applicazioni.

 La parte migliore è che i compilatori Roslyn, le relative API, esempi e procedure dettagliate e gli strumenti reali creati in base a queste API sono tutti completamente open source in [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn). Per altre informazioni e per iniziare a usare Roslyn, visitare il sito OSS. Sono disponibili collegamenti per ottenere le funzionalità di C# e Visual Basic più recenti che è possibile usare come utente finale, nonché collegamenti per iniziare come generatore di strumenti sfruttando le API Roslyn.

## <a name="see-also"></a>Vedi anche
- [Introduzione a Analizzatori Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
