---
title: Eseguire il debug di app .NET in Linux con WSL 2
description: Informazioni su come eseguire ed eseguire il debug delle app .NET in WSL 2 senza uscire Visual Studio.
ms.date: 07/16/2021
ms.topic: conceptual
helpviewer_keywords:
- debugging, linux
- debugging, wsl2
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 41bd6cf6f45862702e282691467ce1ef26137b8e
ms.sourcegitcommit: 3c5b1a1d51b521356f42a6879c1f1745573dda65
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2021
ms.locfileid: "114591982"
---
# <a name="debug-net-apps-in-wsl-2-with-visual-studio"></a>Eseguire il debug di app .NET in WSL 2 con Visual Studio

È possibile eseguire ed eseguire facilmente il debug delle app .NET in Linux senza Visual Studio con WSL 2. Gli sviluppatori multipiattaforma possono usare questo metodo come modo semplice per testare più ambienti di destinazione.

Per un Windows .NET che ha come destinazione Linux, WSL 2 si trova in una posizione ideale tra il realistico della produzione e la produttività. In Visual Studio, è già possibile eseguire il debug in un ambiente Linux remoto usando il [debugger](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)remoto o con i contenitori usando [Gli strumenti contenitore](../containers/overview.md). Quando il realistico della produzione è il problema principale, è consigliabile usare una di queste opzioni. Quando un ciclo interno semplice e veloce è più importante, WSL 2 è un'ottima opzione.

Non è necessario scegliere un solo metodo. È possibile avere un profilo di avvio per Docker e WSL 2 nello stesso progetto e scegliere quale sia appropriato per una determinata esecuzione. Dopo aver distribuito l'app, è sempre possibile usare il debugger remoto per connettersi ad essa in caso di problemi.

## <a name="prerequisites"></a>Prerequisiti

- Visual Studio 2019 v16.9 Preview 1 o versioni successive con il componente facoltativo .NET Core Debugging con WSL 2.

  Il componente facoltativo è incluso per impostazione predefinita con i carichi di lavoro multipiattaforma .NET Core o ASP.NET e sviluppo Web. È necessario installare uno o entrambi questi carichi di lavoro.

- Installare [WSL 2.](/windows/wsl/about)

- Installare la [distribuzione](https://aka.ms/wslstore) desiderata.

## <a name="start-debugging-with-wsl-2"></a>Avviare il debug con WSL 2

1. Dopo aver installato i componenti necessari, aprire un'app Web ASP.NET Core o un'app console .NET Core in Visual Studio Verrà visualizzato un nuovo profilo di avvio denominato WSL 2:

   ![Profilo di avvio di WSL 2 nell'elenco dei profili di avvio](media/linux-wsl2-debugging-select-launch-profile.png)

1. Selezionare questo profilo per aggiungerlo allaunchSettings.js *in*.

   Alcuni degli attributi chiave nel file sono illustrati nell'esempio seguente.

    ```json
    "WSL 2": {
        "commandName": "WSL2",
        "launchBrowser": true,
        "launchUrl": "https://localhost:5001",
        "environmentVariables": {
            "ASPNETCORE_URLS": "https://localhost:5001;http://localhost:5000",
            "ASPNETCORE_ENVIRONMENT": "Development"
        },
        "distributionName": ""
    }
    ```

   Dopo aver selezionato il nuovo profilo, l'estensione verifica che la distribuzione WSL 2 sia configurata per l'esecuzione di app .NET e consente di installare eventuali dipendenze mancanti. Dopo aver installato queste dipendenze, è possibile eseguire il debug in WSL 2.

1. Avviare il debug come di consueto e l'app verrà eseguita nella distribuzione WSL 2 predefinita.

   Un modo semplice per verificare che sia in esecuzione in Linux è controllare il valore di `Environment.OSVersion` .

>[!NOTE]
> Sono stati testati e supportati solo Ubuntu e Debian. Le altre distribuzioni supportate da .NET dovrebbero funzionare, ma richiedono l'installazione manuale di [.NET Runtime](https://aka.ms/wsldotnet) e [Curl.](https://curl.haxx.se/)

## <a name="choose-a-specific-distribution"></a>Scegliere una distribuzione specifica

Per impostazione predefinita, il profilo di avvio di WSL 2 usa la distribuzione predefinita impostata in *wsl.exe*. Se si vuole che il profilo di avvio sia di destinazione di una distribuzione specifica, indipendentemente da tale impostazione predefinita, è possibile modificare il profilo di avvio. Ad esempio, se si esegue il debug di un'app Web e si vuole testarla in Ubuntu 20.04, il profilo di avvio sarà simile al seguente:

```json
"WSL 2": {
    "commandName": "WSL2",
    "launchBrowser": true,
    "launchUrl": "https://localhost:5001",
    "environmentVariables": {
        "ASPNETCORE_URLS": "https://localhost:5001;http://localhost:5000",
        "ASPNETCORE_ENVIRONMENT": "Development"
    },
    "distributionName": "Ubuntu-20.04"
}
```

## <a name="target-multiple-distributions"></a>Destinazione di più distribuzioni

Se si sta lavorando a un'applicazione che deve essere eseguita in più distribuzioni e si vuole un modo rapido per testare ognuna di esse, è possibile avere più profili di avvio. Ad esempio, se è necessario testare l'app console in Debian, Ubuntu 18.04 e Ubuntu 20.04, è possibile usare i profili di avvio seguenti:

```json
"WSL 2 : Debian": {
    "commandName": "WSL2",
    "distributionName": "Debian"
},
"WSL 2 : Ubuntu 18.04": {
    "commandName": "WSL2",
    "distributionName": "Ubuntu-18.04"
},
"WSL 2 : Ubuntu 20.04": {
    "commandName": "WSL2",
    "distributionName": "Ubuntu-20.04"
}
```

Con questi profili di avvio, è possibile passare facilmente da una distribuzione all'altra tra le distribuzioni di destinazione, senza lasciare la comodità di Visual Studio.

![Più profili di avvio WSL 2 nell'elenco dei profili di avvio](media/linux-wsl2-debugging-switch-target-distribution.png)

## <a name="wsl-settings-in-the-launch-profile"></a>Impostazioni WSL nel profilo di avvio

La tabella seguente illustra le impostazioni supportate nel profilo di avvio.

|Nome|Predefinito|Scopo|Supporta i token?|
|-|-|-|-|
|executablePath|dotnet|Eseguibile da eseguire|Sì|
|commandLineArgs|Valore della proprietà MSBuild targetPath mappata all'ambiente WSL|Argomenti della riga di comando passati a executablePath|Sì|
|Workingdirectory|Per le app console: {*OutDir*}</br>Per le app Web: {*ProjectDir*}|Directory di lavoro in cui avviare il debug|Sì|
|environmentVariables||Coppie chiave-valore delle variabili di ambiente da impostare per il processo di debug.|Sì|
|setupScriptPath||Script da eseguire prima del debug. Utile per l'esecuzione di script come ~/.bash_profile.|Sì|
|distributionName||Nome della distribuzione WSL da usare.|No|
|launchBrowser|false|Se avviare o meno un browser|No|
|launchUrl||URL da avviare se launchBrowser è true|No|

Token supportati:

{*ProjectDir*} - Percorso della directory del progetto

{*OutDir*} - Valore della proprietà MSBuild`OutDir`

>[!NOTE]
> Tutti i percorsi sono per WSL non Windows.
