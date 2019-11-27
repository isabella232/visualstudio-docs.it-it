---
title: Application Lifecycle Management (ALM) con app Xamarin | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: ff978cc2-5a25-46d6-921b-e51adaa65992
caps.latest.revision: 16
ms.author: crdun
manager: crdun
ms.openlocfilehash: 1a0ea4f611c5312331fa0e2f2f467b4189778f30
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300027"
---
# <a name="application-lifecycle-management-alm-with-xamarin-apps"></a>Application Lifecycle Management (ALM) con app Xamarin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Xamarin consente di compilare le app per dispositivi mobili multipiattaforma destinate ad Android, iOS e Windows con C#, .NET e Visual Studio. Xamarin consente di condividere la maggior parte del codice tra le piattaforme e solo una piccola percentuale di codice rimane specifica della piattaforma. Per altre informazioni su Xamarin, vedere [Visual Studio e Xamarin](../cross-platform/visual-studio-and-xamarin.md).  
  
 Lo sviluppo di app per piattaforme moderne comporta molte più attività rispetto alla semplice scrittura di codice. Queste attività definite DevOps (Development + Operations) si estendono per il ciclo di vita completo di un'app e includono pianificazione e tracciatura del lavoro, progettazione e implementazione di codice, gestione di un repository di codice sorgente, esecuzione di compilazioni, gestione di integrazioni e distribuzioni continue, test (tra cui unit test e test dell'interfaccia utente), esecuzione di varie forme di diagnostica in ambienti di sviluppo e produzione e monitoraggio delle prestazioni delle app e comportamenti dell'utente in tempo reale tramite telemetria e analisi dei dati.  
  
 Visual Studio insieme a Visual Studio Team Services e Team Foundation Server offrono un'ampia gamma di funzionalità DevOps, definita anche Application Lifecycle Management o ALM. Molti di queste sono interamente applicabili ai progetti multipiattaforma.  
  
 Ciò è particolarmente vero con le app Xamarin poiché vengono compilate con C# e .NET per i quali sono compilati alcuni strumenti ALM. Altri strumenti richiedono una stretta integrazione con gli ambienti di runtime e di compilazione. Poiché le app Xamarin vengono eseguite su piattaforme non Windows e usano l'implementazione Mono di .NET, Xamarin offre strumenti specializzati per determinate esigenze.  
  
 Le tabelle seguenti identificano le funzionalità ALM di Visual Studio di cui è possibile prevedere il corretto funzionamento con un progetto Xamarin e quelle che invece presentano limitazioni. Per informazioni dettagliate sulle funzionalità fare riferimento alla documentazione collegata.  
  
## <a name="agile-tools"></a>Strumenti Agile:  
 Collegamento di riferimento: **[Lavoro](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)** (usando Visual Studio Team Services o TFS, incluso Team Explorer Everywhere)  
  
 Commento generale: tutte le funzionalità di pianificazione e traccia sono indipendenti dal tipo di progetto e dai linguaggi di codifica.  
  
|Caratteristica|Supportato con Xamarin|Commenti aggiuntivi|  
|-------------|----------------------------|-------------------------|  
|Gestione di backlog e sprint|Sì||  
|Verifica del lavoro|Sì||  
|Collaborazione nella chat team|Sì||  
|Bacheche Kanban|Sì||  
|Segnalare e visualizzare lo stato di avanzamento|Sì||  
  
