---
title: Riga di comando del profiler - Instrumentare un componente .NET autonomo, ottenere dati di memoria
description: Informazioni su come usare gli strumenti Visual Studio Strumenti di profilatura riga di comando per raccogliere dati di memoria per un .NET Framework di un'applicazione autonoma.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d09cc46a-70f5-48f9-aa24-89913e67b359
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: ba20d0d640aa50d79af5ec7addf3a1f84e4c6edf69125f98414b00bf873a0450
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121426901"
---
# <a name="how-to-instrument-a-stand-alone-net-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line"></a>Procedura: Instrumentare un componente autonomo .NET Framework e raccogliere dati di memoria con il profiler tramite la riga di comando
Questo articolo descrive come usare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per instrumentare un componente .NET Framework di un'applicazione autonoma, ad esempio un file con estensione exe o dll, e raccogliere informazioni sulla memoria tramite il profiler.

> [!NOTE]
> Per ottenere il percorso degli strumenti di profilatura, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso.

 Per raccogliere dati di memoria da un componente .NET Framework tramite il metodo di strumentazione, usare lo strumento [VSInstr.exe](../profiling/vsinstr.md) per generare una versione instrumentata del componente e lo strumento [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) per inizializzare le variabili di ambiente di profilatura. Quindi avviare il profiler tramite lo strumento *VSPerfCmd.exe*.

 Quando viene eseguito il componente instrumentato, i dati di memoria vengono raccolti automaticamente in un file di dati. È possibile sospendere e riprendere la raccolta dei dati durante la sessione di profilatura.

 Per terminare una sessione di profilatura, chiudere l'applicazione di destinazione e arrestare in modo esplicito il profiler. Nella maggior parte dei casi è consigliabile cancellare le variabili di ambiente di profilatura alla fine di una sessione.

## <a name="start-the-application-with-the-profiler"></a>Avviare l'applicazione con il profiler

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Per connettere il profiler a un'applicazione .NET Framework in esecuzione

1. Aprire una finestra del prompt dei comandi.

2. Usare lo strumento **VSInstr** per generare una versione instrumentata dell'applicazione di destinazione.

3. Inizializzare le variabili di ambiente di profilatura di .NET Framework. Digitare:

    **VSPerfClrEnv** {**/tracegc** &#124; **/tracegclife**}

   - Le opzioni **/tracegc** e **/tracegclife** consentono di inizializzare le variabili di ambiente per raccogliere unicamente i dati sull'allocazione della memoria oppure i dati sull'allocazione della memoria e sulla durata degli oggetti.

       |Opzione|Descrizione|
       |------------|-----------------|
       |**/tracegc**|Abilita solo la raccolta dei dati sull'allocazione della memoria.|
       |**/tracegclife**|Abilita la raccolta dei dati relativi sia all'allocazione della memoria che alla durata degli oggetti.|

4. Avvia il profiler. Digitare:

    **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - [L'opzione /start](../profiling/start.md)**:trace** inizializza il profiler.

   - [L'opzione /output](../profiling/output.md)**:** è obbligatoria `OutputFile` con **/start**. `OutputFile` specifica il nome e la posizione dei dati di profilatura (.*vsp*) file.

     È possibile usare qualsiasi opzione tra le seguenti con l'opzione **/start:trace**.

   | Opzione | Descrizione |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Specifica il dominio e il nome utente dell'account proprietario del processo profilato. Questa opzione è obbligatoria solo se il processo è in esecuzione come utente diverso dall'utente connesso. Il proprietario del processo è elencato nella colonna Nome utente nella scheda **Processi** di Gestione attività di Windows. |
   | [/crosssession](../profiling/crosssession.md) | Abilita la profilatura dei processi in altre sessioni. Questa opzione è obbligatoria se l'applicazione è in esecuzione in una sessione diversa. L'identificatore di sessione è elencato nella colonna **ID sessione** della scheda **Processi** di Gestione attività di Windows. È possibile specificare **/CS** come abbreviazione per **/crosssession**. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Per avviare il profiler con la raccolta dei dati in pausa, aggiungere l'opzione **/globaloff** alla riga di comando **/start**. Usare **/globalon** per riprendere la profilatura. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Specifica un contatore delle prestazioni di Windows per cui raccogliere i dati durante la profilatura. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Usare solo con **/wincounter**. Specifica il numero di millisecondi tra gli eventi di raccolta dei dati dei contatori delle prestazioni di Windows. Il valore predefinito è 500 ms. |
   | [/counter](../profiling/counter.md) **:**`Config` | Raccoglie informazioni dal contatore delle prestazioni del processore specificato in Config. Le informazioni sui contatori vengono aggiunte ai dati raccolti a ogni evento di profilatura. |
   | [events](../profiling/events-vsperfcmd.md) **:**`Config` | Specifica un evento di Event Tracing for Windows (ETW) da raccogliere durante la profilatura. Gli eventi ETW vengono raccolti in un file separato con estensione *etl*. |

5. Avviare l'applicazione di destinazione nella finestra del prompt dei comandi.

## <a name="control-data-collection"></a>Controllare la raccolta dati
 Mentre è in esecuzione l'applicazione di destinazione, è possibile controllare la raccolta dei dati avviando e interrompendo la scrittura dei dati nel file usando le opzioni *VSPerfCmd.exe*. Il controllo della raccolta dei dati consente di raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.

#### <a name="to-start-and-stop-data-collection"></a>Per avviare o interrompere la raccolta dei dati

- Le coppie di opzioni **vsPerfCmd seguenti** avviano e arrestano la raccolta dati. Specificare ogni opzione in una riga di comando separata. È possibile attivare e disattivare la raccolta dei dati più volte.

    |Opzione|Descrizione|
    |------------|-----------------|
    |[/globalon](../profiling/globalon-and-globaloff.md) [/globaloff](../profiling/globalon-and-globaloff.md)|Avvia (**/globalon**) o interrompe (**/globaloff**) la raccolta dei dati per tutti i processi.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Avvia (**/processon**) o interrompe (**/processoff**) la raccolta dei dati per il processo specificato dall'ID di processo (`PID`).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|Avvia (**/threadon**) o interrompe (**/threadoff**) la raccolta dei dati per il thread specificato dall'ID del thread (`TID`).|

## <a name="end-the-profiling-session"></a>Terminare la sessione di profilatura
 Per terminare una sessione di profilatura, chiudere l'applicazione che esegue il componente instrumentato e quindi chiamare l'opzione **VSPerfCmd** [/shutdown](../profiling/shutdown.md) per disattivare il profiler e chiudere il file di dati di profilatura. Il comando **VSPerfClrEnv /off** cancella le variabili di ambiente di profilatura.

#### <a name="to-end-a-profiling-session"></a>Per terminare una sessione di profilatura

1. Chiudere l'applicazione di destinazione.

2. Arrestare il profiler. Digitare:

     **VSPerfCmd /shutdown**

3. (Facoltativo) Cancellare le variabili di ambiente di profilatura. Digitare:

     **VSPerfCmd /off**

## <a name="see-also"></a>Vedi anche
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md)
