---
title: Gestire i profili di avvio per Docker Compose progetto
description: Informazioni su come usare Docker Compose di avvio e controllare quali servizi vengono avviati quando si Docker Compose in Visual Studio.
author: ghogen
manager: jmartens
ms.technology: vs-container-tools
ms.devlang: dotnet
ms.topic: how-to
ms.date: 05/10/2021
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: 3b7872707c450c393c5bbeb654d65c0dbee60052
ms.sourcegitcommit: 8f8804b885c3a68f20bf0e9fe3729f2764145815
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2021
ms.locfileid: "123096953"
---
# <a name="launch-a-subset-of-compose-services"></a>Avviare un subset di servizi Compose

Se si dispone di un'applicazione costituita da più servizi e usa Docker Compose, è possibile configurare quali servizi vengono eseguiti ed eseguono il debug creando o modificando un profilo di avvio esistente nelle impostazioni di avvio Docker Compose di avvio. I profili di avvio consentono di eseguire dinamicamente solo i servizi importanti per lo scenario corrente. È possibile creare e selezionare tra i profili di avvio per personalizzare l'esperienza di debug e impostare azioni di avvio specifiche, ad esempio `Browser Launch URL` . Sarà anche possibile scegliere ogni servizio singolarmente o scegliendo un profilo Docker Compose, che esamina anche il file Compose per determinare il gruppo di servizi da eseguire.

