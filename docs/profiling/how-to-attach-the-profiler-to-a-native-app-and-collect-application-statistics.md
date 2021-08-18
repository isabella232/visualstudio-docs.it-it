---
title: Connettere il profiler all'app nativa & raccogliere statistiche dell'app
description: Usare Visual Studio Strumenti di profilatura per connettere il profiler a un'applicazione autonoma nativa in esecuzione e ottenere statistiche sulle prestazioni usando il metodo di campionamento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: df44fe42-281b-4398-b3fc-277b62ae41f1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 78f610802b6a9c3b9134f84c89adc783178985bc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141909"
---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line"></a>Procedura: Allegare il profiler a un'applicazione nativa autonoma e raccogliere statistiche dell'applicazione tramite la riga di comando
Questo articolo descrive come usare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per connettere il profiler a un'applicazione (client) autonoma nativa in esecuzione e raccogliere statistiche sulle prestazioni tramite il metodo di campionamento.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Per ottenere il percorso degli strumenti di profilatura, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso.

 Mentre il profiler è connesso all'applicazione, è possibile sospendere e riprendere la raccolta dei dati. Per terminare una sessione di profilatura, il profiler non deve essere più connesso all'applicazione e deve essere arrestato in modo esplicito.

## <a name="attach-the-profiler"></a>Connettere il profiler
 Per connettere il profiler a un'applicazione di destinazione usare le opzioni **VSPerfCmd/start** e **/attach** per inizializzare il profiler e connetterlo all'applicazione di destinazione. È possibile specificare **/start** e **/attach** e le relative opzioni in un'unica riga di comando. È anche possibile aggiungere l'opzione **/globaloff** per sospendere la raccolta dei dati all'avvio dell'applicazione di destinazione. Usare quindi **/globalon** per avviare la raccolta dei dati.

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Per connettere il profiler a un'applicazione .NET Framework in esecuzione

1. Aprire una finestra del prompt dei comandi.

