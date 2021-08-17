---
title: Connettere il profiler alle app native & raccogliere dati di concorrenza
description: Usare Visual Studio Strumenti di profilatura strumenti da riga di comando per collegare il profiler a un'applicazione nativa in esecuzione (C/C++) autonoma e ottenere i dati relativi ai thread.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 12d3e0f3-4b74-4e66-8fbf-8ac99bd4f91c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: cc19b7a377d689bb0fee3520cd71f231a4f67cea93c13537d5636acb3335f3ec
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121368427"
---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line"></a>Procedura: Connettere il profiler a un'applicazione autonoma nativa e raccogliere dati di concorrenza tramite la riga di comando
Questo articolo descrive come usare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per connettere il profiler a un'applicazione autonoma nativa (C/C++) in esecuzione e raccogliere dati sui conflitti di thread.

> [!NOTE]
> Per ottenere il percorso degli strumenti di profilatura, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso.

 Mentre il profiler è connesso all'applicazione, è possibile sospendere e riprendere la raccolta dei dati. Per terminare una sessione di profilatura, il profiler non deve essere più connesso all'applicazione e deve essere arrestato in modo esplicito.

## <a name="attach-the-profiler-to-a-running-native-application"></a>Connettere il profiler a un'applicazione nativa in esecuzione

#### <a name="to-attach-the-profiler-to-a-running-native-application"></a>Per connettere il profiler a un'applicazione nativa in esecuzione

1. Al prompt dei comandi digitare il comando seguente:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency**

     È possibile usare una qualsiasi delle opzioni nella tabella seguente con l'opzione **/start:concurrency**.

    |Opzione|Descrizione|
    |------------|-----------------|
    |[/user](../profiling/user-vsperfcmd.md) **:**[ `Domain\` ]`Username`|Specifica il dominio facoltativo e il nome utente dell'account a cui concedere l'accesso al profiler.|
    |[/crosssession](../profiling/crosssession.md)|Abilita la profilatura dei processi in altre sessioni di accesso.|
    |[/wincounter](../profiling/wincounter.md) **:**`WinCounterPath`|Specifica un contatore delle prestazioni di Windows per cui raccogliere i dati durante la profilatura.|
    |[/automark](../profiling/automark.md) **:**`Interval`|Usare solo con **/wincounter**. Specifica il numero di millisecondi tra gli eventi di raccolta dei dati dei contatori delle prestazioni di Windows. Il valore predefinito è 500.|
    |[/events](../profiling/events-vsperfcmd.md) **:**`Config`|Specifica un evento di Event Tracing for Windows (ETW) da raccogliere durante la profilatura. Gli eventi ETW vengono raccolti in un file separato con estensione etl.|

2. Connettere il profiler all'applicazione di destinazione digitando il comando seguente:

     **VSPerfCmd**[/attach:](../profiling/attach.md) { `PID`&#124;`ProcName` }  

     `PID` specifica l'ID del processo dell'applicazione di destinazione. È possibile visualizzare gli ID di processo di tutti i processi in esecuzione in Gestione attività di Windows.

## <a name="control-data-collection"></a>Controllare la raccolta dati
 Mentre è in esecuzione l'applicazione di destinazione, è possibile controllare la raccolta dei dati avviando e interrompendo la scrittura dei dati nel file usando le opzioni *VSPerfCmd.exe*. Per controllare la raccolta dei dati, è possibile raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o arresto dell'applicazione.

#### <a name="to-start-and-stop-data-collection"></a>Per avviare o interrompere la raccolta dei dati

- Le coppie di opzioni nella tabella seguente consentono di avviare e interrompere la raccolta dei dati. Specificare ogni opzione in una riga di comando separata. È possibile attivare e disattivare la raccolta dei dati più volte.

    |Opzione|Descrizione|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Avvia (**/globalon**) o interrompe (**/globaloff**) la raccolta dei dati per tutti i processi.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Avvia (**/processon**) o interrompe (**/processoff**) la raccolta dei dati per il processo specificato dall'ID di processo (`PID`).|
    |[/attach:](../profiling/attach.md) { `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/attach** inizia a raccogliere dati per il processo specificato dall'ID di processo (`PID`) o dal nome di processo (*ProcName*). **/detach** interrompe la raccolta dei dati per il processo specificato o per tutti i processi se non viene specificato un processo.|

## <a name="end-the-profiling-session"></a>Terminare la sessione di profilatura
 Per terminare una sessione di profilatura, non deve essere in corso una raccolta di dati dal profiler. È possibile interrompere la raccolta dei dati da un'applicazione profilata con il metodo di campionamento chiudendo l'applicazione o richiamando l'opzione **VSPerfCmd /detach**. È quindi possibile richiamare l'opzione **VSPerfCmd /shutdown** per disattivare il profiler e chiudere il file di dati di profilatura.

#### <a name="to-end-a-profiling-session"></a>Per terminare una sessione di profilatura

1. Disconnettere il profiler dall'applicazione di destinazione chiudendola o digitando il comando seguente:

     **VSPerfCmd /detach**

2. Arrestare il profiler digitando il comando seguente:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)
