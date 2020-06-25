---
title: Eseguire strumenti di profilatura con o senza debugger | Microsoft Docs
ms.date: 5/26/2020
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45632967c39348e8dc78dc3e2fb95227dcd86d7d
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85285905"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>Eseguire gli strumenti di profilatura con o senza il debugger

Visual Studio offre una vasta gamma di strumenti di misurazione delle prestazioni e di profilatura. Alcuni strumenti, come l'utilizzo della CPU e l'utilizzo della memoria, possono essere eseguiti con o senza il debugger e nelle configurazioni della build di rilascio o di debug. Gli strumenti del profiler delle prestazioni come Sequenza temporale applicazione possono essere eseguiti in build di debug o di rilascio. Gli strumenti integrati nel debugger, come la finestra Strumenti di diagnostica e la scheda eventi, vengono eseguiti solo durante le sessioni di debug.

>[!NOTE]
>È possibile usare gli strumenti per le prestazioni non inclusi nel debugger con Windows 7 e versioni successive. Per eseguire gli strumenti di profilatura integrati nel debugger è necessario Windows 8 o versione successiva.

Il Profiler prestazioni non incluso nel debugger e gli Strumenti di diagnostica integrati nel debugger offrono informazioni ed esperienze di uso diverse. Gli strumenti integrati nel debugger indicano i punti di interruzione e i valori delle variabili. Gli strumenti non inclusi nel debugger ottengono risultati più vicini all'esperienza dell'utente finale.

Per decidere quali strumenti e risultati utilizzare, tenere presente quanto segue:

- I problemi di prestazioni esterni, come ad esempio i problemi di I/O dei file o di velocità di risposta della rete non sono visualizzati in modo molto diverso negli strumenti integrati nel debugger o negli altri.
- Per i problemi causati da chiamate con utilizzo intensivo della CPU, è possibile che si verifichino notevoli differenze di prestazioni tra le build di rilascio e debug. Verificare se il problema è presente nelle build di rilascio.
- Se il problema si verifica solo durante le compilazioni di debug, probabilmente non è necessario eseguire gli strumenti non del debugger. Per i problemi di compilazione della versione, decidere se gli strumenti del debugger aiuteranno a eseguire ulteriori indagini.
- Le compilazioni Release offrono funzionalità di ottimizzazione come ad esempio l'incorporamento di chiamate di funzione e di costanti, l'eliminazione di percorsi di codice non usati e l'archiviazione di variabili in modalità non utilizzabili dal debugger. I valori relativi alle prestazioni negli strumenti integrati nel debugger sono meno precisi perché le compilazioni di debug non hanno queste ottimizzazioni.
- Il debugger stesso modifica i tempi di prestazioni, in quanto esegue le operazioni del debugger necessarie, ad esempio intercettare gli eventi di eccezione e caricamento del modulo.
- I numeri relativi alle prestazioni della compilazione Release negli strumenti Profiler prestazioni sono i più precisi e accurati. I risultati degli strumenti integrati nel debugger sono particolarmente utili per il confronto con altre misurazioni correlate al debug.

## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Raccogliere dati di profilatura durante il debug

Quando si avvia il debug in Visual Studio selezionando **debug**  >  **Avvia debug**o premendo **F5**, per impostazione predefinita viene visualizzata la finestra **strumenti di diagnostica** . Per aprirlo manualmente, selezionare **debug**  >  **Windows**  >  **Mostra strumenti di diagnostica**. Nella finestra **Strumenti di diagnostica** vengono visualizzate informazioni su eventi, memoria dei processi e utilizzo della CPU.

![Screenshot della finestra di Strumenti di diagnostica](../profiling/media/diagnostictoolswindow.png " Finestra Strumenti di diagnostica")

- Usare l'icona **Impostazioni** sulla barra degli strumenti per scegliere se visualizzare **Utilizzo memoria**, **Analisi interfaccia utente** o **Utilizzo CPU**.

- Selezionare **Impostazioni** nell'elenco a discesa **Impostazioni** per aprire le pagine delle **Proprietà strumenti di diagnostica** con più opzioni.

- Se si esegue Visual Studio Enterprise, è possibile abilitare o disabilitare IntelliTrace passando a **strumenti**  >  **Opzioni**  >  **IntelliTrace**.

La sessione di diagnostica termina quando si interrompe il debug.

