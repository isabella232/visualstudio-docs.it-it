---
title: Estensibilità&quot;della&quot;piattaforma del compilatore .NET ( Roslyn ) Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62ceac6e2be8a0a84d82f6b86b685c7c8b20a182
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712071"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>Estensibilità&quot;della&quot;piattaforma del compilatore .NET ( Roslyn )
La missione principale della piattaforma del compilatore .NET ("Roslyn") sta aprendo i compilatori di C e Visual Basic e consentendo agli strumenti e agli sviluppatori di condividere le informazioni avanzate che i compilatori hanno sui programmi. Gli strumenti di analisi del codice migliorano la qualità del codice e i generatori di codice facilitano la costruzione dell'applicazione. Man mano che gli strumenti diventano più intelligenti, hanno bisogno di accedere a un numero sempre maggiore di conoscenze approfondite sul codice che solo i compilatori possiedono. Invece di essere traduttori opachi (codice sorgente in e codice oggetto out), i compilatori Roslyn offrono API che è possibile utilizzare per le attività relative al codice negli strumenti e nelle applicazioni.

 La parte migliore è che i compilatori Roslyn, le loro API, esempi e procedure dettagliate, e gli strumenti reali compilati in cima a queste API sono tutti completamente open source a [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn). Si prega di visitare il sito OSS per saperne di più e iniziare con Roslyn. Sono disponibili collegamenti per ottenere le funzionalità più recenti di C e Visual Basic che è possibile utilizzare come utente finale, nonché collegamenti per iniziare come generatore di strumenti sfruttando le API Roslyn.

## <a name="see-also"></a>Vedere anche
- [Introduzione agli analizzatori Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
