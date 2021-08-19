---
title: Collegare il profiler a un servizio .NET per raccogliere statistiche sull'app
description: Usare Visual Studio Strumenti di profilatura da riga di comando per connettere il profiler a un servizio .NET Framework e ottenere statistiche sulle prestazioni usando il metodo di campionamento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a0046c47-26c8-4bec-96a0-81da05e5104a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 63f17e8d9b16379d689daa4866d09f0942a120be
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076659"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-application-statistics-by-using-the-command-line"></a>Procedura: Connettere il profiler a un servizio .NET per raccogliere statistiche dell'applicazione tramite la riga di comando
Questo articolo descrive come usare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per connettere il profiler a un servizio .NET Framework e raccogliere statistiche sulle prestazioni tramite il metodo di campionamento.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Per ottenere il percorso degli strumenti di profilatura, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso.
>
> L'aggiunta di dati di interazione tra livelli a un'esecuzione di profilatura richiede procedure specifiche con gli strumenti di profilatura da riga di comando. Vedere [Raccolta di dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md).

 Per raccogliere dati sulle prestazioni da un servizio .NET Framework, è necessario usare lo strumento [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) per inizializzare le variabili di ambiente appropriate. È quindi necessario riavviare il computer che ospita il servizio e configurare il computer per la profilatura. Connettere quindi il profiler al processo del servizio. Quando il profiler è connesso al servizio, è possibile sospendere e riprendere la raccolta dei dati.

 Per terminare una sessione di profilatura, è necessario disconnettere il profiler dal servizio e arrestarlo in modo esplicito. Nella maggior parte dei casi è consigliabile cancellare le variabili di ambiente di profilatura alla fine di una sessione.

## <a name="attach-the-profiler"></a>Connettere il profiler

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Per connettere il profiler a un servizio .NET Framework

1. Installare il servizio.

2. Aprire una finestra del prompt dei comandi.

3. Inizializzare le variabili di ambiente di profilatura. Digitare:

    **VSPerfClrEnv /globalsampleon** [**/samplelineoff**]

   - **/globalsampleon** abilita il campionamento.

   - **/samplelineoff** disabilita l'assegnazione dei dati raccolti a righe specifiche del codice sorgente. Quando viene specificata questa opzione, i dati vengono assegnati solo alle funzioni.

4. Riavviare il computer.

5. Aprire una finestra del prompt dei comandi.

6. Avvia il profiler. Digitare:

    **VSPerfCmd**  [/start](../profiling/start.md) **:sample**  [/output](../profiling/output.md) **:** [ `OutputFile` `Options` ]

   - **L'opzione /start:sample** inizializza il profiler.

   - **L'opzione /output:** `OutputFile` è obbligatoria con **/start**. `OutputFile` specifica il nome e il percorso del file dei dati di profilatura (con estensione vsp).

     È possibile usare qualsiasi opzione tra le seguenti con l'opzione **/start:sample**.

   > [!NOTE]
   > Le opzioni **/user** e **/crosssession** sono in genere obbligatorie per i servizi.

   | Opzione | Descrizione |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Specifica il dominio e il nome utente dell'account proprietario del processo profilato. Questa opzione è obbligatoria solo se il processo è in esecuzione come utente diverso dall'utente connesso. Il proprietario del processo è elencato nella colonna Nome utente nella scheda Processi di Gestione attività di Windows. |
   | [/crosssession](../profiling/crosssession.md) | Abilita la profilatura dei processi in altre sessioni. Questa opzione è obbligatoria se il servizio è in esecuzione in una sessione diversa. L'ID di sessione è elencato nella colonna ID sessione nella scheda Processi di Gestione attività di Windows. È possibile specificare **/CS** come abbreviazione per **/crosssession**. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Specifica un contatore delle prestazioni di Windows per cui raccogliere i dati durante la profilatura. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Usare solo con **/wincounter**. Specifica il numero di millisecondi tra gli eventi di raccolta dei dati dei contatori delle prestazioni di Windows. Il valore predefinito è 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Specifica un evento di Event Tracing for Windows (ETW) da raccogliere durante la profilatura. Gli eventi ETW vengono raccolti in un file separato con estensione etl. |

7. Se necessario, avviare il servizio.

