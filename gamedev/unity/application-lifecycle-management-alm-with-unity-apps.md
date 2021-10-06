---
title: Application Lifecycle Management (ALM) con app Unity | Microsoft Docs
description: Informazioni sulla gestione del ciclo di vita delle applicazioni (ALM) con le app Unity. Esaminare gli strumenti Agile, il modello, il codice, la compilazione, il test e il miglioramento della qualità del codice.
ms.date: 08/21/2018
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: 2dc61e63-9ba2-4c16-b1ad-f46249e576b6
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: f78d942ae625e45af6ff74ec1360715348708983
ms.sourcegitcommit: d63ba1eff845d41ca095efb14b499ea96c4b6eba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/06/2021
ms.locfileid: "129561139"
---
# <a name="devops-with-unity-apps"></a>DevOps con app Unity

Lo sviluppo di app per piattaforme moderne comporta molte più attività rispetto alla semplice scrittura di codice. Queste attività definite DevOps (Development + Operations) si estendono per il ciclo di vita completo di un'app e includono pianificazione e rilevamento del lavoro, progettazione e implementazione di codice, gestione di un repository di codice sorgente, esecuzione di compilazioni, gestione di integrazioni e distribuzioni continue, test (tra cui unit test e test dell'interfaccia utente), esecuzione di varie forme di diagnostica in ambienti di sviluppo e produzione e monitoraggio delle prestazioni delle app e comportamenti dell'utente in tempo reale tramite telemetria e analisi.

Visual Studio insieme a Azure DevOps Services e Team Foundation Server offre un'ampia gamma di funzionalità DevOps. Molte di queste sono applicabili a progetti multipiattaforma, inclusi i giochi e le app grafiche immersive creati con Unity&mdash;soprattutto quando si usa C# come linguaggio di script. Tuttavia, poiché Unity ha un ambiente di sviluppo e un motore di runtime propri, diverse funzionalità DevOps non sono applicabili come avviene per altri tipi di progetti compilati in Visual Studio.

Le tabelle seguenti identificano in che modo le funzionalità DevOps in Visual Studio sono o meno applicabili quando si usa Unity. Per informazioni dettagliate sulle funzionalità fare riferimento alla documentazione collegata.

## <a name="agile-tools"></a>Strumenti Agile:

Collegamento di riferimento: [About Agile tools and Agile project management](/azure/devops/boards/backlogs/backlogs-overview?view=vsts&preserve-view=true) (Informazioni sugli strumenti e la gestione di progetti Agile) (usando Azure Boards o TFS, incluso Team Explorer Everywhere)

Commento generale: tutte le funzionalità di pianificazione e traccia sono indipendenti dal tipo di progetto e dai linguaggi di codifica.

|Funzionalità|Supportata con Unity|Commenti aggiuntivi|
|-------------|--------------------------|-------------------------|
|Gestione di backlog e sprint|Sì||
|Verifica del lavoro|Sì||
|Collaborazione nella chat team|Sì||
|Bacheche Kanban|Sì||
|Segnalare e visualizzare lo stato di avanzamento|Sì||

## <a name="modeling"></a>Modellazione