Per informazioni sui Docker Compose, vedere [Uso dei profili con Compose.](https://docs.docker.com/compose/profiles/)
 
## <a name="prerequisites"></a>Prerequisiti

- [Visual Studio 2019 versione 16.10](https://visualstudio.microsoft.com/vs/) o successiva
- Una soluzione .NET con [l'orchestrazione dei contenitori con Docker Compose](tutorial-multicontainer.md)

## <a name="manage-launch-settings"></a>Gestire le impostazioni di avvio

Si consideri Docker Compose progetto in cui *docker-compose.yml* ha cinque servizi e tre profili Compose (web, web1 e web2).

```yml
version: '3.9'

services:
  webapplication1:
    image: ${DOCKER_REGISTRY-}webapplication1
    profiles: [web, web1]
    build:
      context: .
      dockerfile: WebApplication1/Dockerfile

  webapplication2:
    image: ${DOCKER_REGISTRY-}webapplication2
    profiles: [web, web2]
    build:
      context: .
      dockerfile: WebApplication2/Dockerfile

  webapplication3:
    image: ${DOCKER_REGISTRY-}webapplication3
    profiles: [web]
    build:
      context: .
      dockerfile: WebApplication3/Dockerfile

  external1:
    image: redis

  external2:
    image: redis

```

Sono disponibili alcune opzioni per aprire la finestra di dialogo Docker Compose impostazioni di avvio:
- In Visual Studio scegliere **Debug** Gestisci Docker Compose  >  **avvio Impostazioni**:

    ![Screenshot della voce di menu Debug Manage Compose Impostazioni menu](media/launch-settings/debug-dropdown-manage-compose.png)

- Fare clic con il pulsante destro del mouse Visual Studio progetto e scegliere Gestisci Docker Compose `docker-compose` **avvio Impostazioni**

    ![Screenshot della voce del menu di scelta rapida](media/launch-settings/launch-settings-context-menu.png)

- Usare il Avvio veloce (**CTRL** Q ) e cercare Docker Compose per trovare il comando di cui in + questo esempio. 

Nell'esempio seguente è selezionato il profilo Compose, che filtra l'elenco Servizi solo ai tre dei `web1` cinque inclusi in tale profilo: 

!["Screenshot della finestra di dialogo delle impostazioni di avvio"](media/launch-settings/launch-settings-create-profile.png)

La Docker Compose profili predefiniti viene visualizzata solo se sono presenti profili definiti nei *file docker-compose.yml.*

Nell'esempio seguente viene illustrata la selezione tra i singoli servizi anziché applicare filtri ai servizi in un profilo Compose. In questo caso viene illustrato l'aspetto della finestra di dialogo se è stato creato un nuovo profilo di avvio denominato che avvia solo due dei cinque servizi, con debug `test2` `webapplication1` e senza `webapplication2` debug.  Questo profilo di avvio avvia anche un browser all'avvio dell'applicazione e lo apre al home page di `webapplication1` . 

![Screenshot della finestra di dialogo delle impostazioni di avvio con alcuni servizi deselezionati](media/launch-settings/launch-settings-selected.png)

E queste informazioni verranno salvate inlaunchSettings.js *come* illustrato di seguito

```json
{
    "profiles": {
      "test2": {
        "commandName": "DockerCompose",
        "composeLaunchServiceName": "webapplication1",
        "serviceActions": {
          "external1": "DoNotStart",
          "external2": "DoNotStart",
          "webapplication1": "StartDebugging",
          "webapplication2": "StartWithoutDebugging",
          "webapplication3": "DoNotStart"
        },
        "composeLaunchAction": "LaunchBrowser",
        "commandVersion": "1.0",
        "composeLaunchUrl": "{Scheme}://localhost:{ServicePort}"
      }
   }
}
```

## <a name="create-a-launch-profile-that-uses-a-docker-compose-profile"></a>Creare un profilo di avvio che usa un Docker Compose di avvio

È anche possibile personalizzare ulteriormente i comportamenti di avvio creando Visual Studio di avvio che usano i profili Compose.

Per creare un altro profilo che usi il profilo Compose, selezionare **Usa Docker Compose e** scegliere `web1` . Il profilo di avvio include ora tre servizi , che appartengono a entrambi i profili e `webapplication1` `web` `web1` `external1` Compose, e `external2` . Per impostazione predefinita, i servizi senza codice sorgente, ad esempio `external1` e hanno  `external2` l'azione predefinita **Avvia senza eseguire il debug** di . Per impostazione predefinita, le applicazioni .NET con codice sorgente **avviano il debug.**

> [!IMPORTANT]
> Se un servizio non specifica un profilo Compose, verrà incluso in tutti i profili Compose in modo implicito.

![Screenshot della finestra di dialogo delle impostazioni di avvio con un altro profilo creato](media/launch-settings/launch-settings-create-profile.png)

Queste informazioni verranno salvate come illustrato nel codice seguente. La configurazione per il servizio e l'azione predefinita non vengono salvate a meno che non si modifica l'azione predefinita.

```json
{
  "profiles": {
    "test1": {
      "commandName": "DockerCompose",
      "composeProfile": {
         "includes": [
            "web1"
         ]
      },
      "commandVersion": "1.0"
    }
  }
}
```

È anche possibile modificare l'azione di webapplication1 in **Avvia senza eseguire il debug** di . Le impostazioni in *launchSettings.jsquindi* sono simili al codice seguente:

```json
{
  "profiles": {
    "test1": {
        "commandName": "DockerCompose",
        "composeProfile": {
          "includes": [
              "web1"
              ],
          "serviceActions": {
              "webapplication1": "StartWithoutDebugging"
          }
        },
    "commandVersion": "1.0"
    }
  }
}
```

## <a name="properties"></a>Proprietà

Ecco una descrizione di ogni proprietà nellalaunchSettings.js *in*:

|Proprietà| Descrizione|
| - | - |
|Commandname| Nome del comando. Il valore predefinito è "DockerCompose"|
|commandVersion| Numero di versione usato per gestire lo schema del profilo di avvio DockerCompose.|
|composeProfile| Proprietà padre che definisce la definizione del profilo di avvio. Le proprietà figlio sono `includes` e `serviceActions`|
|composeProfile - include | Elenco dei nomi dei profili compose che costituiscono un profilo di avvio.|
|composeProfile - serviceActions | Elenca i profili compose selezionati, i servizi e l'azione di avvio di ogni servizio|
|serviceActions | Elenca i servizi selezionati e l'azione di avvio.|
|composeLaunchServiceName| Se si specifica DockerLaunchAction o DockerLaunchBrowser, DockerServiceName è il nome del servizio da avviare. Usare questa proprietà per determinare quale servizio all'interno del file Docker Compose verrà avviato.|
|composeLaunchAction| Specifica l'azione di avvio da eseguire su **F5** o **CTRL** + **F5.** I valori consentiti sono None, LaunchBrowser e LaunchWCFTestClient.|
|composeLaunchUrl| URL da utilizzare all'avvio del browser. I token di sostituzione validi sono "{ServiceIPAddress}", "{ServicePort}" e "{Scheme}". Ad esempio: {Scheme}://{ServiceIPAddress}:{ServicePort}|

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sul funzionamento di Strumenti contenitore, vedere la Visual Studio di compilazione e debug di [Strumenti contenitori](container-build.md).

## <a name="see-also"></a>Vedi anche

- [Visual Studio Impostazioni di avvio di Strumenti contenitore](container-launch-settings.md)

- [Docker Compose di compilazione](docker-compose-properties.md)
