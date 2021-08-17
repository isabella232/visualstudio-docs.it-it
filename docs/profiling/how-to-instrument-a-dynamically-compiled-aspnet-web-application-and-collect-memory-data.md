---
title: Riga di comando del profiler - Instrumentare l'app ASP.NET dinamica, ottenere i dati di memoria
description: Informazioni su come usare gli strumenti Visual Studio Strumenti di profilatura riga di comando per raccogliere dati dettagliati sulle attività di memoria per un'applicazione ASP.NET dinamica.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 2cdd9903-39db-47e8-93dd-5e6a21bc3435
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 711f30b9dd93af7da03319a837e7990c437da6e5fd9efd5c0506cab1be247a3c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121355100"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Procedura: Instrumentare un'applicazione Web ASP.NET compilata dinamicamente e raccogliere dati di memoria tramite la riga di comando del profiler
Questo argomento descrive come usare gli strumenti della riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per raccogliere dati dettagliati dell'allocazione di memoria .NET e della durata degli oggetti per un'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] compilata in modo dinamico tramite il metodo di profilatura della strumentazione.

> [!NOTE]
> Per ottenere il percorso degli strumenti di profilatura, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso.

 Per raccogliere i dati sulle prestazioni da un'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], modificare il file *web.config* dell'applicazione di destinazione per abilitare lo strumento [VSInstr.exe](../profiling/vsinstr.md) per instrumentare i file dell'applicazione compilata in modo dinamico. Usare quindi lo strumento [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) per configurare il server che ospita l'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e abilitare la profilatura della memoria .NET impostando le variabili di ambiente appropriate e infine riavviare il computer.

 Per raccogliere i dati, avviare il profiler ed eseguire l'applicazione di destinazione. Mentre il profiler è collegato all'applicazione, è possibile sospendere e riprendere la raccolta dei dati. Dopo avere raccolto i dati appropriati, chiudere l'applicazione, chiudere il processo di lavoro IIS (Internet Information Services) e arrestare il profiler.

 Dopo aver completato l'attività di profilatura, ripristinare gli stati originali del file *web.config* e del server Web.

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>Configurare l'applicazione Web ASP.NET e il server Web

#### <a name="to-configure-the-aspnet-web-application-and-the-web-server"></a>Per configurare l'applicazione Web ASP.NET e il server Web

1. Modificare il file *web.config* dell'applicazione di destinazione. Vedere [Procedura: modificare file web.config per instrumentare e profilare applicazioni Web ASP.NET compilate dinamicamente](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md).

2. Aprire una finestra del prompt dei comandi nel computer che ospita l'applicazione Web.

3. Inizializzare le variabili di ambiente di profilatura. Digitare:

     **VSPerfClrEnv /globaltracegc**

     -oppure-

     **VSPerfClrEnv /globaltracegclife**

    - **/globaltracegc** abilita la raccolta dei dati di allocazione della memoria.

    - **/globaltracegclife** abilita la raccolta dei dati di allocazione della memoria e dei dati di durata degli oggetti.

4. Riavviare il computer.

## <a name="run-the-profiling-session"></a>Eseguire la sessione di profilatura

#### <a name="to-profile-the-aspnet-web-application"></a>Per profilare l'applicazione Web ASP.NET

