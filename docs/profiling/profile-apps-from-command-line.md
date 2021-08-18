---
title: Misurare le prestazioni dalla riga di comando
description: Misurare le prestazioni della CPU e managed memory'utilizzo nell'applicazione dalla riga di comando.
ms.custom: ''
ms.date: 02/21/2020
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, command-line
- Diagnostics Tools, command-line
- CPU Usage, command-line
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 9520c5a06621673b4f262d9adc313e63ada5b310
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076334"
---
# <a name="measure-application-performance-from-the-command-line"></a>Misurare le prestazioni dell'applicazione dalla riga di comando

È possibile raccogliere le informazioni sulle prestazioni di un'applicazione usando gli strumenti da riga di comando.

Nell'esempio descritto in questo articolo si raccolgono informazioni sulle prestazioni di Blocco note, ma lo stesso metodo può essere usato per profilare qualsiasi processo.

## <a name="prerequisites"></a>Prerequisiti

* Visual Studio 2019 o versioni successive

* Conoscenza degli strumenti da riga di comando

* Per raccogliere informazioni sulle prestazioni in un computer remoto senza Visual Studio installato, installare il Remote Tools per Visual Studio [nel](https://visualstudio.microsoft.com/downloads#remote-tools-for-visual-studio-2019) computer remoto. La versione degli strumenti deve corrispondere alla versione di Visual Studio.

## <a name="collect-performance-data"></a>Raccogliere i dati sulle prestazioni

Per eseguire la profilatura tramite gli strumenti da riga di comando di diagnostica di Visual Studio è necessario associare lo strumento di profilatura insieme a uno degli agenti di raccolta a un processo. Quando si associa lo strumento di profilatura, si avvia una sessione di diagnostica che acquisisce e archivia i dati di profilatura fino a quando lo strumento non viene arrestato. I dati vengono quindi esportati in un file con estensione *diagsession*. È quindi possibile aprire il file in Visual Studio per analizzare i risultati.

1. Avviare Blocco note e quindi aprire Gestione attività per ottenere gli ID processo (PID). In Gestione attività cercare il PID nella scheda **Dettagli**.

1. Aprire un prompt dei comandi e passare alla directory con il file eseguibile dell'agente di raccolta, in genere qui (ad Visual Studio Enterprise).

   ```<Visual Studio installation folder>\2019\Enterprise\Team Tools\DiagnosticsHub\Collector\```

1. Avviare *VSDiagnostics.exe* digitando il comando seguente.

   ```cmd
   VSDiagnostics.exe start <id> /attach:<pid> /loadConfig:<configFile>
   ```

   È necessario includere gli argomenti seguenti:

   * \<*id*> Identifica la sessione di raccolta. L'ID deve essere un numero compreso tra 1 e 255.
   * \<*pid*>, PID del processo da profilare, in questo caso il PID trovato nel passaggio 1.
   * \<*configFile*>, file di configurazione per l'agente di raccolta da avviare. Per altre informazioni, vedere [File di configurazione degli agenti](#config_file).

   Ad esempio, è possibile usare il comando seguente per l'agente CPUUsageBase sostituendo il *pid* come descritto in precedenza.

   ```cmd
   VSDiagnostics.exe start 1 /attach:<pid> /loadConfig:AgentConfigs\CPUUsageLow.json
   ```

1. Ridimensionare Blocco note o digitare un testo nell'applicazione per assicurarsi che vengano raccolte alcune informazioni di profilatura interessanti.

1. Arrestare la sessione di raccolta e inviare l'output in un file digitando il comando seguente.

   ```cmd
   VSDiagnostics.exe stop <id> /output:<path to file>
   ```

1. Individuare l'output del file con estensione *diagsession* del comando precedente e aprirlo in Visual Studio (**Apri file**) per esaminare le  >  informazioni raccolte.

   Per analizzare i risultati, vedere la documentazione per lo strumento per le prestazioni corrispondente. Ad esempio, potrebbe trattarsi dello strumento [Utilizzo CPU](../profiling/cpu-usage.md), Allocazione oggetti [.NET](../profiling/dotnet-alloc-tool.md)o [Database.](../profiling/analyze-database.md)

## <a name="agent-configuration-files"></a><a name="config_file"></a> File di configurazione degli agenti

Gli agenti di raccolta sono componenti intercambiabili che raccolgono tipi diversi di dati a seconda degli elementi che si sta tentando di misurare.

Per praticità, è consigliabile archiviare queste informazioni in un file di configurazione dell'agente. Il file di configurazione è un file con estensione *.json* che contiene almeno il nome del file con estensione *dll* e il relativo CLSID COM. Di seguito sono elencati i file di configurazione di esempio che è possibile trovare nella cartella seguente:

```<Visual Studio installation folder>Team Tools\DiagnosticsHub\Collector\AgentConfigs\```

Vedere i collegamenti seguenti per scaricare e visualizzare i file di configurazione dell'agente:

- https://aka.ms/vs/diaghub/agentconfig/cpubase
- https://aka.ms/vs/diaghub/agentconfig/cpuhigh
- https://aka.ms/vs/diaghub/agentconfig/cpulow
- https://aka.ms/vs/diaghub/agentconfig/database
- https://aka.ms/vs/diaghub/agentconfig/dotnetasyncbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetallocbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetalloclow
- https://aka.ms/vs/diaghub/agentconfig/dotnetcountersbase

Le configurazioni CpuUsage (Base/Alto/Basso) corrispondono ai dati raccolti per lo strumento di profilatura [utilizzo CPU.](../profiling/cpu-usage.md)
Le configurazioni dotNetObjectAlloc (Base/Bassa) corrispondono ai dati raccolti per lo strumento di allocazione [di oggetti .NET](../profiling/dotnet-alloc-tool.md).

Le configurazioni Base/Basso/Alto fanno riferimento alla frequenza di campionamento. Ad esempio, il valore Basso corrisponde a 100 campioni al secondo e Alto corrisponde a 4.000 campioni al secondo.

Perché lo *VSDiagnostics.exe* funzioni con un agente di raccolta, richiede sia una DLL che un CLSID COM per l'agente appropriato. L'agente potrebbe avere anche opzioni di configurazione aggiuntive, ovvero qualsiasi opzione specificata nel file di configurazione, formattata come JSON con caratteri di escape corretto.

## <a name="permissions"></a>Autorizzazioni

Per profilare un'applicazione che richiede autorizzazioni elevate, è necessario eseguire la profilatura da un prompt dei comandi con privilegi elevati.
