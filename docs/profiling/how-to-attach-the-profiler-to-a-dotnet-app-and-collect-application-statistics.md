---
title: "Procedura: Connettere il profiler a un'applicazione .NET Framework autonoma e raccogliere statistiche dell'applicazione tramite la riga di comando | Microsoft Docs"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b62fcbc1-791f-474e-890a-a6c332e0c9ea
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c51b981e7863db371d8e50ae13e48afbc7f270fc
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line"></a>Procedura: Connettere il profiler a un'applicazione .NET Framework autonoma e raccogliere statistiche dell'applicazione tramite la riga di comando
Questo argomento descrive come usare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per connettere il profiler a un'applicazione (client) autonoma .NET Framework in esecuzione e raccogliere statistiche sulle prestazioni tramite il metodo di campionamento.  
  
> [!NOTE]
>  Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app UWP richiedono anche nuove tecniche di raccolta. Vedere [Performance Tools on Windows 8 and Windows Server 2012 applications](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) (Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012).  
>   
>  Gli strumenti da riga di comando degli strumenti di profilatura sono disponibili nella sottodirectory \Team Tools\Performance Tools della directory di installazione di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso. Per altre informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  L'aggiunta di dati di interazione tra livelli a un'esecuzione di profilatura richiede procedure specifiche con gli strumenti di profilatura da riga di comando. Vedere [Raccolta di dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
  
 Per raccogliere i dati sulle prestazioni di un'applicazione .NET Framework, le variabili di ambiente appropriate devono essere inizializzate prima dell'avvio dell'applicazione di destinazione. Mentre il profiler è connesso all'applicazione, è possibile sospendere e riprendere la raccolta dei dati.  
  
 Per terminare una sessione di profilatura, il profiler non deve essere più connesso all'applicazione e deve essere arrestato in modo esplicito. Nella maggior parte dei casi è consigliabile cancellare le variabili di ambiente di profilatura alla fine di una sessione di profilatura.  
  
## <a name="attach-the-profiler"></a>Connettere il profiler  
  
#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Per connettere il profiler a un'applicazione .NET Framework in esecuzione  
  
1.  Aprire una finestra del prompt dei comandi.  
  
2.  Inizializzare le variabili di ambiente di profilatura. Tipo:  
  
     **VSPerfClrEnv /sampleon** [**/samplelineoff**]  
  
    -   L'opzione **/samplelineoff** disabilita la raccolta dei dati di numero di riga del codice sorgente.  
  
3.  Avvia il profiler. Tipo:  
  
     **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]  
  
    -   L'opzione [/start](../profiling/start.md)**:sample** inizializza il profiler.  
  
    -   L'opzione [/output](../profiling/output.md)**:**`OutputFile` è obbligatoria con **/start**. `OutputFile` specifica il nome e il percorso del file dei dati di profilatura (con estensione vsp).  
  
     È possibile usare una delle opzioni seguenti con l'opzione **/start:sample**.  
  
    |Opzione|Descrizione|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Specifica il dominio e il nome utente facoltativi dell'account proprietario del processo profilato. Questa opzione è obbligatoria solo se l'applicazione profilata è stata avviata con un account utente diverso da quello connesso.|  
    |[/crosssession](../profiling/crosssession.md)|Abilita la profilatura dei processi in altre sessioni di accesso. È possibile specificare **/CS** come abbreviazione per **/crosssession**. Questa opzione è obbligatoria se l'applicazione è in esecuzione in una sessione diversa.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Specifica un contatore delle prestazioni di Windows per cui raccogliere i dati durante la profilatura.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Usare solo con **/wincounter**. Specifica il numero di millisecondi tra gli eventi di raccolta dei dati dei contatori delle prestazioni di Windows. Il valore predefinito è 500 ms.|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Specifica un evento di Event Tracing for Windows (ETW) da raccogliere durante la profilatura. Gli eventi ETW vengono raccolti in un file separato con estensione etl.|  
  
4.  Se necessario, avviare l'applicazione di destinazione nel modo usuale.  
  
