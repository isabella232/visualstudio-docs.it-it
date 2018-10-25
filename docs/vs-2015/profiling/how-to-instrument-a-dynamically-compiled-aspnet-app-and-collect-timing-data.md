---
title: "Procedura: Instrumentare un'applicazione Web ASP.NET compilata dinamicamente e raccogliere dati di intervallo dettagliati con il profiler tramite la riga di comando | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6c140ae2-ecdd-48c7-bd89-3dc1b88e19b0
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aedd447fa7c979497da0c1d56e6dd57531255cb0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912643"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>Procedura: instrumentare un'applicazione Web ASP.NET compilata dinamicamente e raccogliere dati di intervallo dettagliati con il profiler tramite la riga di comando
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questo argomento viene descritto come utilizzare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] gli strumenti da riga di comando degli strumenti di profilatura per raccogliere dati di intervallo dettagliati per compilata in modo dinamico [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] applicazione usando il metodo di profilatura della strumentazione.  

> [!NOTE]
>  Gli strumenti da riga di comando degli strumenti di profilatura sono disponibili nella sottodirectory \Team Tools\Performance Tools della directory di installazione di [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso. Per altre informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Per raccogliere i dati sulle prestazioni da un'applicazione Web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], modificare il file web.config dell'applicazione di destinazione per abilitare lo strumento [VSInstr.exe](../profiling/vsinstr.md) per instrumentare i file dell'applicazione compilata in modo dinamico. È quindi possibile usare lo strumento [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) per impostare le variabili di ambiente appropriate nel server Web per abilitare la profilatura, quindi riavviare il computer.  

 Avviare il profiler, quindi eseguire l'applicazione di destinazione. Mentre il profiler è connesso all'applicazione, è possibile sospendere e riprendere la raccolta dei dati. Al termine della profilatura, chiudere l'applicazione, chiudere il processo di lavoro di Internet Information Services (IIS), quindi arrestare il profiler. Dopo aver completato l'attività di profilatura, ripristinare gli stati originali del file web.config e del server Web.  

## <a name="configuring-the-aspnet-web-application-and-the-web-server"></a>Configurazione dell'applicazione Web ASP.NET e del server Web  

#### <a name="to-configure-the-aspnet-web-application-and-the-web-server"></a>Per configurare l'applicazione Web ASP.NET e il server Web  

1.  Modificare il file web.config dell'applicazione di destinazione. Vedere [Procedura: modificare file Web.Config per instrumentare e profilare applicazioni Web ASP.NET compilate dinamicamente](../profiling/how-to-modify-web-config-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications.md).  

2.  Aprire una finestra del prompt dei comandi.  

3.  Inizializzare le variabili di ambiente di profilatura. Tipo:  

     **VSPerfClrEnv /globaltraceon**  

    -   **/globaltraceon** abilita la profilatura tramite il metodo di strumentazione.  

4.  Riavviare il computer.  

## <a name="running-the-profiling-session"></a>Esecuzione della sessione di profilatura  

#### <a name="to-profile-the-web-application"></a>Per profilare l'applicazione Web  

1. Aprire una finestra del prompt dei comandi.  

2. Avvia il profiler. Tipo:  

    **VSPerfCmd**  [/start](../profiling/start.md) **:trace**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]  

   - L'opzione **/start:trace** inizializza il profiler.  

   - L'opzione **/output:**`OutputFile` è obbligatoria con **/start**. `OutputFile` specifica il nome e il percorso del file dei dati di profilatura (con estensione vsp).  

     È possibile usare qualsiasi opzione tra le seguenti con l'opzione **/start:trace**.  

   > [!NOTE]
   >  Le opzioni **/user** e **/crosssession** sono in genere obbligatorie per le applicazioni ASP.NET.  

   |                                 Opzione                                  |                                                                                                                                                       Descrizione                                                                                                                                                        |
   |-------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` |                   Specifica il dominio e il nome utente dell'account proprietario del processo di lavoro ASP.NET. Questa opzione è obbligatoria se il processo è in esecuzione come utente diverso dall'utente connesso. Il proprietario del processo è elencato nella colonna Nome utente nella scheda Processi di Gestione attività di Windows.                   |
   |              [/crosssession](../profiling/crosssession.md)              | Abilita la profilatura dei processi in altre sessioni di accesso. Questa opzione è obbligatoria se l'applicazione ASP.NET è in esecuzione in una sessione diversa. L'identificatore di sessione è elencato nella colonna ID sessione nella scheda Processi di Gestione attività di Windows. È possibile specificare **/CS** come abbreviazione per **/crosssession**. |
   |          [/globaloff](../profiling/globalon-and-globaloff.md)           |                                                                                              Avvia il profiler con la raccolta dei dati sospesa. Usare [/globalon](../profiling/globalon-and-globaloff.md) per riprendere la profilatura.                                                                                               |
   |           [/counter](../profiling/counter.md) **:** `Config`            |                                                                      Raccoglie informazioni dal contatore delle prestazioni del processore specificato in `Config`. Le informazioni del contatore vengono aggiunte ai dati raccolti a ogni evento di profilatura.                                                                      |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                                                                        Specifica un contatore delle prestazioni di Windows per cui raccogliere i dati durante la profilatura.                                                                                                                         |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                                                                      Usare solo con **/wincounter**. Specifica il numero di millisecondi tra gli eventi di raccolta dei dati dei contatori delle prestazioni di Windows. Il valore predefinito è 500 ms.                                                                                       |
   |       [/events](../profiling/events-vsperfcmd.md) **:** `Config`        |                                                                                         Specifica un evento di Event Tracing for Windows (ETW) da raccogliere durante la profilatura. Gli eventi ETW vengono raccolti in un file separato con estensione etl.                                                                                         |


3. Avviare l'applicazione Web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] nel modo usuale.  

## <a name="controlling-data-collection"></a>Controllo della raccolta di dati  
 Quando è in esecuzione l'applicazione di destinazione, è possibile controllare la raccolta dati avviando e interrompendo la scrittura dei dati nel file di dati del profiler usando le opzioni **VSPerfCmd.exe**. Il controllo della raccolta dei dati consente di raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.  

#### <a name="to-start-and-stop-data-collection"></a>Per avviare o interrompere la raccolta dei dati  

-   Le seguenti coppie di opzioni consentono di avviare e interrompere la raccolta dei dati. Specificare ogni opzione in una riga di comando separata. È possibile attivare e disattivare la raccolta dei dati più volte.  

    |Opzione|Descrizione|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Avvia (**/globalon**) o interrompe (**/globaloff**) la raccolta dei dati per tutti i processi.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Avvia (**/processon**) o interrompe (**/processoff**) la raccolta dei dati per il processo specificato dall'ID di processo (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Avvia (**/threadon**) o arresta (**/threadoff**) la raccolta dei dati per il thread specificato dall'ID thread (`TID`).|  

-   È anche possibile usare l'opzione **VSPerfCmd.exe**[/mark](../profiling/mark.md) per inserire un indicatore di profilatura nel file di dati. Il comando **/mark** aggiunge un identificatore, un timestamp e una stringa di testo facoltativa definita dall'utente. Gli indicatori possono essere usati per filtrare i dati nei rapporti e nelle visualizzazioni dei dati del profiler.  

## <a name="ending-the-profiling-session"></a>Arresto della sessione di profilatura  
 Per terminare una sessione di profilatura, chiudere l'applicazione Web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] di destinazione, reimpostare IIS per interrompere il processo profilato, quindi arrestare il profiler.  

#### <a name="to-end-a-profiling-session"></a>Per terminare una sessione di profilatura  

1.  Chiudere l'applicazione Web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  

2.  Chiudere il processo di lavoro [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] reimpostando Internet Information Services (IIS). Tipo:  

     **IISReset /stop**  

3.  Arrestare il profiler. Tipo:  

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)  

4.  Riavviare IIS. Tipo:  

     **IISReset /start**  

## <a name="restoring-the-application-and-computer-configuration"></a>Ripristino della configurazione dell'applicazione e del computer  
 Dopo aver completato l'attività di profilatura, sostituire il file web.config, cancellare le variabili di ambiente di profilatura e riavviare il computer per ripristinare gli stati antecedenti la profilatura del server e dell'applicazione.  

#### <a name="to-restore-the-application-and-computer-configuration"></a>Per ripristinare la configurazione dell'applicazione e del computer  

1.  Sostituire il file web.config con una copia del file originale.  

2.  Cancellare le variabili di ambiente di profilatura. Tipo:  

     **VSPerfCmd /globaloff**  

3.  Riavviare il computer.  

## <a name="see-also"></a>Vedere anche  
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Instrumentation Method Data Views](../profiling/instrumentation-method-data-views.md) (Visualizzazioni dei dati del metodo di strumentazione)



