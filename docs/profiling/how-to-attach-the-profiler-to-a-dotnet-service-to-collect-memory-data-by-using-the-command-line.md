---
title: Connettere il profiler al servizio .NET per raccogliere dati di memoria
description: Usare Visual Studio Strumenti di profilatura da riga di comando per connettere il profiler a un servizio .NET Framework e raccogliere dati di memoria.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: aeac39af-ad99-479f-aa36-4104356ca512
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 859c71d1bee179f59ab19ddf1b1e038809db7d43
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122131482"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-service-to-collect-memory-data-by-using-the-command-line"></a>Procedura: Connettere il profiler a un servizio .NET Framework per raccogliere dati di memoria tramite la riga di comando
Questo articolo descrive come usare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per connettere il profiler a un servizio .NET Framework e raccogliere dati di memoria. È possibile raccogliere dati relativi al numero e alla dimensione delle allocazioni di memoria ed è anche possibile raccogliere dati sulla durata degli oggetti di memoria.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> [!NOTE]
> Per ottenere il percorso degli strumenti di profilatura, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso.

 Per raccogliere dati di memoria da un servizio .NET Framework, usare lo strumento [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) per inizializzare le variabili di ambiente appropriate nel computer che ospita il servizio. Per configurare il computer per la profilatura è necessario riavviarlo.

 Usare quindi lo strumento [VSPerfCmd](../profiling/vsperfcmd.md) per connettere il profiler al processo del servizio. Quando il profiler è connesso al servizio, è possibile sospendere e riprendere la raccolta dei dati.

 Per terminare una sessione di profilatura, è necessario disconnettere il profiler dal servizio e arrestarlo in modo esplicito. Nella maggior parte dei casi è consigliabile cancellare le variabili di ambiente di profilatura alla fine di una sessione.

## <a name="attach-the-profiler"></a>Connettere il profiler

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Per connettere il profiler a un servizio .NET Framework

1. Se necessario, installare il servizio.

2. Aprire una finestra del prompt dei comandi.

3. Inizializzare le variabili di ambiente di profilatura. Digitare:

    **VSPerfClrEnv** {**/globalsamplegc /globalsamplegclife**}[**/samplelineoff**]

   - Le opzioni **/globalsamplegclife** e **/globalsamplegclife** specificano il tipo di dati di memoria da raccogliere. Specificare una sola delle opzioni seguenti.

     **/globalsamplegc** abilita la raccolta dei dati di allocazione della memoria.

     **/globalsamplegclife** abilita la raccolta dei dati di allocazione della memoria e dei dati di durata degli oggetti.

   - L'opzione **/samplelineoff** disabilita la raccolta dei dati di numero di riga del codice sorgente.

4. Riavviare il computer per impostare la nuova configurazione di ambiente.

5. Se necessario, avviare il servizio.

6. Aprire una finestra del prompt dei comandi. Se necessario, aggiungere il percorso del profiler alla variabile di ambiente PATH.

7. Avvia il profiler. Digitare:

    **VSPerfCmd**  [/start](../profiling/start.md) **:sample**  [/output](../profiling/output.md) **:** [ `OutputFile` `Options` ]

   - **L'opzione /start:sample** inizializza il profiler.

   - **L'opzione /output:** `OutputFile` è obbligatoria con **/start**. `OutputFile` specifica il nome e il percorso del file dei dati di profilatura (con estensione vsp).

     È possibile usare una o più delle opzioni seguenti con l'opzione **/start:sample**.

   > [!NOTE]
   > Le opzioni **/user** e **/crosssession** sono in genere obbligatorie per i servizi.

   | Opzione | Descrizione |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Specifica il dominio e il nome utente dell'account proprietario del processo. Questa opzione è obbligatoria se il processo è in esecuzione come utente diverso dall'utente connesso. Il proprietario del processo è elencato nella colonna Nome utente nella scheda Processi di Gestione attività di Windows. |
   | [/crosssession](../profiling/crosssession.md) | Abilita la profilatura dei processi in altre sessioni di accesso. Questa opzione è obbligatoria se l'applicazione ASP.NET è in esecuzione in una sessione diversa. L'ID di sessione è elencato nella colonna ID sessione nella scheda Processi di Gestione attività di Windows. È possibile specificare **/CS** come abbreviazione per **/crosssession**. |
   | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Specifica il dominio opzionale e il nome utente dell'account di accesso con cui viene eseguito il servizio. L'account di accesso è elencato nella colonna Accedi come del servizio in Gestione controllo servizi di Windows. |
   | [/crosssession&#124;cs](../profiling/crosssession.md) | Abilita la profilatura dei processi in altre sessioni di accesso. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Specifica un contatore delle prestazioni di Windows per cui raccogliere i dati durante la profilatura. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Usare solo con **/wincounter**. Specifica il numero di millisecondi tra gli eventi di raccolta dei dati dei contatori delle prestazioni di Windows. Il valore predefinito è 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Specifica un evento di Event Tracing for Windows (ETW) da raccogliere durante la profilatura. Gli eventi ETW vengono raccolti in un file separato con estensione etl. |

8. Connettere il profiler al servizio. Digitare:

    **VSPerfCmd**[/attach:](../profiling/attach.md) {&#124;} `PID` [ `ProcName` [/targetclr](../profiling/targetclr.md)**:** `Version` ]  

   - Specificare l'ID processo o il nome del processo del servizio. È possibile visualizzare gli ID processo e i nomi di tutti i processi in esecuzione in Gestione attività di Windows.

   - **targetclr:** `Version` specifica la versione di Common Language Runtime (CLR) da profilare quando più di una versione del runtime è caricata in un'applicazione. facoltativo.

## <a name="control-data-collection"></a>Controllare la raccolta dati
 Mentre il servizio è in esecuzione, è possibile usare le opzioni di *VSPerfCmd.exe* per arrestare e avviare la scrittura dei dati nel file di dati del profiler. Il controllo della raccolta dei dati consente di raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.

#### <a name="to-start-and-stop-data-collection"></a>Per avviare o interrompere la raccolta dei dati

- Le coppie di opzioni **vsPerfCmd seguenti** avviano e arrestano la raccolta dati. Specificare ogni opzione in una riga di comando separata. È possibile attivare e disattivare la raccolta dei dati più volte.

    |Opzione|Descrizione|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Avvia (**/globalon**) o interrompe (**/globaloff**) la raccolta dei dati per tutti i processi.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Avvia (**/processon**) o interrompe (**/processoff**) la raccolta dei dati per il processo specificato dall'ID di processo (`PID`).|
    |**/attach:**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[:{ `PID`&#124;`ProcName` }]|**/attach** inizia a raccogliere dati per il processo specificato dall'ID o dal nome di processo. **/detach** interrompe la raccolta dei dati per il processo specificato o per tutti i processi se non viene specificato un processo specifico.|

## <a name="end-the-profiling-session"></a>Terminare la sessione di profilatura
 Per terminare una sessione di profilatura, non deve essere in corso una raccolta di dati dal profiler. È possibile interrompere la raccolta dei dati da un'applicazione profilata con il metodo di campionamento interrompendo il servizio oppure chiamando l'opzione **VSPerfCmd /detach**. Chiamare quindi **l'opzione VSPerfCmd** [/shutdown](../profiling/shutdown.md) per disattivare il profiler e chiudere il file di dati di profilatura. Il comando **VSPerfClrEnv /globaloff** cancella le variabili di ambiente di profilatura, ma la configurazione di sistema non viene reimpostata fino al riavvio del computer.

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
- [Viste dati di memoria .NET](../profiling/dotnet-memory-data-views.md)
