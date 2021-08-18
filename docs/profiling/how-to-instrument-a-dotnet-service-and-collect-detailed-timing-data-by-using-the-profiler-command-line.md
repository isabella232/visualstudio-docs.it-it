---
title: Riga di comando del profiler - Instrumentare il servizio .NET, ottenere i dettagli di intervallo
description: Informazioni su come usare gli strumenti Visual Studio Strumenti di profilatura riga di comando per raccogliere dati di intervallo dettagliati per un .NET Framework servizio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 8781170e8f934f457ae16d6193636819f12179ad
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038825"
---
# <a name="how-to-instrument-a-net-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Procedura: Instrumentare un servizio .NET e raccogliere dati di intervallo dettagliati tramite la riga di comando del profiler

Questo articolo descrive come usare gli strumenti da riga di comando disponibili negli strumenti di profilatura di Visual Studio per instrumentare un servizio .NET Framework e raccogliere dati di intervallo dettagliati.

> [!NOTE]
> Non è possibile profilare un servizio con il metodo di strumentazione se il servizio non può essere riavviato dopo l'avvio del computer, ad esempio un servizio che viene avviato solo all'avvio del sistema operativo.
>
> Per ottenere il percorso degli strumenti di profilatura, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso.
>
> L'aggiunta di dati di interazione tra livelli a un'esecuzione di profilatura richiede procedure specifiche con gli strumenti di profilatura da riga di comando. Vedere [Raccolta di dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md).

Per raccogliere dati di intervallo dettagliati da un servizio .NET Framework tramite il metodo di strumentazione, usare lo strumento [VSInstr.exe](../profiling/vsinstr.md) per generare una versione instrumentata del componente. Sostituire quindi la versione non instrumentata del servizio con la versione instrumentata, assicurandosi che il servizio sia configurato per l'avvio manuale. Usare lo strumento [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) per inizializzare le variabili di ambiente di profilatura globali e quindi riavviare il computer host. Avviare quindi il profiler.

Quando viene avviato il servizio, i dati di intervallo vengono raccolti automaticamente in un file di dati. È possibile sospendere e riprendere la raccolta dei dati durante la sessione di profilatura.

Per terminare una sessione di profilatura, chiudere il servizio e arrestare in modo esplicito il profiler. Nella maggior parte dei casi è consigliabile cancellare le variabili di ambiente di profilatura alla fine di una sessione.

## <a name="start-the-application-with-the-profiler"></a>Avviare l'applicazione con il profiler

1. Aprire una finestra del prompt dei comandi.

2. Usare lo strumento **VSInstr** per generare una versione instrumentata del file binario del servizio.

3. Sostituire il file binario originale con la versione instrumentata. In Gestione controllo servizi di Windows assicurarsi che tipo di avvio del servizio sia impostato su Manuale.

4. Inizializzare le variabili di ambiente di profilatura di .NET Framework. Digitare:

     **VSPerfClrEnv /globaltraceon**

5. Riavviare il computer.

6. Aprire una finestra del prompt dei comandi.

