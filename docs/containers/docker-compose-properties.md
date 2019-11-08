---
title: Strumenti contenitore di Visual Studio Docker Compose impostazioni di compilazione
author: ghogen
description: Panoramica del processo di compilazione degli strumenti contenitore
ms.author: ghogen
ms.date: 08/12/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 4ea1a936de215340cc13971e7a70a8d795d36cbb
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73713926"
---
# <a name="docker-compose-build-properties"></a>Proprietà di compilazione Docker Compose

Oltre alle proprietà che controllano singoli progetti Docker, descritti in [strumenti contenitore proprietà di compilazione](container-msbuild-properties.md), è anche possibile personalizzare il modo in cui Visual Studio compila i progetti di Docker compose impostando le proprietà Docker compose che MSBuild USA per compilare la soluzione. È anche possibile controllare il modo in cui il debugger di Visual Studio esegue le app Docker Compose impostando le etichette dei file nei file di configurazione Docker Compose.

## <a name="how-to-set-the-msbuild-properties"></a>Come impostare le proprietà di MSBuild

Per impostare il valore di una proprietà, modificare il file di progetto. Per Docker Compose proprietà, questo file di progetto è quello con estensione dcproj, salvo diversa indicazione nella tabella nella sezione successiva. Si supponga, ad esempio, di voler specificare di avviare il browser all'avvio del debug. È possibile impostare la proprietà `DockerLaunchAction` nel file di progetto con estensione dcproj, come indicato di seguito.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

È possibile aggiungere l'impostazione della proprietà a un elemento `PropertyGroup` esistente o, se non ne esiste uno, creare un nuovo elemento `PropertyGroup`.

## <a name="docker-compose-msbuild-properties"></a>Proprietà di Docker Compose MSBuild

Nella tabella seguente vengono illustrate le proprietà MSBuild disponibili per i progetti Docker Compose.

| Nome della proprietà | Percorso | Descrizione | Valore predefinito  |
|---------------|----------|-------------|----------------|
|AdditionalComposeFiles|dcproj|Specifica i file di composizione aggiuntivi in un elenco delimitato da punti e virgola da inviare a Docker-compose. exe per tutti i comandi. Sono consentiti percorsi relativi dal file di progetto Docker-compose (dcproj).|-|
|DockerComposeBaseFilePath|dcproj|Specifica la prima parte dei nomi file dei file Docker-compose, senza l'estensione *yml* . Esempio: <br>1. DockerComposeBaseFilePath = null/undefined: usare il percorso del file di base *Docker-compose*e i file verranno denominati *Docker-compose. yml* e *Docker-compose. override. yml*<br>2. DockerComposeBaseFilePath = *mydockercompose*: i file verranno denominati *mydockercompose. yml* e *mydockercompose. override. yml*<br> 3. DockerComposeBaseFilePath = *.. \mydockercompose*: i file saranno di un livello superiore. |Docker-compose|
|DockerComposeBuildArguments|dcproj|Specifica i parametri aggiuntivi da passare al comando `docker-compose build`. Ad esempio, `--parallel --pull`. |
|DockerComposeDownArguments|dcproj|Specifica i parametri aggiuntivi da passare al comando `docker-compose down`. Ad esempio, `--timeout 500`.|-|  
|DockerComposeProjectPath|csproj o vbproj|Percorso relativo del file del progetto Docker-compose (dcproj). Impostare questa proprietà quando si pubblica il progetto di servizio per trovare le impostazioni di compilazione dell'immagine associate archiviate nel file Docker-compose. yml.|-|
|DockerComposeUpArguments|dcproj|Specifica i parametri aggiuntivi da passare al comando `docker-compose up`. Ad esempio, `--timeout 500`.|-|
|DockerLaunchAction| dcproj | Specifica l'azione di avvio da eseguire in F5 o CTRL + F5.  I valori consentiti sono None, LaunchBrowser e LaunchWCFTestClient|Nessuno|
|DockerLaunchBrowser| dcproj | Indica se avviare il browser. Viene ignorato se viene specificato DockerLaunchAction. | False |
|DockerServiceName| dcproj|Se vengono specificati DockerLaunchAction o DockerLaunchBrowser, DockerServiceName è il nome del servizio che deve essere avviato.  Usare questa proprietà per determinare il numero potenzialmente elevato di progetti a cui può fare riferimento un file Docker-compose.|-|
|DockerServiceUrl| dcproj | URL da utilizzare all'avvio del browser.  I token di sostituzione validi sono "{ServiceIPAddress}", "{ServicePort}" e "{Scheme}".  Ad esempio: {Scheme}://{ServiceIPAddress}: {ServicePort}|-|
|DockerTargetOS| dcproj | Sistema operativo di destinazione usato durante la compilazione dell'immagine docker.|-|

> [!NOTE]
> DockerComposeBuildArguments, DockerComposeDownArguments e DockerComposeUpArguments sono una novità di Visual Studio 2019 versione 16,3.

## <a name="docker-compose-file-labels"></a>Etichette file Docker Compose

È anche possibile eseguire l'override di determinate impostazioni inserendo un file denominato *Docker-compose. vs. debug. yml* (per la configurazione di **debug** ) o *Docker-compose. vs. Release. yml* (per la configurazione della **versione** ) nella stessa directory *del file Docker-compose. yml* .  In questo file è possibile specificare le impostazioni come segue:

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

Utilizzare le virgolette doppie intorno ai valori, come nell'esempio precedente, e utilizzare la barra rovesciata come carattere di escape per le barre rovesciate nei percorsi.

|Nome etichetta|Descrizione|
|----------|-----------|
|com. Microsoft. VisualStudio. debuggingee. Arguments|Argomenti passati al programma all'avvio del debug. Per le app .NET Core, questi argomenti sono in genere percorsi di ricerca aggiuntivi per i pacchetti NuGet seguiti dal percorso dell'assembly di output del progetto.|
|com. Microsoft. VisualStudio. debuggingee. killprogram|Questo comando viene usato per arrestare il programma sottoposto a debug in esecuzione all'interno del contenitore, se necessario.|
|com. Microsoft. VisualStudio. debuggingee. Program|Programma avviato all'avvio del debug. Per le app .NET Core questa impostazione è in genere **DotNet**.|
|com. Microsoft. VisualStudio. debuggingee. WorkingDirectory|Directory utilizzata come directory iniziale all'avvio del debug. Questa impostazione è in genere */app* per i contenitori Linux o *C:\app* per i contenitori di Windows.|

## <a name="next-steps"></a>Passaggi successivi

Per informazioni sulle proprietà di MSBuild in genere, vedere [proprietà di MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Vedere anche

[Proprietà di compilazione degli strumenti contenitore](container-msbuild-properties.md)

[Impostazioni di avvio degli strumenti contenitore](container-launch-settings.md)

[Proprietà riservate e note MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