Collegamento di riferimento: **[Analizzare e modellare l'architettura](/visualstudio/modeling/analyze-and-model-your-architecture)**

Commento generale: anche se le funzionalità di progettazione sono indipendenti dal linguaggio di codifica o funzionano con i linguaggi .NET come C#, operano in base a un paradigma di applicazione tradizionale con gerarchie di oggetti e relazioni tra classi. La progettazione di un gioco in Unity prevede un paradigma completamente diverso, ossia relazioni di oggetti grafici, suoni, shader, script e così via. Per questo motivo, gli strumenti diagramma di modellazione di Visual Studio non sono particolarmente rilevanti per un intero progetto Unity. Possono eventualmente essere usati per gestire le relazioni negli script C#, che però costituiscono solo una parte dell'intero progetto.

|Funzionalità|Supportata con Unity|Commenti aggiuntivi|
|-------------|--------------------------|-------------------------|
|Diagrammi sequenza|No||
|Grafici delle dipendenze|No||
|Gerarchia di chiamata|No||
|Progettazione classi|No||
|Esplora architettura|No||
|Diagrammi UML (caso di utilizzo, attività, classe, componente, sequenza e DSL)|No||
|Diagrammi livello|No||
|Convalida dei livelli|No||

## <a name="code"></a>Codice

|Funzionalità|Supportata con Unity|Commenti aggiuntivi|
|-------------|--------------------------|-------------------------|
|[Usare controllo della versione di Team Foundation (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts&preserve-view=true) o Azure Repos|Sì|I progetti Unity sono semplicemente una raccolta di file che possono essere inseriti nei sistemi di controllo della versione come qualsiasi altro progetto, ma con alcune considerazioni speciali descritte dopo la presente tabella.|
|[Introduzione a Git in Azure Repos](/azure/devops/repos/git/gitquickstart?view=vsts&preserve-view=true&tabs=visual-studio)|Sì|Vedere le note dopo la tabella.|
|[Migliorare la qualità del codice](/visualstudio/test/improve-code-quality)|Sì||
|[Trovare le modifiche apportate al codice e altri elementi della cronologia](/visualstudio/ide/find-code-changes-and-other-history-with-codelens)|Sì||
|[Usare le mappe del codice per eseguire il debug delle applicazioni](/visualstudio/modeling/use-code-maps-to-debug-your-applications)|Sì||

Considerazioni speciali per il controllo della versione con Unity:

1. Unity tiene traccia dei metadati relativi alle risorse del gioco in una singola libreria opaca, nascosta per impostazione predefinita. Per mantenere sincronizzati i file e i metadati, è necessario per rendere visibili i metadati e archiviarli in blocchi più gestibili. Per informazioni dettagliate, vedere [Using External Version Control Systems with Unity](https://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) (Uso di sistemi di controllo della versione esterni con Unity) nella documentazione di Unity.

2. Non tutti i file e tutte le cartelle in un progetto Unity sono appropriati per il controllo del codice sorgente, come descritto anche nel collegamento precedente. È necessario aggiungere le cartelle Assets e ProjectSettings, mentre Library e Temp non devono essere aggiunte. Per un elenco aggiuntivo dei file generati che non vengono sottoposti al controllo del codice sorgente, vedere la discussione [How to use Git for Unity3D source control?](https://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control) (Come usare Git per il controllo del codice sorgente di Unity3D) in StackOverflow. Molti sviluppatori hanno anche discusso di questo argomento in modo indipendente.

3. Le risorse binarie in un progetto Unity, ad esempio trame e file audio, possono richiedere una grande quantità di spazio di archiviazione. Diversi sistemi di controllo del codice sorgente, come Git, memorizzano una copia univoca di un file per ogni modifica apportata, anche se la modifica interessa solo una piccola parte del file. Ciò può causare un aumento eccessivo dell'archivio Git. Per risolvere questo problema, gli sviluppatori Unity scelgono spesso di aggiungere al repository solo le risorse finali e usare un modo diverso per mantenere una cronologia di lavoro delle risorse, ad esempio OneDrive, DropBox o git-annex. Questo approccio funziona perché tali attività in genere non richiedono il controllo della versione insieme alle modifiche del codice sorgente. In genere, gli sviluppatori impostano anche la modalità di serializzazione delle risorse dell'editor di progetto sull'opzione per forzare il testo per archiviare i file delle scene in formato testo anziché binario, in modo da consentire operazioni di unione nel controllo del codice sorgente. Per informazioni dettagliate, vedere [Editor Settings](https://docs.unity3d.com/Manual/class-EditorManager.html) (Impostazioni dell'editor) nella documentazione di Unity.

## <a name="build"></a>Compilazione

Collegamento di riferimento: **[Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true)**

|Funzionalità|Supportata con Unity|Commenti aggiuntivi|
|-------------|--------------------------|-------------------------|
|Team Foundation Server (TFS) locale|Possibile|I progetti Unity vengono compilati tramite l'ambiente Unity e non tramite il sistema di compilazione di Visual Studio (se si usa Visual Studio Tools per Unity, vengono compilati gli script, ma non viene prodotto un eseguibile). Poiché è possibile [compilare progetti Unity dalla riga di comando](https://docs.unity3d.com/Manual/CommandLineArguments.html) (documentazione di Unity), si può configurare un processo MSBuild in un server TFS per eseguire i comandi Unity appropriati, a condizione che Unity sia installato nello stesso computer.<br /><br /> Unity offre anche [Unity Cloud Build](https://build.cloud.unity3d.com/landing/) che monitora un repository Git o SVN ed esegue compilazioni periodiche. Al momento non funziona con TFVC o Azure DevOps Services.|
|Server di compilazione locale collegato a Azure DevOps Services|Possibile|Date le stesse condizioni precedenti, è anche possibile indirizzare le compilazioni attivate tramite Azure DevOps Services in modo che usino un computer TFS locale. Per [istruzioni, vedere Build and Release Agents](/azure/devops/pipelines/agents/agents?view=vsts&preserve-view=true) (Agenti di compilazione e versione).|
|Servizio controller ospitato di Azure DevOps Services|No|Le compilazioni Unity non sono attualmente supportate.|
|Definizioni di compilazione con pre e post script|Sì|Per gli script pre- e post-compilazione è anche possibile configurare una definizione di compilazione personalizzata che usa la riga di comando di Unity per eseguire una compilazione.|
|Integrazione continuata incluse le archiviazioni gestite|Sì|Archiviazioni gestite per TFVC solo quando Git elabora un modello di richiesta di pull anziché le archiviazioni.|

## <a name="test"></a>Test

|Funzionalità|Supportata con Unity|Commenti aggiuntivi|
|-------------|--------------------------|-------------------------|
|Pianificazione dei test, creazione di test case e organizzazione di gruppi di test|Sì||
|Test manuali|Sì||
|Test Manager (registrazione e riproduzione di test)|Solo dispositivi Windows ed emulatori Android||
|Code coverage|n/d|Non applicabile perché l'esecuzione di unit test avviene in Unity e non in Visual Studio. Vedere di seguito.|
|[Eseguire unit test del codice](/visualstudio/test/unit-test-your-code)|In Unity, ma non Visual Studio.|Unity offre un proprio framework unit test come parte degli strumenti [di test di Unity](https://assetstore.unity.com/packages/tools/utilities/unity-test-tools-13802) (Unity Asset Store). I risultati degli unit test vengono segnalati in Unity e non saranno rilevati in Visual Studio.|
|[Usare l'automazione dell'interfaccia utente per testare il codice](/visualstudio/test/use-ui-automation-to-test-your-code)|No|I test codificati dell'interfaccia utente si basano su controlli leggibili nell'interfaccia utente dell'app. Le app Unity sono di natura grafica e il contenuto non può quindi essere letto dagli strumenti di test codificato dell'interfaccia utente.|

## <a name="improve-code-quality"></a>Migliorare la qualità del codice

Collegamento di riferimento: **[Migliorare la qualità del codice](/visualstudio/test/improve-code-quality)**

|Funzionalità|Supportata con Unity|Commenti aggiuntivi|
|-------------|--------------------------|-------------------------|
|[Analizzare la qualità del codice gestito](/visualstudio/code-quality/code-analysis-for-managed-code-overview)|Sì|È possibile analizzare il codice di script C# in Visual Studio.|
|[Ricerca del codice duplicato mediante il rilevamento del clone di codice](https://msdn.microsoft.com/library/hh205279.aspx)|Sì|È possibile analizzare il codice di script C# in Visual Studio.|
|[Misurazione della complessità e della manutenibilità del codice gestito](/visualstudio/code-quality/code-metrics-values)|Sì|È possibile analizzare il codice di script C# in Visual Studio.|
|[Strumenti per le prestazioni](/visualstudio/profiling/performance-explorer)|No|Usare il [profiler di Unity](https://docs.unity3d.com/Manual/Profiler.html) (sito Web di Unity).|
|Analizzare i problemi relativi alla memoria .NET Framework|No|Gli Strumenti di Visual Studio non includono per il framework Mono, usato da Unity, per la profilatura. Usare il [profiler di Unity](http://docs.unity3d.com/Manual/Profiler.html) (documentazione di Unity).|

## <a name="release-management"></a>Gestione versioni

Collegamento di riferimento: [Build and Release in Azure Pipelines and TFS](/azure/devops/pipelines/overview?view=vsts&preserve-view=true) (Compilazione e rilascio in Azure Pipelines e TFS)

|Funzionalità|Supportata con Unity|Commenti aggiuntivi|
|-------------|--------------------------|-------------------------|
|Gestire i processi di rilascio|Sì||
|Distribuzione ai server per il caricamento laterale tramite script|Sì||
|Caricare nell'app store|Partial|Sono disponibili estensioni che possono automatizzare questo processo per alcuni archivi applicazioni. Vedere le [estensioni per Azure DevOps Services](https://marketplace.visualstudio.com/VSTS), ad esempio l'[estensione per Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|

## <a name="monitor-with-hockeyapp"></a>Monitorare con HockeyApp

Collegamento di riferimento: **[Monitorare con HockeyApp](https://www.hockeyapp.net/features/)**

|Funzionalità|Supportata con Unity|Commenti aggiuntivi|
|-------------|--------------------------|-------------------------|
|Analisi degli arresti anomali, telemetria e distribuzione beta|Sì|HockeyApp risulta particolarmente utile per gestire la distribuzione beta e ottenere report sugli arresti anomali.<br /><br /> Per la telemetria di script C#, è possibile usare qualsiasi framework di analisi, a condizione che venga eseguito nella versione di .NET usata da Unity. Tuttavia, consente l'analisi solo all'interno degli script di gioco e non più in profondità nel motore di Unity. Attualmente non è disponibile un plug-in per Application Insights, ma sono disponibili plug-in per altre soluzioni di analisi, ad esempio [Unity Analytics](https://assetstore.unity.com/packages/add-ons/services/analytics/unity-analytics-28120) e [Google Analytics](https://github.com/googleanalytics/google-analytics-plugin-for-unity). I servizi come Unity Analytics che riconoscono la natura di un progetto Unity forniscono naturalmente analisi più significative rispetto ai framework generici.|
