---
title: Riga di comando del profiler - Instrumentare l'app ASP.NET statica, ottenere i dati di memoria
description: Informazioni su come usare gli strumenti Visual Studio Strumenti di profilatura riga di comando per raccogliere dati di memoria e temporizzazione per un componente Web o un sito Web ASP.NET precompilato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ea1dcb7c-1dc3-49ff-9418-8795b5b3d3bc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: feae93bd802dc40640494a5725d0c9f6f0ce8d0c036b8c12daa2c14c039064e0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121410684"
---
# <a name="how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Procedura: Instrumentare un'applicazione Web ASP.NET compilata staticamente e raccogliere dati di memoria tramite la riga di comando del profiler
Questo articolo descrive come usare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per instrumentare un componente Web o un sito Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] precompilato e raccogliere dati di allocazione di memoria, di durata degli oggetti e di intervallo dettagliati .NET.

> [!NOTE]
> Per ottenere il percorso degli strumenti di profilatura, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso.

 Per raccogliere dati da un componente Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] usando il metodo di strumentazione, usare lo strumento [VSInstr.exe](../profiling/vsinstr.md) per generare una versione instrumentata del componente. Nel computer che ospita il componente sostituire la versione non instrumentata del componente con la versione instrumentata. Usare quindi lo strumento [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) per inizializzare le variabili di ambiente di profilatura globali e riavviare il computer host. Avviare quindi il profiler.

 Quando viene eseguito il componente instrumentato, i dati di intervallo vengono raccolti automaticamente in un file di dati. È possibile sospendere e riprendere la raccolta dei dati durante la sessione di profilatura.

 Per terminare una sessione di profilatura, chiudere il processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] che ospita il componente e quindi arrestare in modo esplicito il profiler. Nella maggior parte dei casi è consigliabile cancellare le variabili di ambiente di profilatura alla fine di una sessione.

## <a name="start-to-profile"></a>Avviare la profilatura

#### <a name="to-instrument-an-aspnet-web-component-and-start-profiling"></a>Per instrumentare un componente Web ASP.NET e avviare la profilatura

1. Usare lo strumento **VSInstr** per generare una versione instrumentata dell'applicazione di destinazione. Se necessario, sostituire i file binari dell'applicazione nel computer host ASP.NET con i file binari instrumentati.

2. Aprire una finestra del prompt dei comandi

3. Inizializzare le variabili di ambiente di profilatura .NET. Nella finestra del prompt dei comandi digitare:

    **VSPerfClrEnv /globaltracegc**

    -oppure-

    **VSPerfClrEnv /globaltracegclife**

   - **/globaltracegc** raccoglie i dati di allocazione della memoria e i dati di intervallo .NET.

   - **/globaltracegclife** raccoglie i dati di allocazione della memoria, di durata degli oggetti e di intervallo dettagliati .NET.

4. Riavviare il computer.

5. Aprire una finestra del prompt dei comandi.

6. Avvia il profiler. Nella finestra del prompt dei comandi digitare:

    **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - [L'opzione /start](../profiling/start.md)**:trace** inizializza il profiler.

   - [L'opzione /output](../profiling/output.md)**:** è obbligatoria `OutputFile` con **/start**. `OutputFile` specifica il nome e il percorso del file dei dati di profilatura (con estensione vsp).

     È possibile usare qualsiasi opzione tra le seguenti con l'opzione **/start:trace**.

   > [!NOTE]
   > Le opzioni **/user** e **/crosssession** sono in genere obbligatorie per le applicazioni ASP.NET.

   | Opzione | Descrizione |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Specifica il dominio facoltativo e il nome utente dell'account proprietario del processo di lavoro ASP.NET. Questa opzione è obbligatoria se il processo è in esecuzione come utente diverso dall'utente connesso. Il nome è elencato nella colonna **Nome utente** della scheda **Processi** di Gestione attività di Windows. |
   | [/crosssession](../profiling/crosssession.md) | Abilita la profilatura dei processi in altre sessioni. Questa opzione è obbligatoria se l'applicazione è in esecuzione in una sessione diversa. L'ID sessione è elencato nella colonna ID sessione della **scheda** Processi Windows Gestione attività. È possibile specificare **/CS** come abbreviazione per **/crosssession**. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Specifica un contatore delle prestazioni di Windows per cui raccogliere i dati durante la profilatura. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Usare solo con **/wincounter**. Specifica il numero di millisecondi tra gli eventi di raccolta dei dati dei contatori delle prestazioni di Windows. Il valore predefinito è 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Specifica un evento di Event Tracing for Windows (ETW) da raccogliere durante la profilatura. Gli eventi ETW vengono raccolti in un file separato con estensione etl. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Per avviare il profiler con la raccolta dei dati in pausa, aggiungere l'opzione **/globaloff** alla riga di comando **/start**. Usare **/globalon** per riprendere la profilatura. |

7. Aprire il sito Web che contiene il componente instrumentato.

## <a name="control-data-collection"></a>Controllare la raccolta dati
 Mentre è in esecuzione l'applicazione di destinazione, è possibile controllare la raccolta dei dati avviando e interrompendo la scrittura dei dati nel file usando le opzioni *VSPerfCmd.exe*. Il controllo della raccolta dei dati consente di raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.

#### <a name="to-start-and-stop-data-collection"></a>Per avviare o interrompere la raccolta dei dati

- Le seguenti coppie di opzioni consentono di avviare e interrompere la raccolta dei dati. Specificare ogni opzione in una riga di comando separata. È possibile attivare e disattivare la raccolta dei dati più volte.

    |Opzione|Descrizione|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Avvia (**/globalon**) o interrompe (**/globaloff**) la raccolta dei dati per tutti i processi.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Avvia (**/processon**) o interrompe (**/processoff**) la raccolta dei dati per il processo specificato dall'ID di processo (`PID`).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|Avvia (**/threadon**) o arresta (**/threadoff**) la raccolta dei dati per il thread specificato dall'ID thread (`TID`).|

## <a name="end-the-profiling-session"></a>Terminare la sessione di profilatura
 Per terminare una sessione di profilatura, chiudere l'applicazione Web e quindi usare il comando [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] **IISReset** di Internet Information Services (IIS) per chiudere il processo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] di lavoro. Chiamare **l'opzione VSPerfCmd** [/shutdown](../profiling/shutdown.md) per disattivare il profiler e chiudere il file di dati di profilatura. Il comando **VSPerfClrEnv /globaloff** cancella le variabili di ambiente di profilatura. È necessario riavviare il computer per applicare le nuove impostazioni di ambiente.

#### <a name="to-end-a-profiling-session"></a>Per terminare una sessione di profilatura

1. Chiudere l'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

2. Chiudere il processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Digitare:

    **IISReset /stop**

3. Arrestare il profiler. Digitare:

    **VSPerfCmd /shutdown**

4. (Facoltativo) Cancellare le variabili di ambiente di profilatura. Digitare:

    **VSPerfCmd /globaloff**

5. Riavviare il computer. Se necessario, riavviare IIS. Digitare:

    **IISReset /start**

## <a name="see-also"></a>Vedi anche
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md)
