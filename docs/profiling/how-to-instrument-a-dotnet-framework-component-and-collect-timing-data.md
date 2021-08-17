---
title: Riga di comando del profiler - Instrumentare il componente .NET del client, ottenere i dati di ora
description: Informazioni su come usare gli Visual Studio Strumenti di profilatura da riga di comando per raccogliere dati di intervallo per un componente .NET Framework di un'applicazione autonoma.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: b7dcc27b-45c6-4302-9552-6fa5b1e94b56
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: f2df7702884071787292b335a9da9f7b6dfa43644890276035ba5b1e80de757e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121333015"
---
# <a name="how-to-instrument-a-stand-alone-net-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line"></a>Procedura: Instrumentare un componente autonomo .NET Framework e raccogliere dati di intervallo con il profiler tramite la riga di comando
In questo argomento viene descritto come usare Strumenti di profilatura strumenti da riga di comando per instrumentare un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .NET Framework, ad esempio .*exe* o . *dll* e per raccogliere dati di intervallo dettagliati.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Per ottenere il percorso degli strumenti di profilatura, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso.
>
> L'aggiunta di dati di interazione tra livelli a un'esecuzione di profilatura richiede procedure specifiche con gli strumenti di profilatura da riga di comando. Vedere [Raccolta di dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md).

 Per raccogliere dati di intervallo dettagliati da un componente .NET Framework tramite il metodo di strumentazione, usare lo strumento [VSInstr.exe](../profiling/vsinstr.md) per generare una versione instrumentata del componente e lo strumento [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) per inizializzare le variabili di ambiente di profilatura. Avviare quindi il profiler.

 Quando viene eseguito il componente instrumentato, i dati di intervallo vengono raccolti automaticamente in un file di dati. È possibile sospendere e riprendere la raccolta dei dati durante la sessione di profilatura.

 Per terminare una sessione di profilatura, chiudere l'applicazione di destinazione e arrestare in modo esplicito il profiler. Nella maggior parte dei casi è consigliabile cancellare le variabili di ambiente di profilatura alla fine di una sessione.

## <a name="start-the-profiling-session"></a>Avviare la sessione di profilatura

#### <a name="to-start-profiling-by-using-the-instrumentation-method"></a>Per avviare la profilatura tramite il metodo di strumentazione

1. Aprire una finestra del prompt dei comandi. Se necessario, aggiungere la directory degli strumenti di profilatura alla variabile di ambiente PATH. Il percorso non viene aggiunto al momento dell'installazione.

2. Usare lo strumento **VSInstr** per generare una versione instrumentata dell'applicazione di destinazione.

3. Inizializzare le variabili di ambiente di profilatura di .NET Framework. Digitare:

    **VSPerfClrEnv /traceon**

4. Avvia il profiler. Digitare:

    **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - [L'opzione /start](../profiling/start.md)**:trace** inizializza il profiler.

   - [L'opzione /output](../profiling/output.md)**:** è obbligatoria `OutputFile` con **/start**. `OutputFile` specifica il nome e il percorso del file dei dati di profilatura (con estensione vsp).

     È possibile usare una delle opzioni seguenti con l'opzione **/start:trace**.

   | Opzione | Descrizione |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Specifica il dominio e il nome utente dell'account proprietario del processo profilato. Questa opzione è obbligatoria solo se il processo è in esecuzione come utente diverso dall'utente connesso. Il proprietario del processo è elencato nella colonna **Nome utente** nella scheda **Processi** di Gestione attività di Windows. |
   | [/crosssession](../profiling/crosssession.md) | Abilita la profilatura dei processi in altre sessioni. Questa opzione è obbligatoria se l'applicazione ASP.NET è in esecuzione in una sessione diversa. L'identificatore di sessione è elencato nella colonna **ID sessione** della scheda **Processi** di Gestione attività di Windows. È possibile specificare **/CS** come abbreviazione per **/crosssession**. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Avvia il profiler con la raccolta dei dati sospesa. Usare [/globalon](../profiling/globalon-and-globaloff.md) per riprendere la profilatura. |
   | [/counter](../profiling/counter.md) **:**`Config` | Raccoglie informazioni dal contatore delle prestazioni del processore specificato in `Config`. Le informazioni del contatore vengono aggiunte ai dati raccolti a ogni evento di profilatura. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Specifica un contatore delle prestazioni di Windows per cui raccogliere i dati durante la profilatura. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Usare solo con **/wincounter**. Specifica il numero di millisecondi tra gli eventi di raccolta dei dati dei contatori delle prestazioni di Windows. Il valore predefinito è 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Specifica un evento di Event Tracing for Windows (ETW) da raccogliere durante la profilatura. Gli eventi ETW vengono raccolti in un file separato con estensione *etl*. |

5. Avviare l'applicazione di destinazione nella finestra del prompt dei comandi.

## <a name="control-data-collection"></a>Controllare la raccolta dati
 Quando è in esecuzione l'applicazione di destinazione, è possibile controllare la raccolta dei dati avviando e interrompendo la scrittura dei dati nel file di dati del profiler usando le opzioni *VSPerfCmd.exe*. Il controllo della raccolta dei dati consente di raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.

#### <a name="to-start-and-stop-data-collection"></a>Per avviare o interrompere la raccolta dei dati

- Le seguenti coppie di opzioni consentono di avviare e interrompere la raccolta dei dati. Specificare ogni opzione in una riga di comando separata. È possibile attivare e disattivare la raccolta dei dati più volte.

    |Opzione|Descrizione|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Avvia (**/globalon**) o interrompe (**/globaloff**) la raccolta dei dati per tutti i processi.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Avvia (**/processon**) o interrompe (**/processoff**) la raccolta dei dati per il processo specificato dall'ID di processo (`PID`).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|Avvia (**/threadon**) o arresta (**/threadoff**) la raccolta dei dati per il thread specificato dall'ID thread (`TID`).|

## <a name="end-the-profiling-session"></a>Terminare la sessione di profilatura
 Per terminare una sessione di profilatura, chiudere l'applicazione che esegue il componente instrumentato. Chiamare **l'opzione VSPerfCmd** [/shutdown](../profiling/shutdown.md) per disattivare il profiler e chiudere il file di dati di profilatura. Il comando **VSPerfClrEnv /off** cancella le variabili di ambiente di profilatura.

#### <a name="to-end-a-profiling-session"></a>Per terminare una sessione di profilatura

1. Chiudere l'applicazione di destinazione.

2. Arrestare il profiler. Digitare:

     **VSPerfCmd /shutdown**

3. (Facoltativo) Cancellare le variabili di ambiente di profilatura. Digitare:

     **VSPerfClrEnv /off**

## <a name="see-also"></a>Vedi anche
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Visualizzazioni dei dati del metodo di strumentazione](../profiling/instrumentation-method-data-views.md)
