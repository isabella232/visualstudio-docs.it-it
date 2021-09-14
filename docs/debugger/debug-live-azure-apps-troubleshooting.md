---
title: Risoluzione dei problemi relativi al debug di snapshot | Microsoft Docs
description: Informazioni sulla risoluzione dei problemi e sui problemi noti per il debug di snapshot in Visual Studio. Caricare ICorProfiler senza causare tempi di inattività nel sito di produzione.
ms.custom: SEO-VS-2020
ms.date: 04/24/2019
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f06bb143bfb10940d107dccc038dc852b54efb2e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626562"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Risoluzione dei problemi e problemi noti per il debug di snapshot in Visual Studio

Se i passaggi descritti in questo articolo non risolvono il problema, cercare il problema in [Developer Community](https://aka.ms/feedback/suggest?space=8) o segnalare un nuovo problema scegliendo Help  >  **Send Feedback** Report a Problem (Invia commenti e suggerimenti) per segnalare un  >   problema in Visual Studio.

## <a name="issue-attach-snapshot-debugger-encounters-an-http-status-code-error"></a>Problema: "Collega Snapshot Debugger" rileva un errore del codice di stato HTTP

Se viene visualizzato l'errore seguente nella finestra **Output** durante il tentativo di connessione, potrebbe trattarsi di un problema noto elencato di seguito. Provare le soluzioni proposte e, se il problema persiste, contattare l'alias precedente.

`[TIMESTAMP] Error --- Unable to Start Snapshot Debugger - Attach Snapshot Debugger failed: System.Net.WebException: The remote server returned an error: (###) XXXXXX`

### <a name="401-unauthorized"></a>(401) Non autorizzato

Questo errore indica che la chiamata REST emessa da Visual Studio azure usa credenziali non valide. 

Seguire questa procedura:

* Assicurarsi che l'Visual Studio account di personalizzazione abbia le autorizzazioni per la sottoscrizione di Azure e la risorsa a cui ci si connette. Un modo rapido per determinare questo problema è controllare se la risorsa è disponibile nella finestra di dialogo da Debug  >  **attach Snapshot Debugger...**  >  **Risorsa di Azure**  >  **Selezionare Esistente** o in Cloud Explorer.
* Se l'errore persiste, usare uno dei canali di feedback descritti all'inizio di questo articolo.

Se è stata abilitata l'autenticazione/autorizzazione (EasyAuth) nel servizio app, è possibile che si verifichi un errore 401 con LaunchAgentAsync nel messaggio di errore dello stack di chiamate. Assicurarsi  che Azione da eseguire quando la richiesta non è autenticata sia impostata su Consenti richieste anonime **(nessuna azione)** nel portale di Azure e fornire un file authorization.json in D:\Home\sites\wwwroot con il contenuto seguente. 

```
{
  "routes": [
    {
      "path_prefix": "/",
      "policies": {
        "unauthenticated_action": "RedirectToLoginPage"
      }
    },
    {
      "http_methods": [ "POST" ],
      "path_prefix": "/41C07CED-2E08-4609-9D9F-882468261608/api/agent",
      "policies": {
        "unauthenticated_action": "AllowAnonymous"
      }
    }
  ]
}
```

La prima route protegge in modo efficace il dominio dell'app **in modo simile a Log in with [IdentityProvider] (Accedi con [IdentityProvider]).** La seconda route espone l'endpoint SnapshotDebugger AgentLaunch all'esterno dell'autenticazione, che esegue  l'azione predefinita di avvio dell'agente di diagnostica SnapshotDebugger solo se l'estensione del sito preinstallata SnapshotDebugger è abilitata per il servizio app. Per altri dettagli sulla configurazione di authorization.json, vedere Regole [di autorizzazione url.](https://azure.github.io/AppService/2016/11/17/URL-Authorization-Rules.html)

### <a name="403-forbidden"></a>(403) Non consentito

Questo errore indica che l'autorizzazione è stata negata. Ciò può essere causato da molti problemi diversi.

Seguire questa procedura:

* Verificare che l'account Visual Studio abbia una sottoscrizione di Azure valida con le autorizzazioni Role-Based controllo degli accessi in base al ruolo necessarie per la risorsa. Per AppService, verificare di avere le autorizzazioni per eseguire [query](/rest/api/appservice/appserviceplans/get) sul piano di servizio app che ospita l'app.
* Verificare che il timestamp del computer client sia corretto e aggiornato. I server con timestamp disattivati di più di 15 minuti dal timestamp della richiesta generano in genere questo errore.
* Se l'errore persiste, usare uno dei canali di feedback descritti all'inizio di questo articolo.

### <a name="404-not-found"></a>(404) Non trovato

Questo errore indica che non è stato possibile trovare il sito Web nel server.

Seguire questa procedura:

* Verificare di avere un sito Web distribuito e in esecuzione nella risorsa del servizio app a cui ci si connette.
* Verificare che il sito sia disponibile in https:// \<resource\> .azurewebsites.net
* Verificare che l'applicazione Web personalizzata in esecuzione correttamente non restituirà il codice di stato 404 quando si accede https:// \<resource\> .azurewebsites.net
* Se l'errore persiste, usare uno dei canali di feedback descritti all'inizio di questo articolo.

### <a name="406-not-acceptable"></a>(406) Non accettabile

Questo errore indica che il server non è in grado di rispondere al tipo impostato nell'intestazione Accept della richiesta.

Seguire questa procedura:

* Verificare che il sito sia disponibile all'indirizzo https:// \<resource\> .azurewebsites.net
* Verificare che non sia stata eseguita la migrazione del sito alle nuove istanze. Snapshot Debugger usa la nozione di ARRAffinity per il routing delle richieste a istanze specifiche che possono generare questo errore in modo intermittente.
* Se l'errore persiste, usare uno dei canali di feedback descritti all'inizio di questo articolo.

### <a name="409-conflict"></a>(409) Conflitto

Questo errore indica che la richiesta è in conflitto con lo stato corrente del server.

Si tratta di un problema noto che si verifica quando un utente tenta di Snapshot Debugger a un servizio app che ha abilitato ApplicationInsights. ApplicationInsights imposta AppSettings con una distinzione tra maiuscole e minuscole diversa rispetto Visual Studio, causando questo problema.

::: moniker range=">= vs-2019"
Questo problema è stato risolto in Visual Studio 2019.
::: moniker-end

Seguire questa procedura:

::: moniker range="vs-2017"

* Verificare nel portale di Azure che AppSettings per SnapshotDebugger (SNAPSHOTDEBUGGER_EXTENSION_VERSION) e InstrumentationEngine (INSTRUMENTATIONENGINE_EXTENSION_VERSION) siano maiuscoli. In caso contrario, aggiornare manualmente le impostazioni, forzando il riavvio del sito.
::: moniker-end
* Se l'errore persiste, usare uno dei canali di feedback descritti all'inizio di questo articolo.

### <a name="500-internal-server-error"></a>(500) Errore interno del server

Questo errore indica che il sito è completamente insoddibile o che il server non è in grado di gestire la richiesta. Snapshot Debugger funzioni solo nelle applicazioni in esecuzione. [Application Insights Snapshot Debugger](/azure/azure-monitor/app/snapshot-debugger) offre snapshot sulle eccezioni e può essere lo strumento migliore per le proprie esigenze.

### <a name="502-bad-gateway"></a>(502) Gateway non valido

Questo errore indica un problema di rete lato server e può essere temporaneo.

Seguire questa procedura:

* Provare ad attendere alcuni minuti prima di collegare Snapshot Debugger nuovo.
* Se l'errore persiste, usare uno dei canali di feedback descritti all'inizio di questo articolo.

## <a name="issue-snappoint-does-not-turn-on"></a>Problema: il punto di acquisizione snapshot di ancoraggio non viene attivato

Se viene visualizzata un'icona di avviso ![Icona](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "Icona di avviso del punto di agganciamento") di avviso Punto di agganciamento con il punto di agganciamento anziché la normale icona del punto di agganciamento, il punto di agganciamento non è attivato.

![Il punto di agganciato non si attiva](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Il punto di agganciato non si attiva")

Seguire questa procedura:

1. Assicurarsi di avere la stessa versione del codice sorgente usata per compilare e distribuire l'app. Assicurarsi di caricare i simboli corretti per la distribuzione. A tale scopo, visualizzare la finestra **Moduli** durante il debug di snapshot e verificare che nella colonna File di simboli sia indicato un file con estensione pdb caricato per il modulo di cui si esegue il debug. Snapshot Debugger tenterà automaticamente di scaricare e usare i simboli per la distribuzione.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problema: i simboli non vengono caricati quando si apre uno snapshot

Se viene visualizzata la finestra seguente, i simboli non sono stati caricati.

![I simboli non vengono caricati](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "I simboli non vengono caricati")

Seguire questa procedura:

- Fare clic sul collegamento **Cambia impostazioni simboli** in questa pagina. Nelle impostazioni **Debug > Simboli** aggiungere una directory di cache dei simboli. Riavviare il debug di snapshot dopo aver impostato il percorso dei simboli.

   I simboli, o file con estensione pdb, disponibili nel progetto devono corrispondere alla distribuzione del servizio app. La maggior parte delle distribuzioni (distribuzione tramite Visual Studio, CI/CD con Azure Pipelines o Kudu e così via) pubblica i file di simboli insieme al servizio app. L'impostazione della directory di cache dei simboli consente a Visual Studio di usarli.

   ![Impostazioni dei simboli](../debugger/media/snapshot-troubleshooting-symbol-settings.png "Impostazioni dei simboli")

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

![Punto di snap limitato](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "Punto di snap limitato")

Seguire questa procedura:

- Gli snapshot usano poca memoria, ma prevedono un carico per il commit. Se Snapshot Debugger rileva che il server è in condizioni di carico elevato per la memoria, non verranno acquisiti snapshot. È possibile eliminare gli snapshot già acquisiti interrompendo la sessione di Snapshot Debugger e riprovando.

::: moniker range=">= vs-2019"
## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>Problema: Il debug di snapshot con più versioni di Visual Studio genera errori

Visual Studio 2019 richiede una versione più recente dell'Snapshot Debugger del sito nel Servizio app di Azure.  Questa versione non è compatibile con la versione precedente dell'Snapshot Debugger del sito usata da Visual Studio 2017.  Se si tenta di collegare il Snapshot Debugger in Visual Studio 2019 a un Servizio app di Azure di cui è stato precedentemente fatto il debug da Snapshot Debugger in Visual Studio 2017, verrà visualizzato l'errore seguente:

![Estensione del Snapshot Debugger incompatibile Visual Studio 2019](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "Estensione del sito Snapshot Debugger incompatibile Visual Studio 2019")

Viceversa, se si usa Visual Studio 2017 per collegare il Snapshot Debugger a un Servizio app di Azure di cui è stato precedentemente fatto il debug da Snapshot Debugger in Visual Studio 2019, verrà visualizzato l'errore seguente:

![Estensione del sito Snapshot Debugger incompatibile Visual Studio 2017](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "Estensione del sito Snapshot Debugger incompatibile Visual Studio 2017")

Per risolvere questo problema, eliminare le impostazioni dell'app seguenti nel portale di Azure e collegare nuovamente Snapshot Debugger:

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION
::: moniker-end

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>Problema: si verificano problemi con il debug di snapshot ed è necessario abilitare ulteriori log

### <a name="enable-agent-logs"></a>Abilitare i log dell'agente

Per abilitare e disabilitare la registrazione dell'agente, aprire Visual Studio e passare a *Strumenti > Opzioni > Snapshot Debugger > Abilita la registrazione dell'agente*. Si noti che se è abilitata anche l'opzione *Elimina i log dell'agente meno recenti all'avvio della sessione*, per ogni collegamento corretto a Visual Studio verranno eliminati i log dell'agente precedenti.

I log dell'agente sono disponibili nelle posizioni seguenti:

- Servizi app:
  - Passare al sito di Kudu del servizio app (ovvero, servizioapp.**scm**.azurewebsites.net) e passare alla console di debug.
  - I log dell'agente vengono archiviati nella directory seguente: D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\
- Macchina virtuale/set di scalabilità di macchine virtuali:
  - Accedere alla macchina virtuale, i log dell'agente vengono archiviati come segue: C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics \<Version> \SnapshotDebuggerAgent_*.txt
- Servizio Azure Kubernetes
  - Passare alla directory seguente: /tmp/diag/AgentLogs/*

### <a name="enable-profilerinstrumentation-logs"></a>Abilitare i log di profiler/strumentazione

I log di strumentazione sono disponibili nelle posizioni seguenti:

- Servizi app:
  - La registrazione degli errori viene inviata automaticamente D:\Home\LogFiles\eventlog.xml, gli eventi sono contrassegnati con `<Provider Name="Instrumentation Engine" />` o "Production Breakpoints"
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

## <a name="see-also"></a>Vedi anche

- [Debug in Visual Studio](../debugger/index.yml)
- [Eseguire il debug di app ASP.NET attive con Snapshot Debugger](../debugger/debug-live-azure-applications.md)
- [Eseguire il debug di app ASP.NET attive in macchine virtuali/set di scalabilità di macchine virtuali di Azure con Snapshot Debugger](../debugger/debug-live-azure-virtual-machines.md)
- [Eseguire il debug di servizi Azure Kubernetes ASP.NET attivi con Snapshot Debugger](../debugger/debug-live-azure-kubernetes.md)
- [Domande frequenti sul debug di snapshot](../debugger/debug-live-azure-apps-faq.yml)