### <a name="the-events-tab"></a>Scheda Eventi

Durante una sessione di debug, la scheda Eventi della finestra Strumenti di diagnostica elenca gli eventi di diagnostica che si verificano. Il punto di *interruzione*dei prefissi di categoria, il *file*e altri elementi consentono di analizzare rapidamente l'elenco per una categoria o ignorare le categorie a cui non si è interessati.

Utilizzare l'elenco a discesa **filtro** per filtrare gli eventi in e fuori visualizzazione selezionando o deselezionando categorie specifiche di eventi.

![Screenshot del filtro eventi di diagnostica](../profiling/media/diagnosticeventfilter.png "Filtro eventi di diagnostica")

Usare la casella di ricerca per trovare una stringa specifica nell'elenco di eventi. Ecco i risultati di una ricerca del *nome* della stringa corrispondente a quattro eventi:

![Screenshot della ricerca di eventi di diagnostica](../profiling/media/diagnosticseventsearch.png "Ricerca di eventi di diagnostica")

Per altre informazioni, vedere l'articolo relativo a come [eseguire ricerche e applicare filtri nella scheda Eventi della finestra Strumenti di diagnostica](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

## <a name="collect-profiling-data-without-debugging"></a>Raccogliere dati di profilatura senza il debug

Per raccogliere dati sulle prestazioni senza debug, è possibile eseguire gli strumenti Profiler prestazioni.

1. Con un progetto aperto in Visual Studio, impostare la configurazione della soluzione su **Release**, quindi selezionare **debugger Windows locale**   (o **computer locale**) come destinazione della distribuzione.

1. Selezionare **debug**  >  **prestazioni profiler**oppure premere **ALT** + **F2**.

1. Nella pagina di avvio degli strumenti di diagnostica selezionare uno o più strumenti da eseguire. Vengono visualizzati solo gli strumenti applicabili al tipo di progetto, al sistema operativo e al linguaggio di programmazione. Selezionare **Mostra tutti gli strumenti** per vedere anche gli strumenti che sono disabilitati per la sessione di diagnostica.

   ![Screenshot degli strumenti di diagnostica](../profiling/media/diaghubsummarypage.png "DIAG_SelectTool")

