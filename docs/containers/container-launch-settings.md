---
title: Impostazioni di avvio degli strumenti contenitore di Visual Studio
author: ghogen
description: Panoramica del processo di compilazione degli strumenti contenitore
ms.author: ghogen
ms.date: 08/15/2019
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: de0e3cc4e563f7082b91b904a110996cdb85b3b4
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/15/2020
ms.locfileid: "88247977"
---
# <a name="container-tools-launch-settings"></a>Impostazioni di avvio degli strumenti contenitore

Nella cartella *Properties* di un progetto ASP.NET Core è possibile trovare il launchSettings.jssu file, che contiene le impostazioni che controllano la modalità di avvio dell'app Web nel computer di sviluppo. Per informazioni dettagliate sul modo in cui questo file viene usato nello sviluppo ASP.NET, vedere [usare più ambienti in ASP.NET Core](/aspnet/core/fundamentals/environments?view=aspnetcore-2.2). In *launchSettings.json*, le impostazioni nella sezione **Docker** sono correlate al modo in cui Visual Studio gestisce le app in contenitori.

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

L'impostazione CommandName indica che questa sezione si applica agli strumenti contenitore. La tabella seguente illustra le proprietà che è possibile impostare in questa sezione:

::: moniker range="vs-2017"

|Nome impostazione|Versione|Esempio|Descrizione|
|------------|-------|-------|---------------|
|launchBrowser|Visual Studio 2017|"launchBrowser": true|Indica se avviare il browser dopo aver avviato correttamente il progetto.|
|launchUrl|Visual Studio 2017|"launchUrl": "{Scheme}://{ServiceHost}: {ServicePort}"|Questo URL viene usato quando si avvia il browser.  I token di sostituzione supportati per questa stringa sono:<br>   {Scheme}: sostituito con "http" o "https" a seconda che si stia usando SSL.<br>   {ServiceHost}-generalmente sostituito con "localhost". Quando si fa riferimento a contenitori Windows in Windows 10 RS3 o versioni precedenti, tuttavia, viene sostituito con l'IP del contenitore.<br>   {ServicePort}: in genere sostituito con sslPort o httpPort, a seconda che venga usato SSL.  Quando si fa riferimento a contenitori di Windows in Windows 10 RS3 o versioni precedenti, tuttavia, viene sostituito con "443" o "80", a seconda che venga usato SSL.|

::: moniker-end

::: moniker range=">=vs-2019"

| Nome impostazione         | Esempio                                               | Descrizione                                                                                                             |
| -------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| commandLineArgs      | "commandLineArgs": "--impostazione di SetValue"              | Questi argomenti della riga di comando per l'avvio dell'app vengono usati quando si avvia il progetto nel contenitore.                                     |
| environmentVariables | "environmentVariables": {                             | Questi valori delle variabili di ambiente vengono passati al processo quando viene avviato nel contenitore.                       |
|                      | "ASPNETCORE_URLS": " https://+:443 ; http://+:80 ",       |                                                                                                                         |
|                      | "ASPNETCORE_HTTPS_PORT": "44381"                      |                                                                                                                         |
|                      | }                                                     |                                                                                                                         |
| httpPort             | "httpPort": 24051                                     | Questa porta sull'host viene mappata alla porta 80 del contenitore all'avvio del contenitore.                                |
|                      |                                                       | Se non è specificato, il valore viene ricavato dal valore iisSettings.                                                          |
| launchBrowser        | "launchBrowser": true                                 | Indica se avviare il browser dopo aver avviato correttamente il progetto.                                       |
| launchUrl            | "launchUrl": "{Scheme}://{ServiceHost}: {ServicePort}" | Questo URL viene usato quando si avvia il browser. I token di sostituzione supportati per questa stringa sono:                          |
|                      |                                                       | -{Scheme}-sostituito con "http" o "https" a seconda che si stia usando SSL.                                   |
|                      |                                                       | -{ServiceHost}-generalmente sostituito con "localhost".                                                                    |
|                      |                                                       | Quando si fa riferimento a contenitori Windows in Windows 10 RS3 o versioni precedenti, tuttavia, viene sostituito con l'IP del contenitore.           |
|                      |                                                       | -{ServicePort}-generalmente sostituito con sslPort o httpPort, a seconda che venga usato SSL.                   |
|                      |                                                       | Quando si fa riferimento a contenitori di Windows in Windows 10 RS3 o versioni precedenti, tuttavia, viene sostituito con "443" o "80",         |
|                      |                                                       | a seconda se viene utilizzato SSL.                                                                                       |
| sslPort              | "sslPort": 44381                                      | Questa porta sull'host viene mappata alla porta 443 del contenitore all'avvio del contenitore.                               |
|                      |                                                       | Se non è specificato, il valore viene ricavato dal valore iisSettings.                                                          |
| useSSL               | "useSSL": true                                        | Indica se utilizzare SSL all'avvio del progetto. Se useSSL non è specificato, viene usato SSL quando sslPort > 0. |

::: moniker-end

## <a name="next-steps"></a>Passaggi successivi

Configurare il progetto impostando le [proprietà di compilazione degli strumenti contenitore](container-msbuild-properties.md).

## <a name="see-also"></a>Vedere anche

[Proprietà di compilazione Docker Compose](docker-compose-properties.md)
