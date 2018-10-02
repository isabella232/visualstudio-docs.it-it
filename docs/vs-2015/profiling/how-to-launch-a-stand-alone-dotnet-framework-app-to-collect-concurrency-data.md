---
title: "Procedura: Avviare un'applicazione .NET Framework autonoma con il profiler per raccogliere dati di concorrenza tramite la riga di comando | Microsoft Docs"
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17a48848-bd3e-44ef-9971-e39836ff1df2
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b79933d9d59d21b5f41926dd4b8ef5afa64950ba
ms.sourcegitcommit: d705e015cb525bfa87a0b93e93376c3956ec2707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/29/2018
ms.locfileid: "47590481"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Procedura: avviare un'applicazione .NET Framework autonoma con il profiler per raccogliere dati di concorrenza tramite la riga di comando
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: avviare un stand-alone applicazione .NET Framework con il Profiler per raccogliere dati di concorrenza tramite la riga di comando](https://docs.microsoft.com/visualstudio/profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line).  
  
Questo argomento descrive come usare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per avviare un'applicazione (client) autonoma .NET Framework e raccogliere dati di concorrenza di thread e processi  
  
> [!NOTE]
>  Gli strumenti da riga di comando degli strumenti di profilatura sono disponibili nella sottodirectory \Team Tools\Performance Tools della directory di installazione di [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso. Per altre informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Mentre il profiler è connesso all'applicazione, è possibile sospendere e riprendere la raccolta dei dati. Per terminare una sessione di profilatura, il profiler non deve essere più connesso all'applicazione e deve essere arrestato in modo esplicito.  
  
## <a name="starting-the-application-with-the-profiler"></a>Avvio dell'applicazione con il profiler  
 Per avviare un'applicazione di destinazione di .NET Framework con il profiler, usare VSPerfClrEnv.exe per impostare le variabili di profilatura di .NET Framework. Usare quindi le opzioni VSPerfCmd **/start** e **/launch** per inizializzare il profiler e avviare l'applicazione. È possibile specificare **/start** e **/launch** e le relative opzioni in un'unica riga di comando. È anche possibile aggiungere l'opzione **/globaloff** alla riga di comando per sospendere la raccolta dei dati all'avvio dell'applicazione di destinazione. Usare quindi **/globalon** su una riga di comando separata per iniziare la raccolta dati.  
  
#### <a name="to-start-an-application-with-the-profiler"></a>Per avviare un'applicazione con il profiler  
  
1.  Aprire una finestra del prompt dei comandi.  
  
2.  Avvia il profiler. Tipo:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency**[**,**{**ResourceOnly**&#124;**ThreadOnly**}] **/output:**`OutputFile` [`Options`]  
  
    -   L'opzione [/start](../profiling/start.md) inizializza il profiler.  
  
        |||  
        |-|-|  
        |**/start:concurrency**|Abilita sia la raccolta dei dati sui conflitti di risorse che dei dati sull'esecuzione dei thread.|  
        |**/start:concurrency,resourceonly**|Abilita la raccolta solo dei dati sui conflitti di risorse.|  
        |**/start:concurrency,threadonly**|Abilita la raccolta solo dei dati di esecuzione dei thread.|  
  
    -   L'opzione [/output](../profiling/output.md)**:**`OutputFile` è obbligatoria con **/start**. `OutputFile` specifica il nome e il percorso del file dei dati di profilatura (con estensione vsp).  
  
     È possibile usare qualsiasi opzione tra le seguenti con l'opzione **/start:concurrency**.  
  
    |Opzione|Descrizione|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`domain\`]`username`|Specifica il dominio facoltativo e il nome utente dell'account a cui concedere l'accesso al profiler.|  
    |[/crosssession](../profiling/crosssession.md)|Abilita la profilatura dei processi in altre sessioni di accesso.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Specifica un contatore delle prestazioni di Windows per cui raccogliere i dati durante la profilatura.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Usare solo con **/wincounter**. Specifica il numero di millisecondi tra gli eventi di raccolta dei dati dei contatori delle prestazioni di Windows. Il valore predefinito è 500 ms.|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Specifica un evento di Event Tracing for Windows (ETW) da raccogliere durante la profilatura. Gli eventi ETW vengono raccolti in un file separato con estensione etl.|  
  
3.  Avviare l'applicazione di destinazione. Tipo:  
  
     **VSPerfCmd**  [/launch](../profiling/launch.md) **:** `AppName` [`Options`] [`Sample Event`]  
  
     È possibile usare qualsiasi opzione tra le seguenti con l'opzione **/launch**.  
  
    |Opzione|Descrizione|  
    |------------|-----------------|  
    |[/args](../profiling/args.md) **:** `Arguments`|Specifica una stringa che contiene gli argomenti della riga di comando da passare all'applicazione di destinazione.|  
    |[/console](../profiling/console.md)|Avvia l'applicazione della riga di comando di destinazione in una finestra separata.|  
    |[/targetclr](../profiling/targetclr.md) **:** `Version`|Specifica la versione di Common Language Runtime (CLR) da profilare quando più di una versione del runtime è caricata in un'applicazione.|  
  
## <a name="controlling-data-collection"></a>Controllo della raccolta di dati  
 Mentre è in esecuzione l'applicazione di destinazione, è possibile controllare la raccolta dei dati avviando e interrompendo la scrittura dei dati nel file usando le opzioni VSPerfCmd.exe. Il controllo della raccolta dei dati consente di raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.  
  
#### <a name="to-start-and-stop-data-collection"></a>Per avviare o interrompere la raccolta dei dati  
  
1.  Le seguenti coppie di opzioni VSPerfCmd.exe consentono di avviare e interrompere la raccolta di dati. Specificare ogni opzione in una riga di comando separata. È possibile attivare e disattivare la raccolta dei dati più volte.  
  
    |Opzione|Descrizione|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Avvia (**/globalon**) o interrompe (**/globaloff**) la raccolta dei dati per tutti i processi.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Avvia (**/processon**) o interrompe (**/processoff**) la raccolta dei dati per il processo specificato dall'ID di processo (`PID`).|  
    |[/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/attach** inizia a raccogliere dati per il processo specificato dall'ID del processo (`PID`) o dal nome del processo (ProcName). **/detach** interrompe la raccolta dei dati per il processo specificato o per tutti i processi se non viene specificato un processo specifico.|  
  
## <a name="ending-the-profiling-session"></a>Arresto della sessione di profilatura  
 Per terminare una sessione di profilatura, non deve essere in corso una raccolta di dati dal profiler. È possibile interrompere la raccolta dei dati di concorrenza chiudendo l'applicazione profilata o richiamando l'opzione **VSPerfCmd /detach**. È quindi possibile richiamare l'opzione **VSPerfCmd /shutdown** per disattivare il profiler e chiudere il file di dati di profilatura. Il comando **VSPerfClrEnv /off** cancella le variabili di ambiente di profilatura.  
  
#### <a name="to-end-a-profiling-session"></a>Per terminare una sessione di profilatura  
  
1.  Eseguire una delle operazioni seguenti per disconnettere il profiler dall'applicazione di destinazione.  
  
    -   Chiudere l'applicazione di destinazione.  
  
         oppure  
  
    -   Digitare **VSPerfCmd /detach**  
  
2.  Arrestare il profiler  
  
     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolta di dati di concorrenza](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)



