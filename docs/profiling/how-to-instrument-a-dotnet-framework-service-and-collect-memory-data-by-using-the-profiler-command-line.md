---
title: Riga di comando del profiler - Instrumentare il servizio .NET e ottenere dati di memoria
description: Informazioni su come usare gli strumenti Visual Studio Strumenti di profilatura riga di comando per raccogliere dati sull'allocazione di memoria e sulla durata degli oggetti per un .NET Framework servizio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 2fa072fc-05fe-4420-99c0-51d2ea3ac4ce
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 60ad31c91123f3226227920e08c5194136cfe09ff774a045e1721b2091c527a1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121231184"
---
# <a name="how-to-instrument-a-net-framework-service-and-collect-memory-data-by-using-the-profiler-command-line"></a>Procedura: Instrumentare un servizio .NET Framework e raccogliere dati di memoria tramite la riga di comando del profiler

Questo articolo descrive come usare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per instrumentare un servizio .NET Framework e raccogliere dati di memoria. È possibile raccogliere i dati di allocazione della memoria oppure i dati di allocazione della memoria e i dati di durata degli oggetti.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> [!NOTE]
> Non è possibile profilare un servizio con il metodo di strumentazione se il servizio non può essere riavviato dopo l'avvio del computer, ad esempio un servizio che viene avviato all'avvio del sistema operativo.
>
> Per ottenere il percorso degli strumenti di profilatura, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso.

## <a name="start-the-profiling-session"></a>Avviare la sessione di profilatura
 Per raccogliere dati sulle prestazioni da un servizio .NET Framework, usare lo strumento [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) per inizializzare le variabili di ambiente appropriate e lo strumento [VSInstr.exe](../profiling/vsinstr.md) per creare una copia instrumentata del file binario del servizio.

 Per configurare il computer che ospita il servizio per la profilatura è necessario riavviarlo. È necessario anche avviare il servizio manualmente da Gestione controllo servizi. Avviare il profiler e quindi il servizio .NET Framework.

 Quando viene eseguito il componente instrumentato, i dati di memoria vengono raccolti automaticamente in un file di dati. È possibile sospendere e riprendere la raccolta dei dati durante la sessione di profilatura.

 Per terminare una sessione di profilatura, chiudere il servizio e arrestare in modo esplicito il profiler. Nella maggior parte dei casi è consigliabile cancellare le variabili di ambiente di profilatura alla fine di una sessione.

#### <a name="to-begin-profiling-a-net-framework-service"></a>Per iniziare la profilatura di un servizio .NET Framework

1. Aprire una finestra del prompt dei comandi.

2. Usare lo strumento **VSInstr** per generare una versione instrumentata del file binario del servizio.

3. Usare Gestione controllo servizi per sostituire il file binario originale con la versione instrumentata. Verificare che il tipo di avvio del servizio sia impostato su Manuale.

