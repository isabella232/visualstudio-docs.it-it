---
title: "Riga di comando del profiler: avviare un'app autonoma, ottenere le statistiche dell'app"
description: Informazioni su come usare gli Visual Studio Strumenti di profilatura da riga di comando per avviare un'app autonoma e raccogliere dati sulle prestazioni usando il metodo di campionamento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 52dcee2b-f178-4a76-bddc-e36c50bfcb78
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8a52a66da6607e5c8b85f6ac43bed9a0993d7ab57e64a1cb2630c11104a8b235
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121426781"
---
# <a name="how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line"></a>Procedura: Avviare un'applicazione autonoma con il profiler e raccogliere statistiche dell'applicazione usando la riga di comando
Questo argomento descrive come usare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per avviare un'applicazione (client) autonoma e raccogliere statistiche sulle prestazioni tramite il metodo di campionamento.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> L'aggiunta di dati di interazione tra livelli a un'esecuzione di profilatura richiede procedure specifiche con gli strumenti di profilatura da riga di comando. Vedere [Raccogliere dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md)

 Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra Prompt dei comandi oppure aggiungerlo al comando stesso. È possibile eseguire gli strumenti di profilatura in un computer in cui Visual Studio è installato da una finestra di comando di Visual Studio.

1. Se si eseguono gli strumenti di profilatura in un computer in cui è installato Visual Studio, una finestra di comando di Visual Studio imposta i percorsi corretti. Nel menu **Strumenti** scegliere **prompt dei comandi di VS**.

> [!NOTE]
> Per ottenere il percorso degli strumenti di profilatura, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso.

## <a name="start-the-application-with-the-profiler"></a>Avviare l'applicazione con il profiler
 Per avviare un'applicazione di destinazione tramite il profiler, usare le opzioni VSPerfCmd **/start** e **/launch** per inizializzare il profiler e avviare l'applicazione. È possibile specificare **/start** e **/launch** e le relative opzioni in un'unica riga di comando.

 È anche possibile aggiungere l'opzione **/globaloff** per sospendere la raccolta dei dati all'avvio dell'applicazione di destinazione. Usare quindi **/globalon** per avviare la raccolta dei dati.

#### <a name="to-start-an-application-by-using-the-profiler"></a>Per avviare un'applicazione con il profiler

1. Aprire una finestra del prompt dei comandi.

2. Avvia il profiler. Digitare:

    **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]

   - L'opzione [/start](../profiling/start.md)**:sample** inizializza il profiler.

   - [L'opzione /output](../profiling/output.md)**:** è obbligatoria `OutputFile` con **/start**. `OutputFile` specifica il nome e il percorso del file dei dati di profilatura (con estensione vsp).

     È possibile usare qualsiasi opzione tra le seguenti con l'opzione **/start:sample**.

   | Opzione | Descrizione |
   | - | - |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Specifica un contatore delle prestazioni di Windows per cui raccogliere i dati durante la profilatura. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Usare solo con **/wincounter**. Specifica il numero di millisecondi tra gli eventi di raccolta dei dati dei contatori delle prestazioni di Windows. Il valore predefinito è 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Specifica un evento di Event Tracing for Windows (ETW) da raccogliere durante la profilatura. Gli eventi ETW vengono raccolti in un file separato con estensione *etl*. |

3. Avviare l'applicazione di destinazione. Tipo:**VSPerfCmd /launch:** `appName` [ ] [ `Options` `Sample Event` ]

    È possibile usare una o più opzioni tra le seguenti con l'opzione **/launch**.

   |Opzione|Descrizione|
   |------------|-----------------|
   |[/args](../profiling/args.md) **:**`Arguments`|Specifica una stringa che contiene gli argomenti della riga di comando da passare all'applicazione di destinazione.|
   |[/console](../profiling/console.md)|Avvia l'applicazione della riga di comando di destinazione in una finestra separata.|

    Per impostazione predefinita, i dati relativi alle prestazioni vengono campionati ogni 10.000.000 di cicli di clock del processore non interrotti, ovvero circa una volta ogni 10 secondi su un processore da 1 GHz. È possibile specificare una delle opzioni seguenti per modificare l'intervallo dei cicli di clock o per specificare un evento di campionamento diverso.

   |Evento di esempio|Descrizione|
   |------------------|-----------------|
   |[/timer](../profiling/timer.md) **:**`Interval`|Imposta l'intervallo di campionamento sul numero di cicli di clock non interrotti specificato da `Interval`.|
   |[/pf](../profiling/pf.md)[**:** `Interval` ]|Imposta l'evento di campionamento sugli errori di pagina. Se si specifica `Interval`, imposta il numero di errori di pagina tra campioni. Il valore predefinito è 10.|
   |[/sys](../profiling/sys-vsperfcmd.md)[**:** `Interval` ]|Imposta l'evento di campionamento sulle chiamate di sistema dal processo al kernel del sistema operativo (syscall). Se si specifica `Interval`, imposta il numero di chiamate tra campioni. Il valore predefinito è 10.|
   |[/counter](../profiling/counter.md) **:**`Config`|Imposta l'evento e l'intervallo di campionamento sul contatore delle prestazioni del processore e sull'intervallo specificati in `Config`.|

## <a name="control-data-collection"></a>Controllare la raccolta dati
 Quando è in esecuzione l'applicazione di destinazione, è possibile controllare la raccolta dei dati avviando e interrompendo la scrittura dei dati nel file di dati del profiler usando le opzioni *VSPerfCmd.exe*. Il controllo della raccolta dei dati consente di raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.

#### <a name="to-start-and-stop-data-collection"></a>Per avviare o interrompere la raccolta dei dati

- Le seguenti coppie di opzioni consentono di avviare e interrompere la raccolta dei dati. Specificare ogni opzione in una riga di comando separata. È possibile attivare e disattivare la raccolta dei dati più volte.

    |Opzione|Descrizione|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Avvia (**/globalon**) o interrompe (**/globaloff**) la raccolta dei dati per tutti i processi.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**  `PID`|Avvia (**/processon**) o interrompe (**/processoff**) la raccolta dei dati per il processo specificato dall'ID di processo (`PID`).|
    |[/attach:](../profiling/attach.md) { `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/attach** inizia a raccogliere dati per il processo specificato da `PID` o dal nome del processo (ProcName). **/detach** arresta la raccolta dei dati per il processo specificato o per tutti i processi se non è specificato un processo specifico.|

## <a name="end-the-profiling-session"></a>Terminare la sessione di profilatura
 Per terminare una sessione di profilatura, il profiler non deve essere connesso ad alcun processo profilato e deve essere arrestato in modo esplicito. È possibile disconnettere il profiler da un'applicazione profilata tramite il metodo di campionamento chiudendo l'applicazione o chiamando l'opzione **VSPerfCmd /detach**. È quindi possibile chiamare l'opzione **VSPerfCmd /shutdown** per disattivare il profiler e chiudere il file di dati di profilatura. Il comando **VSPerfClrEnv /off** cancella le variabili di ambiente di profilatura.

#### <a name="to-end-a-profiling-session"></a>Per terminare una sessione di profilatura

1. Eseguire una delle operazioni seguenti per disconnettere il profiler dall'applicazione di destinazione:

    - Chiudere l'applicazione di destinazione.

         -oppure-

    - Digitare **VSPerfCmd /detach**

2. Arrestare il profiler. Digitare:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>Vedi anche
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Visualizzazioni dei dati del metodo di campionamento](../profiling/profiler-sampling-method-data-views.md)
