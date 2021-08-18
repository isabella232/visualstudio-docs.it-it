---
title: Connettere il profiler a .NET per raccogliere dati di memoria
description: Informazioni su come usare Visual Studio Strumenti di profilatura strumenti da riga di comando per connettere il profiler a un'app .NET Framework autonoma (client) e ottenere i dati di memoria.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 68854e9b3082ce017e4a8b41d9875a2f5610d278c45974a141095bc2f2e35cd6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121442203"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line"></a>Procedura: Connettere il profiler a un'applicazione .NET Framework autonoma per raccogliere dati di memoria tramite la riga di comando

Questo articolo descrive come usare gli strumenti da riga di comando disponibili negli strumenti di profilatura di Visual Studio per connettere il profiler a un'applicazione (client) NET Framework autonoma in esecuzione e raccogliere dati di memoria.

> [!NOTE]
> Per ottenere il percorso degli strumenti di profilatura, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso.

Per connettersi a un'applicazione .NET Framework e raccogliere dati di memoria, è necessario usare lo strumento [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) per inizializzare le variabili di ambiente appropriate prima dell'avvio dell'applicazione di destinazione. Mentre il profiler è connesso all'applicazione, è possibile usare lo strumento *VSPerfCmd.exe* per sospendere e riprendere la raccolta dei dati.

Per terminare una sessione di profilatura, il profiler deve essere disconnesso da tutti i processi profilati e deve essere arrestato in modo esplicito. Nella maggior parte dei casi è consigliabile cancellare le variabili di ambiente di profilatura alla fine di una sessione.

## <a name="attach-the-profiler"></a>Connettere il profiler

### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Per connettere il profiler a un'applicazione .NET Framework in esecuzione

1. Aprire una finestra del prompt dei comandi.

2. Inizializzare le variabili di ambiente di profilatura. Digitare:

     **VSPerfClrEnv** {**/samplegc** &#124; **/samplegclife**} [**/samplelineoff**]

    - Le opzioni **/samplegc** e **/samplegclife** specificano se raccogliere solo i dati di allocazione della memoria o se raccogliere sia i dati di allocazione della memoria che quelli di durata degli oggetti. È necessario specificare una sola opzione.

        |Opzione|Descrizioni|
        |------------|------------------|
        |**/samplegc**|Raccoglie solo i dati di allocazione della memoria.|
        |**/samplegclife**|Raccoglie sia i dati sull'allocazione di memoria che quelli sulla durata degli oggetti.|

    - L'opzione **/samplelineoff** disabilita la raccolta dei dati di numero di riga del codice sorgente.

3. Avvia il profiler. Digitare:

     **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]

   - L'opzione [/start](../profiling/start.md)**:sample** inizializza il profiler.

   - [L'opzione /output](../profiling/output.md)**:** è obbligatoria `OutputFile` con **/start**. `OutputFile` specifica il nome e il percorso del file dei dati di profilatura (con estensione vsp).

     È possibile usare qualsiasi opzione tra le seguenti con l'opzione **/start:sample**.

     | Opzione | Descrizione |
     | - | - |
     | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Specifica il dominio e il nome utente dell'account proprietario del processo profilato. Questa opzione è obbligatoria solo se il processo è in esecuzione come utente diverso dall'utente connesso. Il proprietario del processo è elencato nella colonna Nome utente nella scheda Processi di Gestione attività di Windows. |
     | [/crosssession &#124; /cs](../profiling/crosssession.md) | Abilita la profilatura dei processi in altre sessioni. Questa opzione è obbligatoria se l'applicazione è in esecuzione in una sessione diversa. L'identificatore di sessione è elencato nella colonna ID sessione nella scheda Processi di Gestione attività di Windows. È possibile specificare **/CS** come abbreviazione per **/crosssession**. |
     | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Specifica un contatore delle prestazioni di Windows per cui raccogliere i dati durante la profilatura. |
     | [/automark](../profiling/automark.md) **:**`Interval` | Usare solo con **/wincounter**. Specifica il numero di millisecondi tra gli eventi di raccolta dei dati dei contatori delle prestazioni di Windows. Il valore predefinito è 500 ms. |

4. Se necessario, avviare l'applicazione di destinazione nel modo usuale.

5. Connettere il profiler all'applicazione di destinazione. Digitare:

     **VSPerfCmd**[/attach:](../profiling/attach.md) {&#124;} `PID` [ `ProcName` [/targetclr](../profiling/targetclr.md)**:** `Version` ]  

    - `PID` specifica l'ID del processo dell'applicazione di destinazione. `ProcessName` specifica il nome del processo. Si noti che se si specifica `ProcessName` e sono in esecuzione più processi con lo stesso nome, i risultati sono imprevedibili. È possibile visualizzare gli ID di processo di tutti i processi in esecuzione in Gestione attività di Windows.

    - **/targetclr:** `Version` specifica la versione di Common Language Runtime (CLR) da profilare quando vengono caricate più versioni del runtime in un'applicazione. facoltativo.

## <a name="control-data-collection"></a>Controllare la raccolta dati

Quando è in esecuzione l'applicazione di destinazione, è possibile controllare la raccolta dei dati avviando e interrompendo la scrittura dei dati nel file usando le opzioni *VSPerfCmd.exe*. Il controllo della raccolta dei dati consente di raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.

### <a name="to-start-and-stop-data-collection"></a>Per avviare o interrompere la raccolta dei dati

- Le seguenti coppie di opzioni consentono di avviare e interrompere la raccolta dei dati. Specificare ogni opzione in una riga di comando separata. È possibile attivare e disattivare la raccolta dei dati più volte.

    |Opzione|Descrizione|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Avvia (**/globalon**) o interrompe (**/globaloff**) la raccolta dei dati per tutti i processi.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Avvia (**/processon**) o interrompe (**/processoff**) la raccolta dei dati per il processo specificato da `PID`.|
    |[/attach:](../profiling/attach.md) { `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/attach** avvia la raccolta dei dati per il processo specificato da `PID` o dal nome del processo (ProcName). **/detach** arresta la raccolta dei dati per il processo specificato o per tutti i processi se non è specificato un processo specifico.|

## <a name="end-the-profiling-session"></a>Terminare la sessione di profilatura

Per terminare una sessione di profilatura, il profiler deve essere disconnesso da tutti i processi profilati e deve essere arrestato in modo esplicito. È possibile disconnettere il profiler da un'applicazione profilata tramite il metodo di campionamento chiudendo l'applicazione o chiamando l'opzione **VSPerfCmd /detach**. È quindi possibile chiamare l'opzione **VSPerfCmd /shutdown** per disattivare il profiler e chiudere il file di dati di profilatura. Il comando **VSPerfClrEnv /off** cancella le variabili di ambiente di profilatura.

### <a name="to-end-a-profiling-session"></a>Per terminare una sessione di profilatura

1. Eseguire una delle operazioni seguenti per disconnettere il profiler dall'applicazione di destinazione:

    - Digitare **VSPerfCmd /detach**

         -oppure-

    - Chiudere l'applicazione di destinazione.

2. Arrestare il profiler. Digitare:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

3. (Facoltativo) Cancellare le variabili di ambiente di profilatura. Digitare:

     **VSPerfCmd /off**

## <a name="see-also"></a>Vedi anche

[Profilare applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md) 
 [Viste dati di memoria .NET](../profiling/dotnet-memory-data-views.md)
