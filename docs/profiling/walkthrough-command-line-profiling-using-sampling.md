---
title: 'Procedura dettagliata: Profilatura dalla riga di comando tramite campionamento | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance tools, command-line tools
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6cfa4afeda38180825a9f17b47a4e959fdac092d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54960542"
---
# <a name="walkthrough-command-line-profiling-using-sampling"></a>Procedura dettagliata: Profilatura dalla riga di comando tramite campionamento

Questa procedura dettagliata illustra come eseguire la profilatura di un'applicazione mediante gli strumenti da riga di comando e il campionamento per identificare i problemi di prestazioni.

In questa procedura dettagliata verrà illustrato il processo di profilatura di un'applicazione gestita tramite gli strumenti da riga di comando e sarà descritto come usare il campionamento per isolare e identificare i problemi di prestazioni nell'applicazione.

In questa procedura dettagliata vengono illustrate le operazioni seguenti:

- Eseguire la profilatura di un'applicazione usando gli strumenti della riga di comando e il campionamento.
- Analizzare i risultati della profilatura campionati per individuare e risolvere i problemi di prestazioni.

## <a name="prerequisites"></a>Prerequisiti

- Conoscenza a livello intermedio di [!INCLUDE[csharp_current_short](../misc/includes/csharp_current_short_md.md)]
- Conoscenza a livello intermedio dell'uso degli strumenti della riga di comando
- Una copia dell'[esempio PeopleTrax](/visualstudio/profiling/performance-explorer)
- Per usare le informazioni fornite dalla profilatura, è consigliabile avere a disposizione informazioni sui simboli di debug.

## <a name="command-line-profiling-using-the-sampling-method"></a>Profilatura dalla riga di comando tramite il metodo di campionamento

Il campionamento è un metodo di profilatura mediante il quale viene eseguito periodicamente il polling di un processo specifico per determinare la funzione attiva. I dati risultanti forniscono un conteggio della frequenza con cui la funzione si trovava all'inizio dello stack di chiamate quando è stato eseguito il campionamento del processo.

> [!NOTE]
>  Per ottenere il percorso degli strumenti di profilatura, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso.  

### <a name="to-profile-the-peopletrax-application-by-using-the-sampling-method"></a>Per eseguire la profilatura dell'applicazione PeopleTrax tramite il metodo di campionamento

1. Installare l'applicazione di esempio PeopleTrax e compilare la versione di rilascio dell'applicazione.

2. Aprire una finestra del prompt dei comandi e aggiungere la directory degli strumenti di profilatura alla variabile di ambiente Path locale.

3. Cambiare la directory di lavoro, passando alla directory che contiene i file binari di PeopleTrax.

4. Digitare il comando seguente per impostare le variabili di ambiente appropriate:

    ```cmd
    VSPerfCLREnv /sampleon
    ```

5. Avviare la profilatura eseguendo *VSPerfCmd.exe*, ovvero lo strumento da riga di comando che controlla il profiler. Il comando seguente avvia l'applicazione e il profiler in modalità di campionamento:

    ```cmd
    VsPerfCmd /start:sample /output:PeopleTraxReport.vsp /launch:PeopleTrax.exe
    ```

     Il processo del profiler viene avviato e collegato al processo *PeopleTrax.exe*. Il processo del profiler inizia a scrivere i dati di profilatura raccolti nel file di report.

6. Fare clic su **Get People**.

7. Fare clic su **ExportData**.

     Verrà aperto il Blocco note con un nuovo file che contiene i dati esportati da **PeopleTrax**.

8. Chiudere il Blocco note e quindi chiudere l'applicazione **PeopleTrax**.

9. Arrestare il profiler. Digitare il comando seguente:

    ```cmd
    VSPerfCmd /shutdown
    ```

10. Usare il comando seguente per reimpostare le variabili di ambiente:

    ```cmd
    VSPerfCLREnv /sampleoff
    ```

11. I dati di profilatura vengono archiviati nel file con estensione *vsp*. Analizzare i risultati usando uno dei metodi seguenti:

    - Aprire il file con estensione *vsp* nell'IDE di Visual Studio.

         oppure

    - Generare un file con valori delimitati da virgole (*csv*) tramite lo strumento da riga di comando *VSPerfReport.exe*. Per generare report da usare all'esterno dell'IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], usare il comando seguente:

        ```cmd
        VSPerfReport <dir> PeopleTraxReport.vsp /output:<dir> /summary:all
        ```

## <a name="see-also"></a>Vedere anche

[Panoramica delle sessioni di prestazioni](../profiling/performance-session-overview.md)  
[Profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md)  
[VSPerfCmd](../profiling/vsperfcmd.md)  
[Informazioni sui valori dei dati di campionamento](../profiling/understanding-sampling-data-values.md)  
[Visualizzazioni dei report di prestazioni](../profiling/performance-report-views.md)