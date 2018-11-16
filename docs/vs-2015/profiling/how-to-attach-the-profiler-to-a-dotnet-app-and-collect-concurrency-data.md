---
title: "Procedura: Connettere il profiler a un'applicazione .NET Framework autonoma per raccogliere dati su conflitti tramite la riga di comando | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fdd41576-797e-4312-8520-fee7bb767e4a
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0523b367ec00dd7551dcf30f5002d855a99bf79
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790409"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line"></a>Procedura: connettere il profiler a un'applicazione .NET Framework autonoma per raccogliere dati su conflitti tramite la riga di comando
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questo argomento descrive come usare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per connettere il profiler a un'applicazione NET Framework autonoma in esecuzione (client) e raccogliere dati sulla concorrenza di processi e thread.  
  
> [!NOTE]
>  Gli strumenti da riga di comando degli strumenti di profilatura sono disponibili nella sottodirectory \Team Tools\Performance Tools della directory di installazione di [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso. Per altre informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Mentre il profiler è connesso all'applicazione, è possibile sospendere e riprendere la raccolta dei dati. Per terminare una sessione di profilatura, il profiler non deve essere più connesso all'applicazione e deve essere arrestato in modo esplicito.  
  
## <a name="attaching-the-profiler"></a>Connessione del profiler  
  
#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Per connettere il profiler a un'applicazione .NET Framework in esecuzione  
  
1.  Aprire una finestra del prompt dei comandi.  
  
2.  Avvia il profiler. Tipo:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency  /output:** `OutputFile` [`Options`]  
  
     L'opzione [/output](../profiling/output.md)**:**`OutputFile` è obbligatoria con **/start**. `OutputFile` specifica il nome e il percorso del file dei dati di profilatura (con estensione vsp).  
  
     È possibile usare qualsiasi opzione tra le seguenti con l'opzione **/start:concurrency**.  
  
    |Opzione|Descrizione|  
    |------------|-----------------|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Specifica un contatore delle prestazioni di Windows per cui raccogliere i dati durante la profilatura.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Usare solo con **/wincounter**. Specifica il numero di millisecondi tra gli eventi di raccolta dei dati dei contatori delle prestazioni di Windows. Il valore predefinito è 500 ms.|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Specifica un evento di Event Tracing for Windows (ETW) da raccogliere durante la profilatura. Gli eventi ETW vengono raccolti in un file separato con estensione etl.|  
  
3.  Avviare l'applicazione di destinazione nel modo usuale.  
  
4.  Connettere il profiler all'applicazione di destinazione. Tipo:  
  
     **VSPerfCmd /attach:** `PID` [**/lineoff**] [**/targetclr:**`Version`]  
  
    -   `PID` specifica l'ID del processo dell'applicazione di destinazione. È possibile visualizzare gli ID di processo di tutti i processi in esecuzione in Gestione attività di Windows.  
  
    -   [/lineoff](../profiling/lineoff.md) disabilita la raccolta dei dati dei numeri di riga.  
  
    -   [/targetclr](../profiling/targetclr.md) **:** `Version` specifica la versione di Common Language Runtime (CLR) da profilare quando più di una versione del runtime è caricata in un'applicazione. Facoltativo.  
  
## <a name="controlling-data-collection"></a>Controllo della raccolta di dati  
 Mentre è in esecuzione l'applicazione di destinazione, è possibile controllare la raccolta dei dati avviando e interrompendo la scrittura dei dati nel file usando le opzioni VSPerfCmd.exe. Il controllo della raccolta dei dati consente di raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.  
  
#### <a name="to-start-and-stop-data-collection"></a>Per avviare o interrompere la raccolta dei dati  
  
-   Le seguenti coppie di opzioni VSPerfCmd.exe consentono di avviare e interrompere la raccolta di dati. Specificare ogni opzione in una riga di comando separata. È possibile attivare e disattivare la raccolta dei dati più volte.  
  
    |Opzione|Descrizione|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Avvia (**/globalon**) o interrompe (**/globaloff**) la raccolta dei dati per tutti i processi.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Avvia (**/processon**) o interrompe (**/processoff**) la raccolta dei dati per il processo specificato dall'ID di processo (`PID`).|  
    |[/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/attach** inizia a raccogliere dati per il processo specificato dall'ID del processo (`PID`) o dal nome del processo (ProcName). **/detach** interrompe la raccolta dei dati per il processo specificato o per tutti i processi se non viene specificato un processo specifico.|  
  
## <a name="ending-the-profiling-session"></a>Arresto della sessione di profilatura  
 Per terminare una sessione di profilatura, non deve essere in corso una raccolta di dati dal profiler. È possibile interrompere la raccolta dei dati da un'applicazione profilata con il metodo di concorrenza chiudendo l'applicazione o richiamando l'opzione **VSPerfCmd /detach**. È quindi possibile richiamare l'opzione **VSPerfCmd /shutdown** per disattivare il profiler e chiudere il file di dati di profilatura. Il comando **VSPerfClrEnv /off** cancella le variabili di ambiente di profilatura.  
  
#### <a name="to-end-a-profiling-session"></a>Per terminare una sessione di profilatura  
  
1.  Eseguire una delle operazioni seguenti per disconnettere il profiler dall'applicazione di destinazione.  
  
    -   Digitare **VSPerfCmd /detach**  
  
         oppure  
  
    -   Chiudere l'applicazione di destinazione.  
  
2.  Arrestare il profiler. Tipo:  
  
     VSPerfCmd[/shutdown](../profiling/shutdown.md)



