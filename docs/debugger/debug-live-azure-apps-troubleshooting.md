---
title: Risoluzione dei problemi relativi al debug di snapshot | Microsoft Docs
ms.custom: seodec18
ms.date: 11/07/2018
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b7916cbd3a7faa633baf53a18686779dc2b386c
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2019
ms.locfileid: "58857762"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Risoluzione dei problemi e problemi noti per il debug di snapshot in Visual Studio

Se i passaggi descritti in questo articolo non risolvono il problema, contattare snaphelp@microsoft.com.

## <a name="issue-snappoint-does-not-turn-on"></a>Problema: il punto di acquisizione snapshot di ancoraggio non viene attivato

Se viene visualizzata un'icona di avviso ![Icona di avviso punto di acquisizione snapshot](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "Icona di avviso punto di acquisizione snapshot") con il punto di acquisizione snapshot al posto della normale icona di punto di acquisizione snapshot, questo significa che il punto di acquisizione snapshot non è attivato.

![Punto di acquisizione snapshot non attivato](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Punto di acquisizione snapshot non attivato")

Seguire questa procedura:

1. Assicurarsi di avere la stessa versione del codice sorgente che è stata usata per compilare e distribuire l'app. Assicurarsi di caricare i simboli corretti per la distribuzione. A tale scopo, visualizzare la finestra **Moduli** durante il debug di snapshot e verificare che nella colonna File di simboli sia indicato un file con estensione pdb caricato per il modulo di cui si esegue il debug. Snapshot Debugger tenterà automaticamente di scaricare e usare i simboli per la distribuzione.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problema: i simboli non vengono caricati quando si apre uno snapshot

Se viene visualizzata la finestra seguente, i simboli non sono stati caricati.

![Simboli non caricati](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "Simboli non caricati")

Seguire questa procedura:

- Fare clic sul collegamento **Cambia impostazioni simboli** in questa pagina. Nelle impostazioni **Debug > Simboli** aggiungere una directory di cache dei simboli. Riavviare il debug di snapshot dopo aver impostato il percorso dei simboli.

   I simboli, o file con estensione pdb, disponibili nel progetto devono corrispondere alla distribuzione del servizio app. La maggior parte delle distribuzioni (distribuzione tramite Visual Studio, CI/CD con Azure Pipelines o Kudu e così via) pubblica i file di simboli insieme al servizio app. L'impostazione della directory di cache dei simboli consente a Visual Studio di usarli.

   ![Impostazioni simboli](../debugger/media/snapshot-troubleshooting-symbol-settings.png "Impostazioni simboli")

- In alternativa, se l'organizzazione usa un server di simboli o posiziona i simboli in un percorso diverso, usare le impostazioni dei simboli per caricare i simboli corretti per la distribuzione.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Problema: non è possibile visualizzare l'opzione "Collega Snapshot Debugger" in Cloud Explorer

Seguire questa procedura:

- Verificare che il componente Snapshot Debugger sia installato. Aprire il programma di installazione di Visual Studio e selezionare il componente **Snapshot Debugger** nel carico di lavoro di Azure.
::: moniker range="< vs-2019"
- Assicurarsi che l'app sia supportata. Attualmente, sono supportate solo le app ASP.NET (4.6.1+) e ASP.NET Core (2.0 +) distribuite in servizi app di Azure.
::: moniker-end
::: moniker range=">= vs-2019"
- Assicurarsi che l'app sia supportata:
  - Servizi app di Azure - Applicazioni ASP.NET in esecuzione in .NET Framework 4.6.1 o versioni successive.
  - Servizi app di Azure - Applicazioni ASP.NET Core in esecuzione in .NET Core 2.0 o versioni successive in Windows.
  - Macchine virtuali di Azure (e set di scalabilità di macchine virtuali) - Applicazioni ASP.NET in esecuzione in .NET Framework 4.6.1 o versioni successive.
  - Macchine virtuali di Azure (e set di scalabilità di macchine virtuali) - Applicazioni ASP.NET Core in esecuzione in .NET Core 2.0 o versioni successive in Windows.
  - Servizi Azure Kubernetes - Applicazioni ASP.NET Core in esecuzione in .NET Core 2.2 o versioni successive in Debian 9.
  - Servizi Azure Kubernetes - Applicazioni ASP.NET Core in esecuzione in .NET Core 2.2 o versioni successive in Alpine 3.8.
  - Servizi Azure Kubernetes - Applicazioni ASP.NET Core in esecuzione in .NET Core 2.2 o versioni successive in Ubuntu 18.04.
::: moniker-end

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problema: negli strumenti di diagnostica sono visibili solo snapshot soggetti a limitazioni

![Punto di acquisizione snapshot soggetto a limitazioni](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "Punto di acquisizione snapshot soggetto a limitazioni")

Seguire questa procedura:

- Gli snapshot usano poca memoria, ma prevedono un carico per il commit. Se Snapshot Debugger rileva che il server è in condizioni di carico elevato per la memoria, non verranno acquisiti snapshot. È possibile eliminare gli snapshot già acquisiti interrompendo la sessione di Snapshot Debugger e riprovando.

## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>Problema: Il debug di snapshot con più versioni di Visual Studio genera errori

Visual Studio 2019 richiede una versione più recente dell'estensione del sito Snapshot Debugger nel servizio app di Azure.  Questa versione non è compatibile con la versione precedente dell'estensione del sito Snapshot Debugger usata da Visual Studio 2017.  Se si prova a collegare Snapshot Debugger in Visual Studio 2019 a un servizio app di Azure di cui è stato precedentemente eseguito il debug con Snapshot Debugger di Visual Studio 2017, verrà generato l'errore seguente:

![Estensione del sito Snapshot Debugger di VS 2019 non compatibile](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "Estensione del sito Snapshot Debugger di VS 2019 non compatibile")

Viceversa, se si usa Visual Studio 2017 per collegare Snapshot Debugger a un servizio app di Azure di cui è stato precedentemente eseguito il debug da Snapshot Debugger in Visual Studio 2019, si riceverà l'errore seguente:

![Estensione del sito Snapshot Debugger di VS 2017 non compatibile](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "Estensione del sito Snapshot Debugger di VS 2017 non compatibile")

Per risolvere questo problema, eliminare le impostazioni dell'app seguenti nel portale di Azure e collegare nuovamente Snapshot Debugger:

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>Problema: si verificano problemi con il debug di snapshot ed è necessario abilitare ulteriori log

### <a name="enable-agent-logs"></a>Abilitare i log dell'agente

Per abilitare e disabilitare la registrazione dell'agente, aprire Visual Studio e passare a *Strumenti > Opzioni > Snapshot Debugger > Abilita la registrazione dell'agente*. Si noti che se è abilitata anche l'opzione *Elimina i log dell'agente meno recenti all'avvio della sessione*, per ogni collegamento corretto a Visual Studio verranno eliminati i log dell'agente precedenti.

I log dell'agente sono disponibili nelle posizioni seguenti:

- Servizi app:
  - Passare al sito di Kudu del servizio app (ovvero, servizioapp.**scm**.azurewebsites.net) e passare alla console di debug.
  - I log dell'agente vengono archiviati nella directory seguente: D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\
- Macchina virtuale/set di scalabilità di macchine virtuali:
  - Accedere alla macchina virtuale. I log dell'agente sono archiviati nella posizione seguente: C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics\<Versione>\SnapshotDebuggerAgent_*.txt
- Servizio Azure Kubernetes
  - Passare alla directory seguente: /tmp/diag/AgentLogs/*

### <a name="enable-profilerinstrumentation-logs"></a>Abilitare i log di profiler/strumentazione

I log di strumentazione sono disponibili nelle posizioni seguenti:

- Servizi app:
  - La registrazione degli errori viene inviata automaticamente a D:\Home\LogFiles\eventlog.xml, gli eventi sono contrassegnati con <<Provider Name="Instrumentation Engine" //>> o "Production Breakpoints"
- Macchina virtuale/set di scalabilità di macchine virtuali:
  - Accedere alla macchina virtuale e aprire il Visualizzatore eventi.
  - Aprire la visualizzazione seguente: *Registri di Windows > Applicazione*.
  - Selezionare *Filtro registro corrente* e in *Origine eventi* selezionare *Production Breakpoints* o *Instrumentation Engine*.
- Servizio Azure Kubernetes
  - La registrazione del motore di strumentazione è disponibile in /tmp/diag/log.txt (impostare MicrosoftInstrumentationEngine_FileLogPath in DockerFile)
  - La registrazione ProductionBreakpoint è disponibile in /tmp/diag/shLog.txt

## <a name="known-issues"></a>Problemi noti

- Il debug di snapshot con più client di Visual Studio sullo stesso servizio app non è attualmente supportato.
- Le ottimizzazioni IL per Roslyn non sono completamente supportate nei progetti ASP.NET Core. Per alcuni progetti ASP.NET Core, potrebbe non essere possibile vedere alcune variabili o usare alcune variabili nelle istruzioni condizionali.
- Le variabili speciali, ad esempio *$FUNCTION* oppure *$CALLER*, non possono essere valutate in istruzioni condizionali o punti di inserimento istruzione di registrazione per i progetti ASP.NET Core.
- Il debug di snapshot non funziona nei servizi app con [Cache locale](/azure/app-service/app-service-local-cache) attivata.
- Il debug di snapshot di app API non è attualmente supportato.

## <a name="site-extension-upgrade"></a>Aggiornamento dell'estensione del sito

Il debug di snapshot e Application Insights dipendono da un ICorProfiler, che viene caricato nel processo del sito e causa problemi di blocco di file durante l'aggiornamento. È consigliabile seguire questo processo per assicurarsi di evitare tempi di inattività per il sito di produzione.

- Creare uno [slot di distribuzione](/azure/app-service/web-sites-staged-publishing) all'interno del servizio app e distribuire il sito nello slot.
- Scambiare questo slot con quello di produzione da Cloud Explorer in Visual Studio o dal portale di Azure.
- Arrestare il sito dello slot. In questo modo, entro pochi secondi il processo w3wp.exe del sito verrà terminato in tutte le istanze.
- Aggiornare l'estensione dello slot del sito dal sito di Kudu o dal portale di Azure (*pannello del servizio app > Strumenti di sviluppo > Estensioni > Aggiornamento*).
- Avviare il sito dello slot. È consigliabile visitare il sito per eseguire di nuovo il riscaldamento.
- Scambiare questo slot con quello di produzione.

## <a name="see-also"></a>Vedere anche

- [Debug in Visual Studio](../debugger/index.md)
- [Eseguire il debug di app ASP.NET attive con Snapshot Debugger](../debugger/debug-live-azure-applications.md)
- [Eseguire il debug di app ASP.NET attive in macchine virtuali/set di scalabilità di macchine virtuali di Azure con Snapshot Debugger](../debugger/debug-live-azure-virtual-machines.md)
- [Eseguire il debug di servizi Azure Kubernetes ASP.NET attivi con Snapshot Debugger](../debugger/debug-live-azure-kubernetes.md)
- [Domande frequenti sul debug di snapshot](../debugger/debug-live-azure-apps-faq.md)