4. Inizializzare le variabili di ambiente di profilatura. Digitare:

    **VSPerfClrEnv** {**/globaltracegc** &#124; **/globaltracegclife**}

   - **/globaltracegc** e **/globaltracegclife** abilitano la raccolta dei dati di allocazione della memoria e dei dati di durata degli oggetti.

       |Opzione|Descrizione|
       |------------|-----------------|
       |**/globaltracegc**|Raccoglie solo i dati di allocazione della memoria.|
       |**/globaltracegclife**|Raccoglie i dati di allocazione della memoria e i dati di durata degli oggetti.|

5. Riavviare il computer.

6. Aprire una finestra del prompt dei comandi.

7. Avvia il profiler. Digitare:

    **VSPerfCmd**  [/start](../profiling/start.md) **:trace**  [/output](../profiling/output.md) **:** [ `OutputFile` `Options` ]

   - L'opzione **/start: contention** inizializza il profiler.

   - **L'opzione /output:** `OutputFile` è obbligatoria con **/start**. `OutputFile` specifica il nome e il percorso del file dei dati di profilatura (con estensione vsp).

     È possibile usare qualsiasi opzione tra le seguenti con l'opzione **/start:sample**.

   > [!NOTE]
   > Le opzioni **/user** e **/crosssession** sono in genere obbligatorie per i servizi.

   | Opzione | Descrizione |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Specifica il dominio e il nome utente dell'account proprietario del processo di lavoro ASP.NET. Questa opzione è obbligatoria se il processo è in esecuzione come utente diverso dall'utente connesso. Il proprietario del processo è elencato nella colonna Nome utente nella scheda Processi di Gestione attività di Windows. |
   | [/crosssession](../profiling/crosssession.md) | Abilita la profilatura dei processi in altre sessioni di accesso. Questa opzione è obbligatoria se l'applicazione ASP.NET è in esecuzione in una sessione diversa. L'ID sessione è elencato nella **colonna ID** sessione della **scheda** Processi di Windows Gestione attività. È possibile specificare **/CS** come abbreviazione per **/crosssession**. |
   | [/waitstart](../profiling/waitstart.md)[**:** `Interval` ] | Specifica il numero di secondi di attesa dell'inizializzazione del profiler prima che venga restituito un errore. Se `Interval` non viene specificato, il profiler attende per un tempo indefinito. Per impostazione predefinita, **/start** restituisce immediatamente un valore. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Per avviare il profiler con la raccolta dei dati in pausa, aggiungere l'opzione **/globaloff** alla riga di comando **/start**. Usare **/globalon** per riprendere la profilatura. |
   | [/counter](../profiling/counter.md) **:**`Config` | Raccoglie informazioni dal contatore delle prestazioni del processore specificato in Config. Le informazioni sui contatori vengono aggiunte ai dati raccolti a ogni evento di profilatura. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Specifica un contatore delle prestazioni di Windows per cui raccogliere i dati durante la profilatura. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Usare solo con **/wincounter**. Specifica il numero di millisecondi tra gli eventi di raccolta dei dati dei contatori delle prestazioni di Windows. Il valore predefinito è 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Specifica un evento di Event Tracing for Windows (ETW) da raccogliere durante la profilatura. Gli eventi ETW vengono raccolti in un file separato con estensione *etl*. |

8. Se necessario, avviare il servizio.

9. Connettere il profiler al servizio. Digitare:

     **VSPerfCmd /attach:** `PID`&#124;`ProcessName`

    - Specificare l'ID processo o il nome del processo del servizio. È possibile visualizzare gli ID processo e i nomi di tutti i processi in esecuzione in Gestione attività di Windows.

## <a name="control-data-collection"></a>Controllare la raccolta dati
 Mentre è in esecuzione il servizio, è possibile controllare la raccolta dei dati avviando e arrestando la scrittura dei dati nel file con le opzioni di *VSPerfCmd.exe*. Il controllo della raccolta dei dati consente di raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.

#### <a name="to-start-and-stop-data-collection"></a>Per avviare o interrompere la raccolta dei dati

- Le coppie di opzioni **vsPerfCmd seguenti** avviano e arrestano la raccolta dati. Specificare ogni opzione in una riga di comando separata. È possibile attivare e disattivare la raccolta dei dati più volte.

    |Opzione|Descrizione|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Avvia (**/globalon**) o interrompe (**/globaloff**) la raccolta dei dati per tutti i processi.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Avvia (**/processon**) o interrompe (**/processoff**) la raccolta dei dati per il processo specificato dall'ID di processo (`PID`).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|Avvia (**/threadon**) o arresta (**/threadoff**) la raccolta dei dati per il thread specificato dall'ID thread (`TID`).|

## <a name="end-the-profiling-session"></a>Terminare la sessione di profilatura
 Per terminare una sessione di profilatura, chiudere l'applicazione che esegue il componente instrumentato, quindi avviare l'opzione **VSPerfCmd** [/shutdown](../profiling/shutdown.md) per disattivare il profiler e chiudere il file di dati di profilatura. Il comando **VSPerfClrEnv /globaloff** cancella le variabili di ambiente di profilatura.

#### <a name="to-end-a-profiling-session"></a>Per terminare una sessione di profilatura

1. Arrestare il servizio da Gestione controllo servizi.

2. Arrestare il profiler. Digitare:

     **VSPerfCmd /shutdown**

3. Dopo aver completato tutte le profilature, deselezionare le variabili di ambiente di profilatura. Digitare:

     **VSPerfClrEnv /globaloff**

     Sostituire il modulo instrumentato con l'originale. Se necessario, riconfigurare il tipo di avvio del servizio.

4. Riavviare il computer.

## <a name="see-also"></a>Vedi anche
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)
- [Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md)