2. Avvia il profiler. Digitare:

    **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]

   - L'opzione [/start](../profiling/start.md)**:sample** inizializza il profiler.

   - [L'opzione /output](../profiling/output.md)**:** è obbligatoria `OutputFile` con **/start**. `OutputFile` specifica il nome e il percorso del file dei dati di profilatura (con estensione vsp).

     È possibile usare qualsiasi opzione tra le seguenti con l'opzione **/start:sample**.

   | Opzione | Descrizione |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Specifica il dominio e il nome utente dell'account proprietario del processo profilato. Questa opzione è obbligatoria solo se il processo è in esecuzione come utente diverso dall'utente connesso. Il proprietario del processo è elencato nella colonna Nome utente nella scheda Processi di Gestione attività di Windows. |
   | [/crosssession](../profiling/crosssession.md) | Abilita la profilatura dei processi in altre sessioni. Questa opzione è obbligatoria se l'applicazione ASP.NET è in esecuzione in una sessione diversa. L'identificatore di sessione è elencato nella colonna ID sessione nella scheda Processi di Gestione attività di Windows. È possibile specificare **/CS** come abbreviazione per **/crosssession**. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Specifica un contatore delle prestazioni di Windows per cui raccogliere i dati durante la profilatura. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Usare solo con **/wincounter**. Specifica il numero di millisecondi tra gli eventi di raccolta dei dati dei contatori delle prestazioni di Windows. Il valore predefinito è 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Specifica un evento di Event Tracing for Windows (ETW) da raccogliere durante la profilatura. Gli eventi ETW vengono raccolti in un file separato con estensione *etl*. |

3. Connettere il profiler all'applicazione di destinazione. Digitare:

    **VSPerfCmd**[/attach:](../profiling/attach.md) {&#124;} `PID` [ `ProcName` `Sample Event` ]  

    `PID` specifica l'ID del processo dell'applicazione di destinazione. `ProcessName` specifica il nome del processo. Si noti che se si specifica `ProcessName` e sono in esecuzione più processi con lo stesso nome, i risultati sono imprevedibili. È possibile visualizzare gli ID di processo di tutti i processi in esecuzione in Gestione attività di Windows.

    Per impostazione predefinita, i dati relativi alle prestazioni vengono campionati ogni 10.000.000 di cicli di clock del processore non interrotti, ovvero circa 100 volte al secondo in un processore da 1 GHz. È possibile specificare una delle opzioni seguenti per modificare l'intervallo dei cicli di clock o per specificare un evento di campionamento diverso.

   |Evento di esempio|Descrizione|
   |------------------|-----------------|
   |[/timer](../profiling/timer.md) **:**`Interval`|Imposta l'intervallo di campionamento sul numero di cicli di clock non interrotti specificato da `Interval`.|
   |[/pf](../profiling/pf.md)[**:** `Interval` ]|Imposta l'evento di campionamento sugli errori di pagina. Se si specifica `Interval`, imposta il numero di errori di pagina tra campioni. Il valore predefinito è 10.|
   |[/sys](../profiling/sys-vsperfcmd.md) [**:** `Interval` ]|Imposta l'evento di campionamento sulle chiamate di sistema dal processo al kernel del sistema operativo (syscall). Se si specifica `Interval`, imposta il numero di chiamate tra campioni. Il valore predefinito è 10.|
   |[/counter](../profiling/counter.md) **:**`Config`|Modifica l'evento e l'intervallo di campionamento sul contatore delle prestazioni del processore e l'intervallo specificato in `Config`.|

## <a name="control-data-collection"></a>Controllare la raccolta dati
 Mentre l'applicazione di destinazione è in esecuzione, è possibile usare le opzioni di *VSPerfCmd.exe* per avviare e arrestare la scrittura dei dati nel file di dati del profiler. Il controllo della raccolta dei dati consente di raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.

#### <a name="to-start-and-stop-data-collection"></a>Per avviare o interrompere la raccolta dei dati

- Le coppie seguenti di **opzioni VSPerfCmd** avviano e arrestano la raccolta dati. Specificare ogni opzione in una riga di comando separata. È possibile attivare e disattivare la raccolta dei dati più volte.

    |Opzione|Descrizione|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Avvia (**/globalon**) o interrompe (**/globaloff**) la raccolta dei dati per tutti i processi.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Avvia (**/processon**) o interrompe (**/processoff**) la raccolta dati per il processo specificato da `PID`.|
    |[/attach](../profiling/attach.md) **:** `PID` [/detach](../profiling/detach.md)|**/attach** inizia a raccogliere dati per il processo specificato da `PID`. **detach** interrompe la raccolta dei dati per tutti i processi.|

## <a name="end-the-profiling-session"></a>Terminare la sessione di profilatura
 Per terminare una sessione di profilatura, il profiler deve essere disconnesso da tutti i processi profilati e deve essere arrestato in modo esplicito. È possibile disconnettere il profiler da un'applicazione profilata tramite il metodo di campionamento chiudendo l'applicazione o chiamando l'opzione **VSPerfCmd /detach**. È quindi possibile chiamare l'opzione **VSPerfCmd /shutdown** per disattivare il profiler e chiudere il file di dati di profilatura. Il comando **VSPerfClrEnv /off** cancella le variabili di ambiente di profilatura.

#### <a name="to-end-a-profiling-session"></a>Per terminare una sessione di profilatura

1. Eseguire una delle operazioni seguenti per disconnettere il profiler dall'applicazione di destinazione.

    - Digitare **VSPerfCmd /detach**

         -oppure-

    - Chiudere l'applicazione di destinazione.

2. Arrestare il profiler. Digitare:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

3. (Facoltativo) Cancellare le variabili di ambiente di profilatura. Digitare:

     **VSPerfClrEnv /off**

## <a name="see-also"></a>Vedi anche
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Visualizzazioni dei dati del metodo di campionamento](../profiling/profiler-sampling-method-data-views.md)