5.  Connettere il profiler all'applicazione di destinazione. Tipo:  
  
     **VSPerfCmd /attach:**{`PID`&#124;`ProcessName`} [`Sample Event`] [**/targetclr:**`Version`]  
  
    -   `PID` specifica l'ID del processo dell'applicazione di destinazione. `ProcessName` specifica il nome del processo. Si noti che se si specifica `ProcessName` e sono in esecuzione più processi con lo stesso nome, i risultati sono imprevedibili. È possibile visualizzare gli ID di processo di tutti i processi in esecuzione in Gestione attività di Windows.  
  
    -   [/targetclr](../profiling/targetclr.md) **:** `Version` specifica la versione di Common Language Runtime (CLR) da profilare quando più di una versione del runtime è caricata in un'applicazione. Facoltativo.  
  
    -   Per impostazione predefinita, i dati relativi alle prestazioni vengono campionati ogni 10.000.000 di cicli di clock del processore non interrotti, ovvero circa una volta ogni 10 secondi su un processore da 1 GHz. È possibile specificare una delle opzioni seguenti per modificare l'intervallo dei cicli di clock o per specificare un evento di campionamento diverso. [/targetclr](../profiling/targetclr.md)**:**`Version` specifica la versione di CLR da profilare quando in un'applicazione sono caricate più versioni del runtime. Facoltativo.  
  
    |||  
    |-|-|  
    |Evento di campionamento|Descrizione|  
    |[/timer](../profiling/timer.md) **:** `Interval`|Imposta l'intervallo di campionamento sul numero di cicli di clock non interrotti specificato da `Interval`.|  
    |[/pf](../profiling/pf.md) [**:**`Interval`]|Imposta l'evento di campionamento sugli errori di pagina. Se si specifica `Interval`, imposta il numero di errori di pagina tra campioni. Il valore predefinito è 10.|  
    |[/sys](../profiling/sys-vsperfcmd.md) [**:**`Interval`]|Imposta l'evento di campionamento sulle chiamate di sistema dal processo al kernel del sistema operativo (syscall). Se si specifica `Interval`, imposta il numero di chiamate tra campioni. Il valore predefinito è 10.|  
    |[/counter](../profiling/counter.md) **:** `Config`|Imposta l'evento e l'intervallo di campionamento sul contatore delle prestazioni del processore e sull'intervallo specificati in `Config`.|  
  
     
  
## <a name="control-data-collection"></a>Controllare la raccolta dati  
 Quando è in esecuzione l'applicazione di destinazione, è possibile controllare la raccolta dei dati avviando e interrompendo la scrittura dei dati nel file di dati del profiler usando le opzioni **VSPerfCmd.exe**. Il controllo della raccolta dei dati consente di raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.  
  
#### <a name="to-start-and-stop-data-collection"></a>Per avviare o interrompere la raccolta dei dati  
  
-   Le seguenti coppie di opzioni consentono di avviare e interrompere la raccolta dei dati. Specificare ogni opzione in una riga di comando separata. È possibile attivare e disattivare la raccolta dei dati più volte.  
  
    |Opzione|Descrizione|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Avvia (**/globalon**) o interrompe (**/globaloff**) la raccolta dei dati per tutti i processi.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Avvia (**/processon**) o interrompe (**/processoff**) la raccolta dei dati per il processo specificato da `PID`.|  
    |[/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/attach** avvia la raccolta dei dati per il processo specificato da `PID` o dal nome del processo (ProcName). **/detach** interrompe la raccolta dei dati per il processo specificato o per tutti i processi se non viene specificato un processo specifico.|  
  
## <a name="end-the-profiling-session"></a>Terminare la sessione di profilatura  
 Per terminare una sessione di profilatura, il profiler deve essere disconnesso da tutti i processi profilati e deve essere arrestato in modo esplicito. È possibile disconnettere il profiler da un'applicazione profilata tramite il metodo di campionamento chiudendo l'applicazione o chiamando l'opzione **VSPerfCmd /detach**. È quindi possibile chiamare l'opzione **VSPerfCmd /shutdown** per disattivare il profiler e chiudere il file di dati di profilatura. Il comando **VSPerfClrEnv /off** cancella le variabili di ambiente di profilatura.  
  
#### <a name="to-end-a-profiling-session"></a>Per terminare una sessione di profilatura  
  
1.  Eseguire una delle operazioni seguenti per disconnettere il profiler dall'applicazione di destinazione:  
  
    -   Digitare **VSPerfCmd /detach**  
  
         oppure  
  
    -   Chiudere l'applicazione di destinazione.  
  
2.  Arrestare il profiler. Tipo:  
  
     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)  
  
3.  (Facoltativo) Cancellare le variabili di ambiente di profilatura. Tipo:  
  
     **VSPerfClrEnv /off**  
  
## <a name="see-also"></a>Vedere anche  
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Visualizzazioni dei dati del metodo di campionamento](../profiling/profiler-sampling-method-data-views.md)