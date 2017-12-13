---
title: "Migliorare la qualità del codice | Microsoft Docs"
ms.custom: na
ms.date: 02/17/2017
ms.reviewer: na
ms.suite: na
ms.technology: vs-devops-test
ms.tgt_pltfrm: na
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- team-based development
ms.assetid: 73baa961-c21f-43fe-bb92-3f59ae9b5945
caps.latest.revision: "39"
ms.author: douge
manager: douge
ms.openlocfilehash: 93847beaef971f9370d59a8c5c8ac9f3a59a0967
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="improve-code-quality"></a>Migliorare la qualità del codice
Che cos'è la qualità del codice? Precisione, manutenibilità e anche eleganza sono tutti aspetti di cui tenere conto per la creazione di codice eccellente. Indipendentemente dalla definizione, gli strumenti di test di Visual Studio consentono allo sviluppatore e al team di creare e gestire standard elevati di eccellenza del codice.  
  
 **Requisiti**  
  
-   Alcuni degli strumenti e delle funzionalità descritte in questa sezione sono disponibili solo in edizioni specifiche di Visual Studio e non in tutte le versioni. I requisiti di edizione specifici sono elencati nella documentazione per questi strumenti e funzionalità.  
  
## <a name="in-this-section"></a>In questa sezione  
 Nella tabella seguente sono riportate descrizioni di attività comuni e collegamenti a informazioni aggiuntive sulla corretta esecuzione di queste attività.  
  
|||  
|-|-|  
|[Eseguire unit test del codice](../test/unit-test-your-code.md)|Esplora test facilita l'integrazione degli unit test nelle procedure di sviluppo. È possibile utilizzare il framework per unit test di Microsoft o uno tra i diversi framework di terze parti o open source.|  
|[Live Unit Testing con Visual Studio](../test/live-unit-testing.md)|Live Unit Testing consente di eseguire automaticamente unit test in background e di visualizzare graficamente i risultati di code coverage e test nell'editor del codice di Visual Studio.|  
|[Analisi della qualità delle applicazioni](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|Gli strumenti di analisi del codice statico trovano errori di progettazione, utilizzo, gestibilità e stile nel codice C++ e gestito. Molti di questi problemi possono causare bug che sono difficili da riprodurre nell'ambiente di test standard.|  
|[Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|La metrica del codice è un insieme di misure del software in grado di fornire agli sviluppatori una migliore comprensione del codice che stanno sviluppando. Le metriche includono un indice di manutenibilità per funzioni e classi, complessità ciclomatica di funzioni, profondità dell'ereditarietà delle classi e quantità di accoppiamenti tra le classi.|  
  
## <a name="related-scenarios"></a>Scenari correlati  
 [Panoramica di DevOps per Team Services e TFS](https://www.visualstudio.com/docs/devops-alm-overview)  
 Se non si ha familiarità con Visual Studio Team Foundation e Visual Studio Team Services, è possibile acquisire ulteriori informazioni sul loro uso in un ambiente di sviluppo team per migliorare la produttività e ridurre i rischi correlati allo sviluppo dell'applicazione.  
  
 [Analisi e modellazione dell'architettura](../modeling/analyze-and-model-your-architecture.md)  
 È possibile utilizzare [!INCLUDE[vsPreExt](../test/includes/vspreext_md.md)] per gestire le problematiche e le difficoltà legate alla progettazione del software. [!INCLUDE[vsPreShort](../test/includes/vspreshort_md.md)] consente di modellare visivamente l'applicazione, sia nello stato attuale sia nello stato futuro. È possibile creare e gestire diagrammi con i quali visualizzare i modelli logici dell'applicazione mentre vengono mappati ai modelli fisici allo scopo di poter modificare, convalidare e analizzare il software in fase di progettazione.  
  
 [Test dell'applicazione](https://www.visualstudio.com/docs/test/overview)  
 È possibile utilizzare [!INCLUDE[vsPreShort](../test/includes/vspreshort_md.md)] e [!INCLUDE[vsUltShort](../test/includes/vsultshort_md.md)] per migliorare la produttività nell'intero ciclo di vita dei test. [!INCLUDE[vsPreShort](../test/includes/vspreshort_md.md)] o [!INCLUDE[vsUltShort](../test/includes/vsultshort_md.md)] consentono di pianificare il lavoro di test richiesto. È possibile creare, gestire, modificare ed eseguire sia test manuali che automatici. È inoltre possibile rivedere lo stato di avanzamento dei test in base al piano.  
  
 [Protezione dell'applicazione con PreEmptive Protection - Dotfuscator](../ide/dotfuscator/index.md)  
 È possibile usare la versione gratuita di Dotfuscator Community Edition per proteggere segreti commerciali e altri dati di proprietà intellettuale, ridurre gli attacchi di pirateria e i rischi di contraffazione, nonché evitare manomissioni e operazioni di debug non autorizzate.  Dotfuscator offre funzionalità per la protezione avanzata degli assembly compilati senza richiedere altre attività di programmazione e nemmeno l'accesso al codice sorgente.
  
 [Compilazione dell'applicazione](https://www.visualstudio.com/docs/build/overview)  
 È possibile utilizzare [!INCLUDE[esprbuild](../test/includes/esprbuild_md.md)] per creare e gestire compilazioni automatiche per il codice. [!INCLUDE[esprbuild](../test/includes/esprbuild_md.md)] consente di creare ed eliminare server per distribuire le compilazioni. Inoltre, è possibile analizzare le tendenze di compilazione.  
  
 [Tenere traccia del lavoro tramite Visual Studio Online o Team Foundation Server](https://www.visualstudio.com/docs/work/overview)  
 È possibile utilizzare [!INCLUDE[vstsTfsLong](../test/includes/vststfslong_md.md)] per pianificare e tenere traccia dei progetti sia che si utilizzi il processo Agile, il processo formale o una variazione dei due. Pianificando i progetti, tenendo traccia dello stato di avanzamento rispetto al piano e apportando le modifiche necessarie, è possibile ridurre i rischi, evitare imprevisti e gestire il costo dei progetti.
