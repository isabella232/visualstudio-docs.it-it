---
title: '&quot;Estensibilità .NET Compiler Platform (Roslyn &quot; ) | Microsoft Docs'
description: Informazioni sul .NET Compiler Platform, che consente agli strumenti e agli sviluppatori di condividere i compilatori di informazioni dettagliate sui programmi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8c0286bb35f8a58a2f5fd6cfa95cff62d523567c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883558"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>Estendibilità di .NET Compiler Platform ( &quot; Roslyn &quot; )
La mission principale del .NET Compiler Platform ("Roslyn") consiste nell'aprire i compilatori C# e Visual Basic e consentire agli strumenti e agli sviluppatori di condividere i compilatori di informazioni dettagliate sui programmi. Gli strumenti di analisi del codice migliorano la qualità del codice e i generatori di codice facilitano la costruzione di applicazioni Poiché gli strumenti diventano più intelligenti, devono accedere a una conoscenza approfondita del codice che solo i compilatori posseggono. Anziché essere convertitori opachi (codice sorgente in e codice di oggetto), i compilatori Roslyn offrono API che è possibile usare per le attività correlate al codice negli strumenti e nelle applicazioni.

 Il aspetto migliore è che i compilatori Roslyn, le relative API, gli esempi e le procedure dettagliate e gli strumenti reali basati su queste API sono completamente open source in [github.com/dotnet/Roslyn](https://github.com/dotnet/Roslyn). Visitare il sito OSS per altre informazioni e iniziare a usare Roslyn. Sono disponibili collegamenti per ottenere le funzionalità più recenti di C# e Visual Basic che è possibile usare come utente finale, oltre a collegamenti per iniziare come un generatore di strumenti che sfrutta le API Roslyn.

## <a name="see-also"></a>Vedi anche
- [Introduzione agli analizzatori Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
