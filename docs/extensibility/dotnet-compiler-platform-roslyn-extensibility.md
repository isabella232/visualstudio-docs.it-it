---
title: .NET Compiler Platform ( &quot; Roslyn &quot; ) Estendibilità | Microsoft Docs
description: Informazioni sul .NET Compiler Platform, che consente agli strumenti e agli sviluppatori di condividere informazioni dettagliate sui programmi dei compilatori.
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
ms.openlocfilehash: d04383359133e64ec97fecc1ca0eb8082fcd42c2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152484"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET Compiler Platform ( &quot; Roslyn &quot; ) estendibilità
La mission principale del .NET Compiler Platform ("Roslyn") è l'apertura dei compilatori C# e Visual Basic e consente a strumenti e sviluppatori di condividere le informazioni dettagliate che i compilatori hanno sui programmi. Gli strumenti di analisi del codice migliorano la qualità del codice e i generatori di codice consentono la costruzione di applicazioni. Con l'essere più intelligenti, gli strumenti hanno bisogno di accedere sempre più alle conoscenze approfondite del codice che solo i compilatori possiedono. Invece di essere traduttori opachi (codice sorgente in e codice oggetto), i compilatori Roslyn offrono API che è possibile usare per le attività correlate al codice negli strumenti e nelle applicazioni.

 La parte migliore è che i compilatori Roslyn, le RELATIVE API, gli esempi e le procedure dettagliate e gli strumenti reali creati su queste API sono tutti completamente open source in [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn). Visitare il sito OSS per altre informazioni e iniziare a usare Roslyn. Sono disponibili collegamenti per ottenere le funzionalità più recenti di C# e Visual Basic che è possibile usare come utente finale, nonché collegamenti per iniziare a usare le API Roslyn come generatore di strumenti.

## <a name="see-also"></a>Vedi anche
- [Introduzione a Analizzatori Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
