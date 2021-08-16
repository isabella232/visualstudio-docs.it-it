---
title: Connettere il profiler al ASP.NET per ottenere le statistiche dell'app
description: Usare Visual Studio Strumenti di profilatura da riga di comando per connettere il profiler a un'app Web ASP.NET e ottenere statistiche sulle prestazioni usando il metodo di campionamento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 3725ddbe-ce91-4469-991e-8c5ed048c618
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 12cd8d34e2ac7567e4f3c9a07ab2a779b070a189f2b5d90da5b1b62412c8d6c1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121426976"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line"></a>Procedura: Connettere il profiler a un'applicazione Web ASP.NET per raccogliere statistiche dell'applicazione tramite la riga di comando
Questo articolo descrive come usare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per connettere il profiler a un'applicazione Web ASP.NET e raccogliere statistiche sulle prestazioni tramite il metodo di campionamento.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> L'aggiunta di dati di interazione tra livelli a un'esecuzione di profilatura richiede procedure specifiche con gli strumenti di profilatura da riga di comando. Vedere [Raccolta di dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md).
>
> Per ottenere il percorso degli strumenti di profilatura, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso.

 Per raccogliere dati sulle prestazioni da un'applicazione Web ASP.NET, è necessario inizializzare le variabili di ambiente appropriate e riavviare il computer che ospita l'applicazione Web ASP.NET per configurare il server Web per la profilatura.

 Connettere quindi il profiler al processo di lavoro ASP.NET che ospita il sito Web. Mentre il profiler è connesso all'applicazione, è possibile sospendere e riprendere la raccolta dei dati.

 Per terminare una sessione di profilatura, il profiler deve essere disconnesso dall'applicazione profilata e deve essere arrestato in modo esplicito. Nella maggior parte dei casi è consigliabile cancellare le variabili di ambiente di profilatura alla fine di una sessione.

## <a name="start-the-profiler-and-attach-to-an-aspnet-web-application"></a>Avviare il profiler e connetterlo a un'applicazione Web ASP.NET

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>Per connettere il profiler a un'applicazione Web ASP.NET

1. Aprire una finestra del prompt dei comandi.

2. Inizializzare le variabili di ambiente di profilatura. Digitare:

    **VSPerfClrEnv /globalsampleon** [**/samplelineoff**]

   - **/globalsampleon** abilita il campionamento.

   - **/samplelineoff** disabilita l'assegnazione dei dati raccolti a righe specifiche del codice sorgente. Quando viene specificata questa opzione, i dati vengono assegnati solo alle funzioni.

3. Riavviare il computer.

4. Avvia il profiler. Tipo:**VSPerfCmd** [/start](../profiling/start.md)**:sample** [/output](../profiling/output.md)**:**[ `OutputFile` `Options` ]

   - **L'opzione /start:sample** inizializza il profiler.

   - **L'opzione /output:** `OutputFile` è obbligatoria con **/start**. `OutputFile` specifica il nome e il percorso del file dei dati di profilatura (con estensione vsp).

     È possibile usare una delle opzioni seguenti con l'opzione **/start:sample**.

   > [!NOTE]
   > Le opzioni **/user** e **/crosssession** sono in genere obbligatorie per le applicazioni ASP.NET.

   | Opzione | Descrizione |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Specifica il dominio e il nome utente dell'account proprietario del processo di lavoro ASP.NET. Questa opzione è obbligatoria se il processo è in esecuzione come utente diverso dall'utente connesso. Il proprietario del processo è elencato nella colonna **Nome utente** nella scheda **Processi** di Gestione attività di Windows. |
   | [/crosssession](../profiling/crosssession.md) | Abilita la profilatura dei processi in altre sessioni di accesso. Questa opzione è obbligatoria se l'applicazione ASP.NET è in esecuzione in una sessione diversa. L'identificatore di sessione è elencato nella colonna ID sessione nella scheda Processi di Gestione attività di Windows. È possibile specificare **/CS** come abbreviazione per **/crosssession**. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Specifica un contatore delle prestazioni di Windows per cui raccogliere i dati durante la profilatura. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Usare solo con **/wincounter**. Specifica il numero di millisecondi tra gli eventi di raccolta dei dati dei contatori delle prestazioni di Windows. Il valore predefinito è 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Specifica un evento di Event Tracing for Windows (ETW) da raccogliere durante la profilatura. Gli eventi ETW vengono raccolti in un file separato con estensione etl. |

5. Avviare l'applicazione Web ASP.NET nel modo usuale.