8. Connettere il profiler al servizio. Digitare:

    **VSPerfCmd**[/attach:](../profiling/attach.md)  {&#124;} [ ] `PID` [ `ProcName` `Sample Event` [/targetclr](../profiling/targetclr.md)**:** `Version` ]  

   - Specificare l'ID processo (`PID`) o il nome del processo (ProcName) del servizio. È possibile visualizzare gli ID processo e i nomi di tutti i processi in esecuzione in Gestione attività di Windows.

     Per impostazione predefinita, i dati relativi alle prestazioni vengono campionati ogni 10.000.000 di cicli di clock del processore non interrotti, ovvero circa 100 campioni al secondo in un processore da 1 GHz. È possibile specificare una delle opzioni seguenti per modificare l'intervallo dei cicli di clock o per specificare un evento di campionamento diverso.

   |Evento di campionamento|Descrizione|
   |------------------|-----------------|
   |[/timer](../profiling/timer.md) **:**`Interval`|Imposta l'intervallo di campionamento sul numero di cicli di clock non interrotti specificato da `Interval`.|
   |[/pf](../profiling/pf.md)[**:** `Interval` ]|Imposta l'evento di campionamento sugli errori di pagina. Se si specifica `Interval`, imposta il numero di errori di pagina tra campioni. Il valore predefinito è 10.|
   |[/sys](../profiling/sys-vsperfcmd.md)[ `:``Interval` ]|Imposta l'evento di campionamento sulle chiamate di sistema dal processo al kernel del sistema operativo (syscall). Se si specifica `Interval`, imposta il numero di chiamate tra campioni. Il valore predefinito è 10.|
   |[/counter](../profiling/counter.md) **:**`Config`|Imposta l'evento e l'intervallo di campionamento sul contatore delle prestazioni del processore e sull'intervallo specificati in `Config`.|

   - **targetclr:** `Version` specifica la versione di Common Language Runtime (CLR) da profilare quando più di una versione del runtime è caricata in un'applicazione. facoltativo.

## <a name="control-data-collection"></a>Controllare la raccolta dati
 Mentre il servizio è in esecuzione, è possibile usare le opzioni di *VSPerfCmd.exe* per avviare e arrestare la scrittura dei dati nel file di dati del profiler. Il controllo della raccolta dei dati consente di raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.

#### <a name="to-start-and-stop-data-collection"></a>Per avviare o interrompere la raccolta dei dati

- Le coppie di opzioni **vsPerfCmd seguenti** avviano e arrestano la raccolta dati. Specificare ogni opzione in una riga di comando separata. È possibile attivare e disattivare la raccolta dei dati più volte.

    |Opzione|Descrizione|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Avvia (**/globalon**) o interrompe (**/globaloff**) la raccolta dei dati per tutti i processi.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Avvia (**/processon**) o interrompe (**/processoff**) la raccolta dei dati per il processo specificato dall'ID di processo (`PID`).|
    |**/attach:**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[:{ `PID`&#124;`ProcName` }]|**/attach** inizia a raccogliere dati per il processo specificato dall'ID o dal nome di processo. **/detach** arresta la raccolta dei dati per il processo specificato o per tutti i processi se non viene specificato un processo specifico.|

## <a name="end-the-profiling-session"></a>Terminare la sessione di profilatura
 Per terminare una sessione di profilatura, il profiler deve essere disconnesso da tutti i processi profilati e deve essere arrestato in modo esplicito. È possibile disconnettere il profiler da un'applicazione profilata tramite il metodo di campionamento chiudendo l'applicazione o chiamando l'opzione **VSPerfCmd /detach**. È quindi possibile chiamare l'opzione **VSPerfCmd /shutdown** per disattivare il profiler e chiudere il file di dati di profilatura.

 Il comando **VSPerfClrEnv /globaloff** cancella le variabili di ambiente di profilatura, ma la configurazione di sistema non viene reimpostata fino al riavvio del computer.

#### <a name="to-end-a-profiling-session"></a>Per terminare una sessione di profilatura

1. Eseguire una delle operazioni seguenti per disconnettere il profiler dall'applicazione di destinazione:

    - Consente di arrestare il servizio.

         -oppure-

    - Digitare **VSPerfCmd /detach**

2. Arrestare il profiler. Digitare:

     **VSPerfCmd /shutdown**

3. (Facoltativo) Cancellare le variabili di ambiente di profilatura. Digitare:

     **VSPerfClrEnv /globaloff**

4. Riavviare il computer.

## <a name="see-also"></a>Vedi anche
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)
- [Visualizzazioni dei dati del metodo di campionamento](../profiling/profiler-sampling-method-data-views.md)