7. Avvia il profiler. Digitare:

     **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - [L'opzione /start](../profiling/start.md)**:trace** inizializza il profiler.

   - [L'opzione /output](../profiling/output.md)**:** è obbligatoria `OutputFile` con **/start**. `OutputFile` specifica il nome e la posizione dei dati di profilatura (.*vsp*) file.

     È possibile usare una delle opzioni seguenti con l'opzione **/start:trace**.

     > [!NOTE]
     > Le opzioni **/user** e **/crosssession** sono in genere obbligatorie per i servizi di profilatura.

     | Opzione | Descrizione |
     | - | - |
     | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Specifica il dominio e il nome utente dell'account proprietario del processo profilato. Questa opzione è obbligatoria solo se il processo è in esecuzione come utente diverso dall'utente connesso. Il proprietario del processo è elencato nella colonna **Nome utente** nella scheda **Processi** di Gestione attività di Windows. |
     | [/crosssession](../profiling/crosssession.md) | Abilita la profilatura dei processi in altre sessioni. Questa opzione è obbligatoria se l'applicazione è in esecuzione in una sessione diversa. L'ID sessione è elencato **nella colonna ID** sessione della **scheda** Processi Windows Gestione attività. È possibile specificare **/CS** come abbreviazione per **/crosssession**. |
     | [/waitstart](../profiling/waitstart.md)[**:** `Interval` ] | Specifica il numero di secondi di attesa dell'inizializzazione del profiler prima che venga restituito un errore. Se `Interval` non viene specificato, il profiler attende per un tempo indefinito. Per impostazione predefinita, **/start** restituisce immediatamente un valore. |
     | [/globaloff](../profiling/globalon-and-globaloff.md) | Per avviare il profiler con la raccolta dei dati in pausa, aggiungere l'opzione **/globaloff** alla riga di comando **/start**. Usare **/globalon** per riprendere la profilatura. |
     | [/counter](../profiling/counter.md) **:**`Config` | Raccoglie informazioni dal contatore delle prestazioni del processore specificato in Config. Le informazioni sui contatori vengono aggiunte ai dati raccolti a ogni evento di profilatura. |
     | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Specifica un contatore delle prestazioni di Windows per cui raccogliere i dati durante la profilatura. |
     | [/automark](../profiling/automark.md) **:**`Interval` | Usare solo con **/wincounter**. Specifica il numero di millisecondi tra gli eventi di raccolta dei dati dei contatori delle prestazioni di Windows. Il valore predefinito è 500 ms. |
     | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Specifica un evento di Event Tracing for Windows (ETW) da raccogliere durante la profilatura. Gli eventi ETW vengono raccolti in un file separato con estensione *etl*. |

8. Avviare il servizio da Gestione controllo servizi di Windows.

## <a name="control-data-collection"></a>Controllare la raccolta dati

Mentre il servizio è in esecuzione, è possibile usare le opzioni di *VSPerfCmd.exe* per avviare e arrestare la scrittura dei dati nel file di dati del profiler. Il controllo della raccolta dei dati consente di raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto del servizio.

- Le coppie di opzioni **vsPerfCmd seguenti** avviano e arrestano la raccolta dati. Specificare ogni opzione in una riga di comando separata. È possibile attivare e disattivare la raccolta dei dati più volte.

    |Opzione|Descrizione|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Avvia (**/globalon**) o interrompe (**/globaloff**) la raccolta dei dati per tutti i processi.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Avvia (**/processon**) o interrompe (**/processoff**) la raccolta dei dati per il processo specificato dall'ID di processo (`PID`).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|Avvia (**/threadon**) o arresta (**/threadoff**) la raccolta dei dati per il thread specificato dall'ID thread (`TID`).|

## <a name="end-the-profiling-session"></a>Terminare la sessione di profilatura

Per terminare una sessione di profilatura, arrestare il servizio che esegue il componente instrumentato e quindi chiamare l'opzione **VSPerfCmd** [/shutdown](../profiling/shutdown.md) per disattivare il profiler e chiudere il file di dati di profilatura. Il comando **VSPerfClrEnv /globaloff** cancella le variabili di ambiente di profilatura.

È necessario riavviare il computer per applicare le nuove impostazioni di ambiente.

1. Arrestare il servizio da Gestione controllo servizi.

2. Arrestare il profiler. Digitare:

     **VSPerfCmd /shutdown**

3. Dopo aver completato tutte le profilature, deselezionare le variabili di ambiente di profilatura. Digitare:

     **VSPerfClrEnv /globaloff**

4. Sostituire il modulo instrumentato con l'originale. Se necessario, riconfigurare il tipo di avvio del servizio.

5. Riavviare il computer.

## <a name="see-also"></a>Vedi anche

[Profilare i servizi](../profiling/command-line-profiling-of-services.md) 
 [Visualizzazioni dei dati del metodo di strumentazione](../profiling/instrumentation-method-data-views.md)
