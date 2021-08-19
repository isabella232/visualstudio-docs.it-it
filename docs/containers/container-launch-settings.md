---
title: Visual Studio Impostazioni di avvio di Strumenti contenitore
author: ghogen
description: Informazioni sulle impostazioni di avvio per Strumenti contenitore correlate al modo in cui Visual Studio le app in contenitori.
ms.author: ghogen
ms.date: 08/15/2019
ms.technology: vs-container-tools
ms.topic: reference
ms.openlocfilehash: d05d4a42a6e2433cc9dfc5190a9e380dda49dab0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122122059"
---
# <a name="container-tools-launch-settings"></a>Impostazioni di avvio di Strumenti contenitore

Nella cartella *Proprietà* di un progetto ASP.NET Core è possibile trovare il launchSettings.jsnel file , che contiene le impostazioni che controllano la modalità di avvio dell'app Web nel computer di sviluppo. Per informazioni dettagliate sull'uso di questo file ASP.NET sviluppo, vedere Usare più [ambienti in ASP.NET Core](/aspnet/core/fundamentals/environments?view=aspnetcore-2.2&preserve-view=true). In *launchSettings.jsin*, le impostazioni nella sezione **Docker** sono correlate al modo in cui Visual Studio le app in contenitori.

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

L'impostazione commandName indica che questa sezione si applica a Strumenti contenitore. La tabella seguente illustra le proprietà che è possibile impostare in questa sezione:

::: moniker range="vs-2017"

|Nome impostazione|Versione|Esempio|Descrizione|
|------------|-------|-------|---------------|
|launchBrowser|Visual Studio 2017|"launchBrowser": true|Indica se avviare il browser dopo aver avviato correttamente il progetto.|
|launchUrl|Visual Studio 2017|"launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}"|Questo URL viene usato all'avvio del browser.  I token di sostituzione supportati per questa stringa sono:<br>   {Scheme} - Sostituito con "http" o "https" a seconda che ssl sia o meno usato.<br>   {ServiceHost}: in genere sostituito con "localhost". Quando la destinazione Windows contenitori in Windows 10 RS3 o versioni precedenti, tuttavia, viene sostituita con l'indirizzo IP del contenitore.<br>   {ServicePort}: in genere sostituito con sslPort o httpPort, a seconda che ssl sia usato o meno.  Quando la destinazione è Windows contenitori in Windows 10 RS3 o versioni precedenti, tuttavia, viene sostituita con "443" o "80", a seconda che ssl sia o meno usato.|

::: moniker-end

::: moniker range=">=vs-2019"

| Nome impostazione         | Esempio                                               | Descrizione                                                                                                             |
| -------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| CommandLineArgs      | "commandLineArgs": "--mysetting myvalue"              | Questi argomenti della riga di comando per avviare l'app vengono usati quando si avvia il progetto nel contenitore.                                     |
| environmentVariables | "environmentVariables": {                             | Questi valori delle variabili di ambiente vengono passati al processo quando viene avviato nel contenitore.                       |
|                      | "ASPNETCORE_URLS": " https://+:443 ; http://+:80 ",       |                                                                                                                         |
|                      | "ASPNETCORE_HTTPS_PORT": "44381"                      |                                                                                                                         |
|                      | }                                                     |                                                                                                                         |
| httpPort             | "httpPort": 24051                                     | Questa porta nell'host viene mappata alla porta 80 del contenitore all'avvio del contenitore.                                |
|                      |                                                       | Se non specificato, il valore viene preso dal valore iisSettings.                                                          |
| launchBrowser        | "launchBrowser": true                                 | Indica se avviare il browser dopo aver avviato correttamente il progetto.                                       |
| launchUrl            | "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}" | Questo URL viene usato all'avvio del browser. I token di sostituzione supportati per questa stringa sono:                          |
|                      |                                                       | - {Scheme} - Sostituito con "http" o "https" a seconda che ssl sia o meno usato.                                   |
|                      |                                                       | - {ServiceHost} - In genere sostituito con "localhost".                                                                    |
|                      |                                                       | Quando la destinazione Windows contenitori in Windows 10 RS3 o versioni precedenti, tuttavia, viene sostituita con l'indirizzo IP del contenitore.           |
|                      |                                                       | - {ServicePort} - In genere sostituito con sslPort o httpPort, a seconda che ssl sia usato o meno.                   |
|                      |                                                       | Quando la destinazione Windows contenitori in Windows 10 RS3 o versioni precedenti, tuttavia, viene sostituita con "443" o "80",         |
|                      |                                                       | a seconda che ssl sia o meno utilizzato.                                                                                       |
| sslPort              | "sslPort": 44381                                      | Questa porta nell'host viene mappata alla porta 443 del contenitore all'avvio del contenitore.                               |
|                      |                                                       | Se non specificato, il valore viene preso dal valore iisSettings.                                                          |
| useSSL               | "useSSL": true                                        | Indica se usare SSL all'avvio del progetto. Se useSSL non è specificato, viene usato SSL quando sslPort > 0. |

::: moniker-end

## <a name="next-steps"></a>Passaggi successivi

Configurare il progetto impostando le proprietà [di compilazione di Strumenti contenitore](container-msbuild-properties.md).

## <a name="see-also"></a>Vedi anche

- [Docker Compose proprietà di compilazione](docker-compose-properties.md)
- [Gestire i profili di avvio per Docker Compose](launch-profiles.md)
