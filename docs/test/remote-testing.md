---
title: Test remoti in Visual Studio
description: Informazioni su come usare i test remoti Visual Studio Esplora test per eseguire test da ambienti remoti, inclusi contenitori, WSL2 o connessioni SSH. Questo argomento illustra come configurare i test remoti con un testenvironments.jssu per contenitori locali, connessioni WSL2 o SSH.
ms.date: 08/26/2021
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
monikerRange: '>= vs-2022'
ms.workload:
- multiple
ms.openlocfilehash: ff31dd7e6f5b45c316e3cd094a2728b085180e0b
ms.sourcegitcommit: f4e975cb5755b4a3ff207f9bde74e79f6db5c643
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/01/2021
ms.locfileid: "123361126"
---
# <a name="remote-testing-experimental-preview"></a>Test remoto (anteprima sperimentale)

Il test remoto consente agli sviluppatori di connettersi Visual Studio 2022 ad ambienti remoti per l'esecuzione e il debug di test. Questa funzionalità è utile per gli sviluppatori multipiattaforma che distribuiscono codice in più ambienti di destinazione diversi, ad esempio sistemi operativi Windows o Linux. In genere, ad esempio, uno sviluppatore deve eseguire il push delle modifiche a una pipeline CI per ottenere commenti e suggerimenti da un test in esecuzione in Linux. Con questa funzionalità è possibile eseguire test Linux direttamente Visual Studio connettendo Esplora test a un ambiente remoto.

