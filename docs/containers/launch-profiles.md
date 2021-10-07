---
title: Avviare un subset di Docker Compose servizio
description: Informazioni su come usare i Docker Compose di avvio e controllare quali servizi vengono avviati quando si Docker Compose in Visual Studio.
author: ghogen
manager: jmartens
ms.technology: vs-container-tools
ms.devlang: dotnet
ms.topic: how-to
ms.date: 05/10/2021
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: d91e58a554847fa5a713b120d2896c2e8120b2a8
ms.sourcegitcommit: ff81d69902e869b227d9ceb6e95023d1c63425b1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/06/2021
ms.locfileid: "129595144"
---
# <a name="launch-a-subset-of-compose-services"></a>Avviare un subset di servizi Compose

Se si dispone di un'applicazione costituita da più servizi e usa Docker Compose, è possibile configurare i servizi eseguiti ed eseguirne il debug creando o modificando un profilo di avvio esistente nelle impostazioni Docker Compose avvio. I profili di avvio consentono di eseguire dinamicamente solo i servizi importanti per lo scenario corrente. È possibile creare e selezionare tra i profili di avvio per personalizzare l'esperienza di debug e impostare azioni di avvio specifiche, ad esempio `Browser Launch URL` . Sarà anche possibile scegliere ogni servizio singolarmente o scegliendo un profilo Docker Compose, che esamina anche il file Compose per determinare il gruppo di servizi da eseguire.

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

Sono disponibili alcune opzioni per aprire la finestra di dialogo Docker Compose delle impostazioni di avvio:
- In Visual Studio scegliere **Debug** Gestisci Docker Compose  >  **Avvia Impostazioni**:

    ![Screenshot della voce di menu Impostazioni Compose](media/launch-settings/debug-dropdown-manage-compose.png)

- Fare clic con il pulsante destro del mouse Visual Studio progetto e scegliere Gestisci Docker Compose `docker-compose` **Avvia Impostazioni**

    ![Screenshot della voce del menu di scelta rapida](media/launch-settings/launch-settings-context-menu.png)

- Usare il Avvio veloce (**CTRL** Q ) e cercare Docker Compose trovare il comando di cui si + è fatto parte. 

Nell'esempio seguente è selezionato il profilo Compose, che filtra l'elenco Servizi in modo da visualizzare solo i tre dei `web1` cinque inclusi nel profilo: 

!["Screenshot della finestra di dialogo delle impostazioni di avvio"](media/launch-settings/launch-settings-create-profile.png)

>[!NOTE]
> La Docker Compose dei profili viene visualizzata solo se sono presenti profili definiti nei *file docker-compose.yml.*

Nell'esempio seguente viene illustrata la selezione tra singoli servizi anziché applicare filtri ai servizi in un profilo Compose. In questo esempio viene illustrato l'aspetto della finestra di dialogo se è stato creato un nuovo profilo di avvio denominato che avvia solo due dei cinque servizi, con debug `test2` `webapplication1` e senza `webapplication2` debug.  Questo profilo di avvio avvia anche un browser all'avvio dell'applicazione e lo apre al home page di `webapplication1` . 

![Screenshot della finestra di dialogo delle impostazioni di avvio con alcuni servizi deselezionati](media/launch-settings/launch-settings-selected.png)

Queste informazioni verranno salvate in *launchSettings.json* come illustrato di seguito

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

È anche possibile personalizzare ulteriormente i comportamenti di avvio creando Visual Studio profili di avvio che usano i profili Compose.

Per creare un altro profilo che usa il profilo Compose, selezionare Usa Docker Compose **profili e** scegliere `web1` . Il profilo di avvio include ora tre servizi: (che appartiene a entrambi i profili `webapplication1` `web` e `web1` Compose) `external1` e `external2` . Per impostazione predefinita, i servizi senza codice sorgente, ad esempio e , hanno `external1` l'azione predefinita Avvia senza eseguire il debug  `external2` **di**. Per impostazione predefinita, le applicazioni .NET con codice sorgente **avviano il debug.**

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

È anche possibile modificare l'azione di webapplication1 in **Avvia senza eseguire il debug di**. Le impostazioni in *launchSettings.json* sono simili al codice seguente:

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

Ecco una descrizione di ogni proprietà in *launchSettings.json:*

|Proprietà| Descrizione|
| - | - |
|Commandname| Nome del comando. Il valore predefinito è "DockerCompose"|
|commandVersion| Numero di versione usato per gestire lo schema del profilo di avvio DockerCompose.|
|composeProfile| Proprietà padre che definisce la definizione del profilo di avvio. Le proprietà figlio sono `includes` e `serviceActions`|
|composeProfile - include | Elenco dei nomi dei profili compose che costituiscono un profilo di avvio.|
|composeProfile - serviceActions | Elenca i profili compose selezionati, i servizi e l'azione di avvio di ogni servizio|
|serviceActions | Elenca i servizi selezionati e l'azione di avvio.|
|composeLaunchAction| Specifica l'azione di avvio da eseguire **su F5** o **CTRL** + **F5.** I valori consentiti sono None, LaunchBrowser e LaunchWCFTestClient.|
|composeLaunchUrl| URL da usare all'avvio del browser. I token di sostituzione validi sono "{ServiceIPAddress}", "{ServicePort}" e "{Scheme}". Ad esempio: {Scheme}://{ServiceIPAddress}:{ServicePort}|
|composeLaunchServiceName| Specifica il servizio usato per sostituire i token in composeLaunchUrl.|

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sul funzionamento di Strumenti contenitore, vedere panoramica Visual Studio di compilazione e debug di Strumenti [contenitore.](container-build.md)

## <a name="see-also"></a>Vedi anche

- [Visual Studio Impostazioni di avvio di Strumenti contenitore](container-launch-settings.md)

- [Docker Compose di compilazione](docker-compose-properties.md)