1. Per avviare la sessione di diagnostica, fare clic su **Avvia**.

   Mentre la sessione è in esecuzione, alcuni strumenti visualizzano i grafici dei dati in tempo reale nella pagina strumenti di diagnostica, oltre ai controlli per sospendere e riprendere la raccolta dei dati.

    ![Screenshot della raccolta dati nell'hub prestazioni e diagnostica](../profiling/media/diaghubcollectdata.png "Raccolta dati Hub")

1. Per terminare la sessione di diagnostica, scegliere **Arrestare raccolta**.

   I dati analizzati vengono visualizzati nella pagina del **report** .

È possibile salvare i report e aprirli dall'elenco **sessioni aperte di recente** nella pagina di avvio strumenti di diagnostica.

![Screenshot della Strumenti di diagnostica elenco di sessioni aperte di recente](../profiling/media/diaghubopenexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

## <a name="collect-profiling-data-from-the-command-line"></a>Raccogliere i dati di profilatura dalla riga di comando

Per misurare i dati sulle prestazioni dalla riga di comando, è possibile usare VSDiagnostics.exe, incluso in Visual Studio o nel Strumenti remoti. Questa operazione è utile per acquisire le tracce delle prestazioni nei sistemi in cui Visual Studio non è installato o per creare script per la raccolta di tracce delle prestazioni. Quando si usa VSDiagnostics.exe, si inizia una sessione di diagnostica che acquisisce e archivia i dati di profilatura fino a quando lo strumento non viene arrestato. A questo punto, i dati vengono esportati in un file con estensione DIAGSESSION ed è possibile aprire questo file in Visual Studio per analizzare i risultati.

### <a name="launch-an-application"></a>Avviare un'applicazione

1. Aprire un prompt dei comandi e passare alla directory con VSDiagnostics.exe:

   ```
   <Visual Studio Install Folder>\Team Tools\DiagnosticsHub\Collector\
   ```

2. Avviare VSDiagnostics.exe con il comando seguente:

   ```
   VSDiagnostics.exe start <id> /launch:<appToLaunch> /loadConfig:<configFile>
   ```

   È necessario includere gli argomenti seguenti:

   - \<id\>: Identifica la sessione di raccolta. L'ID deve essere un numero compreso tra 1 e 255.
   - \<appToLaunch\>: File eseguibile da avviare e profilare.
   - \<configFile\>: Il file di configurazione per l'agente di raccolta che si vuole avviare.

3. Per arrestare la raccolta e visualizzare i risultati, seguire la procedura descritta nella sezione "arrestare la raccolta" più avanti in questo articolo.

### <a name="attach-to-an-existing-application"></a>Connetti a un'applicazione esistente

1. Aprire un'applicazione, ad esempio Blocco note, quindi aprire **Gestione attività** per ottenere il relativo ID processo (PID). In Gestione attività trovare il PID nella scheda **Dettagli**   .
2. Aprire un prompt dei comandi e passare alla directory con il file eseguibile dell'agente di raccolta. In genere, è qui:

   ```
   <Visual Studio installation folder>\2019\Preview\Team Tools\DiagnosticsHub\Collector\
   ```

3. Avviare il file di VSDiagnostics.exe digitando il comando seguente.

   ```
   VSDiagnostics.exe start <id> /attach:<pid> /loadConfig:<configFile>
   ```

   È necessario includere gli argomenti seguenti:

   - \<id\>: Identifica la sessione di raccolta. L'ID deve essere un numero compreso tra 1 e 255.
   - \<pid\>: PID del processo che si vuole profilare, che in questo caso è il PID trovato nel passaggio 1.
   - \<configFile\>: Il file di configurazione per l'agente di raccolta che si vuole avviare. Per ulteriori informazioni, vedere [file di configurazione per gli agenti](../profiling/profile-apps-from-command-line.md).

4. Per arrestare la raccolta e visualizzare i risultati, attenersi alla procedura descritta nella sezione successiva.

### <a name="stop-collection"></a>Arresta raccolta

1. Arrestare la sessione di raccolta e inviare l'output a un file digitando il comando seguente.

   ```
   VSDiagnostics.exe stop <id> /output:<path to file>
   ```

2. Passare al file di output dal comando precedente e aprirlo in Visual Studio per esaminare le informazioni raccolte.

## <a name="agent-configuration-files"></a> File di configurazione degli agenti

Gli agenti della raccolta sono componenti intercambiabili che raccolgono tipi diversi di dati, a seconda di ciò che si sta tentando di misurare.
Per praticità, è possibile archiviare le informazioni in un file di configurazione dell'agente. Il file di configurazione è un file con estensione JSON che contiene, come minimo, il nome del file con estensione dll e il relativo CLSID COM. Di seguito sono elencati i file di configurazione di esempio che è possibile trovare nella cartella seguente:

```
<Visual Studio installation folder>\Team Tools\DiagnosticsHub\Collector\AgentConfigs\
```

Per scaricare e visualizzare i file di configurazione dell'agente, vedere i collegamenti seguenti:

- https://aka.ms/vs/diaghub/agentconfig/cpubase
- https://aka.ms/vs/diaghub/agentconfig/cpuhigh
- https://aka.ms/vs/diaghub/agentconfig/cpulow
- https://aka.ms/vs/diaghub/agentconfig/database
- https://aka.ms/vs/diaghub/agentconfig/dotnetasyncbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetallocbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetalloclow

Le configurazioni CpuUsage (base/alta/bassa) corrispondono ai dati raccolti per lo strumento di profilatura [utilizzo CPU](../profiling/cpu-usage.md) .
Le configurazioni DotNetObjectAlloc (base/bassa) corrispondono ai dati raccolti per lo [strumento di allocazione oggetti .NET](../profiling/dotnet-alloc-tool.md).

Le configurazioni Base/Basso/Alto fanno riferimento alla frequenza di campionamento. Ad esempio, il valore Basso corrisponde a 100 campioni al secondo e Alto corrisponde a 4.000 campioni al secondo.
Affinché lo strumento VSDiagnostics.exe funzioni con un agente di raccolta, è necessario che sia una DLL sia un CLSID COM per l'agente appropriato. L'agente potrebbe inoltre disporre di opzioni di configurazione aggiuntive. Se si usa un agente senza un file di configurazione, usare il formato nel comando seguente:

```
VSDiagnostics.exe start <id> /attach:<pid> /loadAgent:<agentCLSID>;<agentName>[;<config>]
```
