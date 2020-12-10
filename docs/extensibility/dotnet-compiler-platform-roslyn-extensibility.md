---
title: '&quot;Estensibilità .NET Compiler Platform (Roslyn &quot; ) | Microsoft Docs'
description: Informazioni sul .NET Compiler Platform, che consente agli strumenti e agli sviluppatori di condividere i compilatori di informazioni dettagliate sui programmi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3bc0ecb6aad5b4da126d5a253a6c0b523444e2c
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994823"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>Estendibilità di .NET Compiler Platform ( &quot; Roslyn &quot; )
La mission principale del .NET Compiler Platform ("Roslyn") consiste nell'aprire i compilatori C# e Visual Basic e consentire agli strumenti e agli sviluppatori di condividere i compilatori di informazioni dettagliate sui programmi. Gli strumenti di analisi del codice migliorano la qualità del codice e i generatori di codice facilitano la costruzione di applicazioni Poiché gli strumenti diventano più intelligenti, devono accedere a una conoscenza approfondita del codice che solo i compilatori posseggono. Anziché essere convertitori opachi (codice sorgente in e codice di oggetto), i compilatori Roslyn offrono API che è possibile usare per le attività correlate al codice negli strumenti e nelle applicazioni.

 Il aspetto migliore è che i compilatori Roslyn, le relative API, gli esempi e le procedure dettagliate e gli strumenti reali basati su queste API sono completamente open source in [github.com/dotnet/Roslyn](https://github.com/dotnet/Roslyn). Visitare il sito OSS per altre informazioni e iniziare a usare Roslyn. Sono disponibili collegamenti per ottenere le funzionalità più recenti di C# e Visual Basic che è possibile usare come utente finale, oltre a collegamenti per iniziare come un generatore di strumenti che sfrutta le API Roslyn.

## <a name="see-also"></a>Vedere anche
- [Introduzione agli analizzatori Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
