---
title: Eseguire il debug di app .NET Core in WSL 2
description: Informazioni su come eseguire ed eseguire il debug delle app .NET Core in WSL 2 senza uscire da Visual Studio.
ms.date: 01/25/2021
ms.topic: conceptual
helpviewer_keywords:
- debugging, linux
- debugging, wsl2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 736987a02ca7e2f59ce689b8402d9a6fcd7407e9
ms.sourcegitcommit: 586369f5aa61d4a0330802f718f0ceaa55d7e9c7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2021
ms.locfileid: "99227655"
---
# <a name="debug-net-core-apps-in-wsl-2-with-visual-studio"></a>Eseguire il debug di app .NET Core in WSL 2 con Visual Studio

È possibile eseguire facilmente ed eseguire il debug delle app .NET Core in Linux senza uscire da Visual Studio con WSL 2. Se si è uno sviluppatore multipiattaforma, è possibile usare questo metodo come un modo semplice per testare più ambienti di destinazione.

Per gli utenti di Windows .NET che hanno come destinazione Linux, WSL 2 si trova in un luogo molto bello tra il realismo di produzione e la produttività. In Visual Studio è già possibile eseguire il debug in un ambiente Linux remoto usando il [debugger remoto](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)o con i contenitori usando gli [strumenti contenitore](../containers/overview.md). Quando il realismo di produzione è la preoccupazione principale, è consigliabile usare una di queste opzioni. Quando un ciclo interno semplice e veloce è più importante, WSL 2 è un'ottima opzione.

Non è necessario scegliere un solo metodo. È possibile avere un profilo di avvio per Docker e WSL 2 nello stesso progetto e scegliere qualunque sia il più appropriato per una determinata esecuzione. Quando l'app viene distribuita, è sempre possibile usare il debugger remoto per collegarsi a questo se si verifica un problema.

## <a name="prerequisites"></a>Prerequisiti

- Visual Studio 2019 v 16,9 Preview 1 o versioni successive con il debug .NET Core con il componente facoltativo WSL 2.

  Il componente facoltativo è incluso per impostazione predefinita con i carichi di lavoro multipiattaforma di .NET Core o ASP.NET e sviluppo Web. È necessario installare uno o entrambi i carichi di lavoro.

- Installare [WSL 2](/windows/wsl/about).

- Installare la [distribuzione](https://aka.ms/wslstore) di propria scelta.

## <a name="start-debugging-with-wsl-2"></a>Avviare il debug con WSL 2

1. Dopo aver installato i componenti necessari, aprire un'app Web ASP.NET Core o un'app console .NET Core in Visual Studio. verrà visualizzato un nuovo profilo di avvio denominato WSL 2:

   ![Profilo di avvio WSL 2 nell'elenco Profilo di avvio](media/linux-wsl2-debugging-select-launch-profile.png)

1. Selezionare questo profilo per aggiungerlo all' *launchSettings.js*.

   Nell'esempio seguente vengono illustrati alcuni degli attributi chiave del file.

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

   Dopo aver selezionato il nuovo profilo, l'estensione verifica che la distribuzione di WSL 2 sia configurata per l'esecuzione di app .NET Core e consente di installare tutte le dipendenze mancanti. Dopo aver installato queste dipendenze, è possibile eseguire il debug in WSL 2.

1. Avviare il debug come di consueto e l'app viene eseguita nella distribuzione predefinita di WSL 2.

   Un modo semplice per verificare che sia in esecuzione in Linux consiste nel controllare il valore di `Environment.OSVersion` .

>[!NOTE]
> Solo Ubuntu e Debian sono stati testati e sono supportati. Altre distribuzioni supportate da .NET Core dovrebbero funzionare, ma richiedono l'installazione manuale del [runtime di .NET Core](https://aka.ms/wsldotnet) e [curl](https://curl.haxx.se/).

## <a name="choose-a-specific-distribution"></a>Scegliere una distribuzione specifica

Per impostazione predefinita, il profilo di avvio WSL 2 usa la distribuzione predefinita impostata in *wsl.exe*. Se si vuole che il profilo di avvio abbia come destinazione una distribuzione specifica, indipendentemente da tale impostazione predefinita, è possibile modificare il profilo di avvio. Ad esempio, se si sta eseguendo il debug di un'app Web e si vuole testarla in Ubuntu 20,04, il profilo di avvio sarà simile al seguente:

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

## <a name="target-multiple-distributions"></a>Più distribuzioni di destinazione

Se si sta lavorando su un'applicazione che deve essere eseguita in più distribuzioni e si desidera un modo rapido per testarli, è possibile avere più profili di avvio. Ad esempio, se è necessario testare l'app console in Debian, Ubuntu 18,04 e Ubuntu 20,04, è possibile usare i seguenti profili di avvio:

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

Con questi profili di avvio, è possibile spostarsi facilmente tra le distribuzioni di destinazione, senza abbandonare la comodità di Visual Studio.

![Più profili di avvio WSL 2 nell'elenco Profilo di avvio](media/linux-wsl2-debugging-switch-target-distribution.png)

## <a name="wsl-settings-in-the-launch-profile"></a>Impostazioni WSL nel profilo di avvio

La tabella seguente illustra le impostazioni supportate nel profilo di avvio.

|Nome|Predefinito|Scopo|Supporta i token?|
|-|-|-|-|
|executablePath|dotnet|Eseguibile da eseguire|Sì|
|commandLineArgs|Il valore della proprietà MSBuild TargetPath mappato all'ambiente WSL|Argomenti della riga di comando passati a executablePath|Sì|
|workingDirectory|Per le app console: {*OutDir*}</br>Per le app Web: {*ProjectDir*}|Directory di lavoro in cui avviare il debug|Sì|
|environmentVariables||Coppie chiave-valore delle variabili di ambiente da impostare per il processo sottoposto a debug.|Sì|
|Percorsoscriptdiinstallazione||Script da eseguire prima del debug. Utile per l'esecuzione di script come ~/.bash_profile.|Sì|
|DistributionName||Nome della distribuzione di WSL da usare.|No|
|launchBrowser|false|Indica se avviare o meno un browser|No|
|launchUrl||URL da avviare se launchBrowser è true|No|

Token supportati:

{*ProjectDir*}: il percorso della directory del progetto

{*OutDir*}: valore della proprietà MSBuild `OutDir`

>[!NOTE]
> Tutti i percorsi sono per WSL non per Windows.