1. Avvia il profiler. Digitare:

    **VSPerfCmd** [/start](../profiling/start.md) **:trace** [/output](../profiling/output.md) **:** [ `OutputFile` `Options` ]

   - L'opzione **/start:trace** inizializza il profiler.

   - **L'opzione /output:** `OutputFile` è obbligatoria con **/start**. `OutputFile` specifica il nome e la posizione dei dati di profilatura (.*vsp*) file.

     È possibile usare qualsiasi opzione tra le seguenti con l'opzione **/start:trace**.

   > [!NOTE]
   > Le opzioni **/user** e **/crosssession** sono in genere obbligatorie per le applicazioni ASP.NET.

   | Opzione | Descrizione |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Specifica il dominio facoltativo e il nome utente dell'account proprietario del processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Questa opzione è obbligatoria se il processo è in esecuzione come utente diverso dall'utente connesso. Il nome è elencato **nella colonna Nome** utente della **scheda** Processi di Windows Gestione attività. |
   | [/crosssession](../profiling/crosssession.md) | Abilita la profilatura dei processi in altre sessioni. Questa opzione è obbligatoria se l'applicazione è in esecuzione in una sessione diversa. L'ID sessione è elencato nella **colonna ID** sessione della **scheda** Processi Windows Gestione attività. È possibile specificare **/CS** come abbreviazione per **/crosssession**. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Avvia il profiler con la raccolta dei dati sospesa. Usare [/globalon](../profiling/globalon-and-globaloff.md) per riprendere la profilatura. |
   | [/counter](../profiling/counter.md) **:**`Config` | Raccoglie informazioni dal contatore delle prestazioni del processore specificato in Config`Config`. Le informazioni del contatore vengono aggiunte ai dati raccolti a ogni evento di profilatura. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Specifica un contatore delle prestazioni di Windows per cui raccogliere i dati durante la profilatura. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Usare solo con **/wincounter**. Specifica il numero di millisecondi tra gli eventi di raccolta dei dati dei contatori delle prestazioni di Windows. Il valore predefinito è 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Specifica un evento di Event Tracing for Windows (ETW) da raccogliere durante la profilatura. Gli eventi ETW vengono raccolti in un file separato con estensione *etl*. |

2. Avviare l'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nel modo usuale.

## <a name="control-data-collection"></a>Controllare la raccolta dati
 Quando è in esecuzione l'applicazione di destinazione, è possibile controllare la raccolta dati avviando e interrompendo la scrittura dei dati nel file di dati del profiler usando le opzioni *VSPerfCmd.exe*. Il controllo della raccolta dei dati consente di raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.

#### <a name="to-start-and-stop-data-collection"></a>Per avviare o interrompere la raccolta dei dati

- Le seguenti coppie di opzioni consentono di avviare e interrompere la raccolta dei dati. Specificare ogni opzione in una riga di comando separata. È possibile attivare e disattivare la raccolta dei dati più volte.

    |Opzione|Descrizione|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Avvia (**/globalon**) o interrompe (**/globaloff**) la raccolta dei dati per tutti i processi.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Avvia (**/processon**) o interrompe (**/processoff**) la raccolta dei dati per il processo specificato dall'ID di processo (`PID`).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|Avvia (**/threadon**) o arresta (**/threadoff**) la raccolta dei dati per il thread specificato dall'ID thread (`TID`).|

- È anche possibile usare l'opzione **VSPerfCmd.exe**[/mark](../profiling/mark.md) per inserire un indicatore di profilatura nel file di dati. Il comando **/mark** aggiunge un identificatore, un timestamp e una stringa di testo facoltativa definita dall'utente. Gli indicatori possono essere usati per filtrare i dati nei rapporti e nelle visualizzazioni dei dati del profiler.

## <a name="end-the-profiling-session"></a>Terminare la sessione di profilatura
 Per terminare una sessione di profilatura, chiudere l'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] di destinazione, arrestare Internet Information Services (IIS) per interrompere il processo profilato e arrestare il profiler. Riavviare quindi IIS.

#### <a name="to-end-a-profiling-session"></a>Per terminare una sessione di profilatura

1. Chiudere l'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

2. Chiudere il processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] reimpostando Internet Information Services (IIS). Digitare:

    **IISReset /stop**

3. Arrestare il profiler. Digitare:

    **VSPerfCmd** [/shutdown](../profiling/shutdown.md)

4. Riavviare IIS. Digitare:

    **IISReset /start**

## <a name="restore-the-application-and-computer-configuration"></a>Ripristinare la configurazione dell'applicazione e del computer
 Dopo aver completato l'attività di profilatura, sostituire il file *web.config*, cancellare le variabili di ambiente di profilatura e riavviare il computer per ripristinare gli stati originali del server e dell'applicazione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

#### <a name="to-restore-the-application-and-computer-configuration"></a>Per ripristinare la configurazione dell'applicazione e del computer

1. Sostituire il file *web.config* con una copia del file originale.

2. (Facoltativo) Cancellare le variabili di ambiente di profilatura. Digitare:

     **VSPerfCmd /globaloff**

3. Riavviare il computer.

## <a name="see-also"></a>Vedi anche
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md)
