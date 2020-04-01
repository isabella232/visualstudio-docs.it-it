---
title: Impostazioni di avvio di Visual Studio Container Tools
author: ghogen
description: Panoramica del processo di compilazione degli strumenti contenitore
ms.author: ghogen
ms.date: 08/15/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 63cf881fdedf9608d5cb773bbcb6b969a0f51624
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472651"
---
# <a name="container-tools-launch-settings"></a>Impostazioni di avvio degli strumenti contenitore

Nella cartella *Proprietà* di un progetto ASP.NET Core è possibile trovare il file launchSettings.json, che contiene le impostazioni che controllano la modalità di avvio dell'app Web nel computer di sviluppo. Per informazioni dettagliate sull'utilizzo di questo file nello sviluppo di ASP.NET, vedere [Usare più ambienti in ASP.NET Core](/aspnet/core/fundamentals/environments?view=aspnetcore-2.2). In *launchSettings.json*, le impostazioni nella sezione **Docker** sono correlate al modo in cui Visual Studio gestisce le app containerizzate.

::: moniker range="vs-2017"
```json
    "Docker": {
      "commandName": "Docker",
      "launchBrowser": true,
      "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}"
    }
```

::: moniker-end
::: moniker range=">=vs-2019"

```json
    "Docker": {
      "commandName": "Docker",
      "launchBrowser": true,
      "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}",
      "environmentVariables": {
        "ASPNETCORE_URLS": "https://+:443;http://+:80",
        "ASPNETCORE_HTTPS_PORT": "44360"
      },
      "httpPort": 51803,
      "useSSL": true,
      "sslPort": 44360
    }
```

::: moniker-end

L'impostazione commandName identifica che questa sezione si applica agli strumenti contenitore. Nella tabella seguente vengono illustrate le proprietà che è possibile impostare in questa sezione:The following table shows the properties that can be set in this section:

::: moniker range="vs-2017"

|Nome impostazione|Versione|Esempio|Descrizione|
|------------|-------|-------|---------------|
|launchBrowser (browser di avvio)|Visual Studio 2017|"launchBrowser": true|Indica se avviare il browser dopo aver avviato correttamente il progetto.|
|LaunchUrl (url di avvio)|Visual Studio 2017|"launchUrl": ""Programma""ServiceHost": "ServicePort""|Questo URL viene utilizzato quando si avvia il browser.  I token di sostituzione supportati per questa stringa sono:Supported replacement tokens for this string are:<br>   "Scheme" - Sostituito con "http" o "https" a seconda che venga utilizzato SSL.<br>   -ServiceHost - In genere sostituito con "localhost". Quando si prendono di mira i contenitori di Windows in Windows 10 RS3 o versioni precedenti, tuttavia, viene sostituito con l'IP del contenitore.<br>   - In genere sostituito con sslPort o httpPort, a seconda che venga utilizzato SSL.  Quando scegli come target i contenitori di Windows in Windows 10 RS3 o versioni precedenti, tuttavia, viene sostituito con "443" o "80", a seconda che venga utilizzato SSL.|

::: moniker-end

::: moniker range=">=vs-2019"

| Nome impostazione         | Esempio                                               | Descrizione                                                                                                             |
| -------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| comandoLineArgs      | "commandLineArgs": "--mysetting myvalue"              | Questi argomenti della riga di comando per l'avvio dell'app vengono usati quando si avvia il progetto nel contenitore.                                     |
| environmentVariables | "variabiliambiente":                             | Questi valori delle variabili di ambiente vengono passati al processo quando viene avviato nel contenitore.                       |
|                      | "ASPNETCORE_URLS":https://+:443" ; http://+:80",       |                                                                                                                         |
|                      | "ASPNETCORE_HTTPS_PORT": "44381"                      |                                                                                                                         |
|                      | }                                                     |                                                                                                                         |
| HttpPorta (informazioni in stato ine             | "httpPort": 24051                                     | Questa porta nell'host è mappata alla porta 80 del contenitore quando si avvia il contenitore.                                |
|                      |                                                       | Se non specificato, il valore viene ricavato dal valore iisSettings.                                                          |
| launchBrowser (browser di avvio)        | "launchBrowser": true                                 | Indica se avviare il browser dopo aver avviato correttamente il progetto.                                       |
| LaunchUrl (url di avvio)            | "launchUrl": ""Programma""ServiceHost": "ServicePort"" | Questo URL viene utilizzato quando si avvia il browser. I token di sostituzione supportati per questa stringa sono:Supported replacement tokens for this string are:                          |
|                      |                                                       | - "Scheme" - Sostituito con "http" o "https" a seconda che venga utilizzato SSL.                                   |
|                      |                                                       | - "ServiceHost" - In genere sostituito con "localhost".                                                                    |
|                      |                                                       | Quando si prendono di mira i contenitori di Windows in Windows 10 RS3 o versioni precedenti, tuttavia, viene sostituito con l'IP del contenitore.           |
|                      |                                                       | - - In genere sostituito con sslPort o httpPort, a seconda che venga utilizzato SSL.                   |
|                      |                                                       | Quando si indirizzano i contenitori di Windows in Windows 10 RS3 o versioni precedenti, tuttavia, viene sostituito con "443" o "80",         |
|                      |                                                       | a seconda che venga utilizzato SSL.                                                                                       |
| sslPorta              | "sslPort": 44381                                      | Questa porta nell'host è mappata alla porta 443 del contenitore all'avvio del contenitore.                               |
|                      |                                                       | Se non specificato, il valore viene ricavato dal valore iisSettings.                                                          |
| useSSL               | "useSSL": true                                        | Indica se utilizzare SSL all'avvio del progetto. Se useSSL non è specificato, viene utilizzato SSL quando sslPort > 0. |

::: moniker-end

## <a name="next-steps"></a>Passaggi successivi

Configurare il progetto impostando le proprietà di [compilazione degli strumenti contenitore](container-msbuild-properties.md).

## <a name="see-also"></a>Vedere anche

[Docker Compose proprietà di compilazione](docker-compose-properties.md)