## <a name="modeling"></a>Modellazione  
 Collegamento di riferimento: **[Analisi e modellazione dell'architettura](../modeling/analyze-and-model-your-architecture.md)**  
  
 Le funzionalità di progettazione sono indipendenti dal linguaggio di codifica o funzionano con i linguaggi .NET come C#. Per informazioni sugli aspetti correlati al codice, vedere [Ruoli dei diagrammi dell'architettura e della modellazione nello sviluppo del software](../modeling/scenario-change-your-design-using-visualization-and-modeling.md#ModelingDiagramsTools).  
  
|Caratteristica|Supportato con Xamarin|Commenti aggiuntivi|  
|-------------|----------------------------|-------------------------|  
|Diagrammi sequenza|Sì||  
|Grafici delle dipendenze|Sì||  
|Gerarchia di chiamata|Sì||  
|Progettazione classi|Sì||  
|Esplora architettura|Sì||  
|Diagrammi UML (caso di utilizzo, attività, classe, componente, sequenza e DSL)|Sì||  
|Diagrammi livello|Sì||  
|Convalida dei livelli|Sì||  
  
## <a name="code"></a>Codice  
  
|Caratteristica|Supportato con Xamarin|Commenti aggiuntivi|  
|-------------|----------------------------|-------------------------|  
|[Usare il controllo della versione di Team Foundation](https://msdn.microsoft.com/library/1d629052-c65d-4c5d-81eb-eaa4413fe285) o di Visual Studio Team Services|Sì||  
|[Introduzione a Git in Team Services](https://msdn.microsoft.com/library/32f46ecd-1b03-4ef0-a9c4-8a120da2b03f)|Sì||  
|[Analisi del codice/migliorare la qualità del codice (riferimenti, modifiche suggerite e così via)](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|Sì||  
|[Trovare le modifiche apportate al codice e altri elementi della cronologia](../ide/find-code-changes-and-other-history-with-codelens.md)|Sì|Ad eccezione dei limiti specifici tra le piattaforme dove l'implementazione viene risolta solo dopo la fase di esecuzione.|  
|[Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)|Sì||  
  
## <a name="build"></a>Compila  
 Collegamento di riferimento: **[Compilazione](/azure/devops/pipelines/index)**  
  
|Caratteristica|Supportato con Xamarin|Commenti aggiuntivi|  
|-------------|----------------------------|-------------------------|  
|Server TFS locale|Sì|È necessario che nei computer di compilazione sia installato Xamarin e che i computer possano essere collegati a un computer OSX per la compilazione con iOS. Vedere [Configurazione di TFS per Xamarin](https://docs.microsoft.com/azure/devops/repos/tfvc/overview?view=azure-devops) (sito Web Xamarin)|  
|Server di compilazione locale collegato a Visual Studio Team Services|Sì|Per istruzioni, vedere [Server di compilazione](https://msdn.microsoft.com/library/2d258a0a-f178-4e93-9da1-eba61151af3c).|  
|Servizio controller ospitato di Visual Studio Team Services|Sì|Vedere [Build your Xamarin app](https://www.visualstudio.com/docs/build/apps/mobile/xamarin) (Compilare l'app Xamarin).|  
|Definizioni di compilazione con pre e post script|Sì||  
|Integrazione continuata incluse le archiviazioni gestite|Sì|Archiviazioni gestite per TFVC solo quando Git elabora un modello di richiesta di pull anziché le archiviazioni.|  
  
## <a name="testing"></a>Test  
 Collegamento di riferimento: **[Test dell'applicazione](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)**  
  
|Caratteristica|Supportato con Xamarin|Commenti aggiuntivi|  
|-------------|----------------------------|-------------------------|  
|Pianificazione dei test, creazione di test case e organizzazione di gruppi di test|Sì||  
|Test manuali|Sì||  
|Test Manager (registrazione e riproduzione di test)|Sì|Solo dispositivi Windows ed emulatori Android da Visual Studio. È possibile la registrazione per tutti i dispositivi con [Xamarin Test Recorder](https://www.xamarin.com/test-cloud/recorder).|  
|Code coverage|N/D||  
|[Eseguire unit test del codice](../test/unit-test-your-code.md)|Sì|Per destinazioni Windows e Android, è possibile usare gli strumenti incorporati MSTest. Per eseguire unit test in Windows, Android e iOS, Xamarin consiglia NUnit. Vedere [Configurazione di TFS per Xamarin](https://docs.microsoft.com/azure/devops/repos/tfvc/overview?view=azure-devops) (sito Web Xamarin).|  
|[Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)|Solo Windows|La registrazione dei test dell'interfaccia utente di Visual Studio è disponibile solo per Windows. Per tutte le piattaforme, vedere [Xamarin Test Recorder](https://www.xamarin.com/test-cloud/recorder).|  
  
## <a name="improve-code-quality"></a>Migliorare la qualità del codice  
 Collegamento di riferimento: **[Migliorare la qualità del codice](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)**  
  
|Caratteristica|Supportato con Xamarin|Commenti aggiuntivi|  
|-------------|----------------------------|-------------------------|  
|[Analisi della qualità del codice gestito](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Sì||  
|[Ricerca del codice duplicato mediante il rilevamento del clone di codice](https://msdn.microsoft.com/library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Sì||  
|[Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Sì||  
|[Esplora prestazioni](../profiling/performance-explorer.md)|No|Usare invece il [Profiler Xamarin](https://docs.microsoft.com/xamarin/cross-platform/deploy-test/) tramite Xamarin Studio. Si noti che il Profiler Xamarin è attualmente in versione di anteprima e non funziona ancora per le destinazioni Windows.|  
|[Analizzare i problemi relativi alla memoria .NET Framework](../misc/analyze-dotnet-framework-memory-issues.md)|No|Gli strumenti di Visual Studio non hanno hook nel framework Mono per la profilatura.|  
  
## <a name="release-management"></a>Gestione versioni  
 Collegamento di riferimento: **[Automatizzare le distribuzioni con Release Management](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
|Caratteristica|Supportato con Xamarin|Commenti aggiuntivi|  
|-------------|----------------------------|-------------------------|  
|Gestire i processi di rilascio|Sì||  
|Distribuzione ai server per il caricamento laterale tramite script|Sì||  
|Caricare nell'app store|Parziale|Sono disponibili estensioni che possono automatizzare questo processo per alcuni archivi applicazioni.  Vedere le [estensioni per Visual Studio Team Services](https://marketplace.visualstudio.com/VSTS), ad esempio l'[estensione per Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|  
  
## <a name="monitor-with-hockeyapp"></a>Monitorare con HockeyApp  
 Collegamento di riferimento: **[Monitorare con HockeyApp](https://www.hockeyapp.net/features/)**  
  
|Caratteristica|Supportato con Xamarin|Commenti aggiuntivi|  
|-------------|----------------------------|-------------------------|  
|Analisi degli arresti anomali, telemetria e distribuzione beta|Sì||