6. Connettere il profiler al processo di lavoro ASP.NET. Tipo:**VSPerfCmd** [/attach:](../profiling/attach.md){&#124;} [ ] `PID` [ `ProcName` `Sample Event` [/targetclr](../profiling/targetclr.md)**:** `Version` ]

   - `PID` specifica l'ID processo del processo di lavoro ASP.NET; `ProcName` specifica il nome del processo di lavoro. È possibile visualizzare gli ID processo e i nomi di tutti i processi in esecuzione in Gestione attività di Windows.

   - Per impostazione predefinita, i dati relativi alle prestazioni vengono campionati ogni 10.000.000 di cicli di clock del processore non interrotti, ovvero circa 100 volte al secondo in un processore da 1 GHz. È possibile specificare una delle opzioni di **VSPerfCmd** seguenti per modificare l'intervallo dei cicli di clock o per specificare un evento di campionamento diverso.

   |Evento di esempio|Descrizione|
   |------------------|-----------------|
   |[/timer](../profiling/timer.md) **:**`Interval`|Imposta l'intervallo di campionamento sul numero di cicli di clock non interrotti specificato da `Interval`.|
   |[/pf](../profiling/pf.md)[**:** `Interval` ]|Imposta l'evento di campionamento sugli errori di pagina. Se si specifica `Interval`, imposta il numero di errori di pagina tra campioni. Il valore predefinito è 10.|
   |[/sys](../profiling/sys-vsperfcmd.md)[ `:``Interval` ]|Imposta l'evento di campionamento sulle chiamate di sistema dal processo al kernel del sistema operativo (syscall). Se si specifica `Interval`, imposta il numero di chiamate tra campioni. Il valore predefinito è 10.|
   |[/counter](../profiling/counter.md) **:**`Config`|Imposta l'evento e l'intervallo di campionamento sul contatore delle prestazioni del processore e sull'intervallo specificati in `Config`.|
   |[/targetclr](../profiling/targetclr.md) **:**`Version`|Specifica la versione di Common Language Runtime (CLR) da profilare quando più di una versione del runtime è caricata in un'applicazione.|

   - **targetclr:** `Version` specifica la versione di CLR da profilare quando più di una versione del runtime è caricata in un'applicazione. facoltativo.

## <a name="control-data-collection"></a>Controllare la raccolta dati
 Mentre è in esecuzione l'applicazione, è possibile controllare la raccolta dei dati avviando e interrompendo la scrittura dei dati nel file usando le opzioni di *VSPerfCmd.exe*. Il controllo della raccolta dei dati consente di raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.

#### <a name="to-start-and-stop-data-collection"></a>Per avviare o interrompere la raccolta dei dati

- Le coppie di opzioni **vsPerfCmd seguenti** avviano e arrestano la raccolta dati. Specificare ogni opzione in una riga di comando separata. È possibile attivare e disattivare la raccolta dei dati più volte.

    |Opzione|Descrizione|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Avvia (**/globalon**) o interrompe (**/globaloff**) la raccolta dei dati per tutti i processi.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` **/processoff:**`PID`|Avvia (**/processon**) o interrompe (**/processoff**) la raccolta dei dati per il processo specificato da `PID`.|
    |[/attach:](../profiling/attach.md) { `PID`&#124;} `ProcName` [/detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/attach** inizia a raccogliere dati per il processo specificato da `PID` o dal nome del processo (ProcName). **/detach** arresta la raccolta dei dati per il processo specificato o per tutti i processi se non viene specificato un processo specifico.|

## <a name="end-the-profiling-session"></a>Terminare la sessione di profilatura
 Per terminare una sessione di profilatura, chiudere l'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e quindi usare il comando **IISReset** di Internet Information Services (IIS) per chiudere il processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Chiamare **l'opzione VSPerfCmd** [/shutdown](../profiling/shutdown.md) per disattivare il profiler e chiudere il file di dati di profilatura.

 Il comando **VSPerfClrEnv /globaloff** cancella le variabili di ambiente di profilatura. È necessario riavviare il computer per applicare le nuove impostazioni di ambiente.

 Il comando **VSPerfClrEnv /globaloff** cancella le variabili di ambiente di profilatura, ma la configurazione di sistema non viene reimpostata fino al riavvio del computer.

#### <a name="to-end-a-profiling-session"></a>Per terminare una sessione di profilatura

1. Eseguire una delle operazioni seguenti per disconnettere il profiler dall'applicazione di destinazione:

   - Digitare **VSPerfCmd /detach**

      -oppure-

   - Chiudere il processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

2. Arrestare il profiler. Tipo:**VSPerfCmd** [/shutdown](../profiling/shutdown.md)

3. (Facoltativo) Cancellare le variabili di ambiente di profilatura. Digitare:

    **VSPerfCmd /globaloff**

4. Riavviare il computer.

## <a name="see-also"></a>Vedi anche
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Visualizzazioni dei dati del metodo di campionamento](../profiling/profiler-sampling-method-data-views.md)
