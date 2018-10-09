---
title: .NET compiler Platform (&quot;Roslyn&quot;) estendibilità | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6ec9dbcd905bce347b5852a6e011ee43795d83fe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518052"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET compiler Platform (&quot;Roslyn&quot;) Extensibility
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [.NET Compiler Platform (&quot;Roslyn&quot;) estendibilità](https://docs.microsoft.com/visualstudio/extensibility/dotnet-compiler-platform-roslyn-extensibility).  
  
Lo scopo fondamentale di .NET Compiler Platform ("Roslyn") è di aprire i compilatori c# e Visual Basic e consentendo di strumenti e agli sviluppatori di condividere i compilatori di informazioni dettagliate sui programmi. Strumenti di analisi codice migliorare la qualità del codice e generatori aiuto nella costruzione dell'applicazione del codice. Man mano che strumenti acquisisce più intelligenti, devono accedere a più e più della conoscenza di codice avanzato che possiedono solo dai compilatori. Anziché essere opachi traduttori (codice sorgente e oggetto codice out), i compilatori Roslyn offrono API che è possibile usare per le attività correlate a codice negli strumenti e applicazioni.  
  
 L'aspetto più interessante è che i compilatori Roslyn, le relative API, esempi e procedure dettagliate e gli strumenti reali partendo da queste API sono tutte completamente open source in [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn). Visitare il sito di SharePoint Server per altre informazioni e iniziare a usare Roslyn. Sono disponibili collegamenti per ottenere le funzionalità di Visual Basic che è possibile usare come un utente finale e più recenti c#, nonché i collegamenti per iniziare a usare come generatore strumento sfruttando APIs Roslyn.  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione agli analizzatori di Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