Requisiti per l'uso di questa versione sperimentale del test remoto:
* Visual Studio 2022 Update 17.0 Preview 3 o versione successiva
* Disponibile solo per i test .NET.
  * Se si è interessati al supporto dei test remoti per altre lingue, determinare un [suggerimento](/visualstudio/ide/suggest-a-feature) o determinare un suggerimento esistente. [Supporto dei test remoti C++.](https://developercommunity.visualstudio.com/t/run-c-unit-tests-on-linux-with-visual-studio/1403357)
* Attualmente, la maggior parte del provisioning dell'ambiente viene lasciata alla specifica dell'utente. L'utente deve installare le dipendenze necessarie nell'ambiente di destinazione. Ad esempio, se i test hanno come destinazione .NET 5.0, è necessario assicurarsi che nel contenitore sia installato .NET 5.0 tramite Dockerfile. Potrebbe essere richiesto di installare .NET Core nell'ambiente remoto, necessario per eseguire e individuare i test in modalità remota. 
* Pianificare il monitoraggio dello stato della connessione all'ambiente remoto usando il riquadro Test > output. Ad esempio, se il contenitore è stato arrestato, verrà visualizzato un messaggio nel riquadro Output > Test. È possibile che non si rilevino tutti gli scenari, quindi pianificare di controllare l'output se sembra che la connessione sia stata persa. In particolare, se il riquadro Output non è impostato su "Test", è possibile che il messaggio non venga visualizzato immediatamente. Se la connessione viene persa, è possibile usare l'elenco a discesa dell'ambiente in Esplora test per impostare di nuovo la connessione all'ambiente locale e quindi selezionare di nuovo l'ambiente remoto per reinizialzzarla.

## <a name="set-up-the-remote-testing-environment"></a>Configurare l'ambiente di test remoto

Gli ambienti vengono `testenvironments.json` specificati usando nella radice della soluzione. La struttura del file JSON segue lo schema descritto di seguito:
```json
{
    "version": "1", // value must be 1
    "environments": [
        { "name": "<unique name>", ... },
        ...
    ]
}
```

### <a name="local-container-connections"></a>Connessioni al contenitore locale

Per connettersi a un contenitore in esecuzione in locale, è necessario [avere Docker Desktop](https://www.docker.com/products/docker-desktop) nel computer locale. Facoltativamente, abilitare [l'integrazione WSL2](/windows/wsl/install-win10) per prestazioni migliori.

Per un Dockerfile, l'ambiente può essere `testEnvironments.json` specificato in nella radice della soluzione. Usa le proprietà descritte qui.
```json
    {
    "name": "<name>",
    "localRoot": "<path to local environment>", // optional
    "type": "docker",
    "dockerImage": "<docker image tag>",
    }
```

L'esempio seguente illustra `testenvironments.json` per un'immagine del contenitore locale denominata \<mcr.microsoft.com/dotnet/core/sdk\> .
```json
{
"version": "1",
"environments": [
    {
    "name": "linux dotnet-core-sdk-3.1",
    "type": "docker",
    "dockerImage": "mcr.microsoft.com/dotnet/core/sdk"
    }
]
}
```

L'esempio seguente mostra un Dockerfile per l'esecuzione di test che hanno come destinazione .NET 5.0. La seconda riga garantisce che il debugger possa connettersi ed eseguire nel contenitore.
```
FROM mcr.microsoft.com/dotnet/core/sdk:5.0

RUN wget https://aka.ms/getvsdbgsh && \
    sh getvsdbgsh -v latest  -l /vsdbg
```

Il contenitore deve avere un'immagine compilata nel computer locale. È possibile compilare un contenitore usando il comando seguente (incluso "." alla fine): `docker build -t <docker image name> -f <path to Dockerfile> .`

### <a name="local-wsl2-connections"></a>Connessioni WSL2 locali
Per eseguire test in modalità remota in WSL2, è necessario abilitare [l'integrazione WSL2](/windows/wsl/install-win10) nel computer locale.

L'ambiente può essere specificato nella radice della soluzione usando lo schema seguente e sostituendo con la distribuzione `testEnvironments.json` \<Ubuntu\> WSL2 installata.
```json
{
"version": "1",
"environments": [
    {
    "name": "WSL-Ubuntu",
    "type": "wsl",
    "wslDistribution": "Ubuntu"
    }
]
}
```

### <a name="ssh-connections"></a>Connessioni SSH
 È possibile aggiungere o rimuovere connessioni SSH in Strumenti **> opzioni > multipiattaforma > Gestione connessioni**. Selezionando "Aggiungi" sarà possibile immettere il nome host, la porta e le credenziali necessarie.

L'ambiente può essere specificato in nella radice della soluzione usando lo schema seguente e sostituendo `testEnvironments.json` `\<ssh://user@hostname:22\>` con remoteUri SSH.
```json
{
"version": "1",
"environments": [
    {
    "name": "ssh-remote",
    "type": "ssh",
    "remoteUri": "ssh://user@hostname:22"
    }
]
}
```

## <a name="use-the-test-explorer-to-run-and-debug-remote-tests"></a>Usare Esplora test per eseguire ed eseguire il debug di test remoti
* L'ambiente attivo viene selezionato tramite un elenco a discesa nella barra degli strumenti di Esplora test. Attualmente, può essere attivo un solo ambiente di test alla volta.

  ![Elenco a discesa ambiente di test remoto in Esplora test](media/remote_test_drop_down.png)

* Dopo aver selezionato un ambiente, i test vengono individuati ed eseguiti nel nuovo ambiente.

  ![I test vengono individuati ed eseguiti in ambienti remoti](media/remote_test_linux_discovery.png)

* È ora possibile eseguire i test all'interno del remoto ed eseguire il debug dei test in ambienti .

  ![Visualizzare i risultati dei test dall'ambiente remoto in Esplora test](media/remote_test_linux_passing.png)

* Esplora test potrebbe richiedere di installare alcuni prerequisiti di ambiente mancanti e provare a installare le dipendenze mancanti. Tuttavia, la maggior parte del provisioning dell'ambiente remoto è in base alle specifiche dell'utente.

## <a name="see-also"></a>Vedi anche

- [Eseguire il debug di unit test con Esplora test](../test/debug-unit-tests-with-test-explorer.md)
- [Eseguire uno unit test come processo a 64 bit](../test/run-a-unit-test-as-a-64-bit-process.md)
- [Domande frequenti su Esplora test](test-explorer-faq.md)
