---
title: Visual Studio Container Tools Docker Compose impostazioni di compilazione
author: ghogen
description: Panoramica del processo di compilazione degli strumenti contenitore
ms.author: ghogen
ms.date: 08/12/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 85cb8745a14439cfb09036a1bc96e6bd0fa15ae4
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2020
ms.locfileid: "79988509"
---
# <a name="docker-compose-build-properties"></a>Docker Compose proprietà di compilazione

Oltre alle proprietà che controllano i singoli progetti Docker, descritti in Proprietà di [compilazione degli strumenti contenitore](container-msbuild-properties.md), è anche possibile personalizzare il modo in cui Visual Studio compila i progetti Docker Compose impostando le proprietà Docker Compose utilizzate da MSBuild per compilare la soluzione. È anche possibile controllare il modo in cui il debugger di Visual Studio esegue le app Docker Compose impostando le etichette dei file nei file di configurazione di Docker Compose.You can also control how the Visual Studio debugger runs your Docker Compose apps by setting file labels in Docker Compose configuration files.

## <a name="how-to-set-the-msbuild-properties"></a>Come impostare le proprietà di MSBuild

Per impostare il valore di una proprietà, modificare il file di progetto. Per le proprietà Docker Compose, questo file di progetto è quello con estensione dcproj, se non diversamente indicato nella tabella nella sezione successiva. Si supponga, ad esempio, di voler specificare di avviare il browser quando si avvia il debug. È possibile `DockerLaunchAction` impostare la proprietà nel file di progetto con estensione dcproj come indicato di seguito.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

È possibile aggiungere l'impostazione della proprietà a un elemento `PropertyGroup` esistente `PropertyGroup` o, se non è presente, creare un nuovo elemento.

## <a name="docker-compose-msbuild-properties"></a>Proprietà d MSBuild per Docker Compose

Nella tabella seguente vengono illustrate le proprietà MSBuild disponibili per i progetti Docker Compose.

| Nome proprietà | Location | Descrizione | Valore predefinito  |
|---------------|----------|-------------|----------------|
|AdditionalComposeFilePaths|dcproj (inmodo)|Specifica file di composizione aggiuntivi in un elenco delimitato da punti e virgola da inviare a docker-compose.exe per tutti i comandi. Sono consentiti percorsi relativi dal file di progetto docker-compose (dcproj).|-|
|DockerComposeBaseFilePath (percorso dockerComposeBaseFilePath)|dcproj (inmodo)|Specifica la prima parte dei nomi di file dei file docker-compose, senza l'estensione *yml.* Ad esempio: <br>1. DockerComposeBaseFilePath - null/undefined: utilizzare il percorso del file di base *docker-compose*e i file saranno *denominati docker-compose.yml* e *docker-compose.override.yml*<br>2. DockerComposeBaseFilePath : *mydockercompose*: i file saranno *denominati mydockercompose.yml* e *mydockercompose.override.yml*<br> 3. DockerComposeBaseFilePath *.. :* i file saranno di un livello superiore. |docker-compose|
|DockerComposeBuildArguments|dcproj (inmodo)|Specifica i parametri aggiuntivi da `docker-compose build` passare al comando. Ad esempio, usare `--parallel --pull` |
|DockerComposeDownArguments|dcproj (inmodo)|Specifica i parametri aggiuntivi da `docker-compose down` passare al comando. Ad esempio, usare `--timeout 500`|-|  
|DockerComposeProjectPath|csproj o vbproj|Percorso relativo del file di progetto docker-compose (dcproj). Impostare questa proprietà quando si pubblica il progetto di servizio per trovare le impostazioni di compilazione dell'immagine associate archiviate nel file docker-compose.yml.|-|
|DockerComposeUpArguments|dcproj (inmodo)|Specifica i parametri aggiuntivi da `docker-compose up` passare al comando. Ad esempio, usare `--timeout 500`|-|
|DockerDevelopmentMode|dcproj (inmodo)| Controlla se l'ottimizzazione "build-on-host" (Velocità rapida) è abilitata.  I valori consentiti sono **Veloce** e **Regolare**. | Veloce |
|DockerLaunchAction| dcproj (inmodo) | Specifica l'azione di avvio da eseguire su F5 o Ctrl -F5.  I valori consentiti sono None, LaunchBrowser e LaunchWCFTestClient|nessuno|
|DockerLaunchBrowser (Browserdia> per il lancio di Un| dcproj (inmodo) | Indica se avviare il browser. Ignorato se si specifica DockerLaunchAction. | False |
|Nome servizio DockerService| dcproj (inmodo)|Se si specifica DockerLaunchAction o DockerLaunchBrowser, DockerServiceName è il nome del servizio che deve essere avviato.  Utilizzare questa proprietà per determinare quali dei potenziali molti progetti a cui un file docker-compose può fare riferimento verrà avviato.|-|
|DockerServiceUrl| dcproj (inmodo) | URL da utilizzare all'avvio del browser.  I token di sostituzione validi sono i caratteri di sostituzione ""ServiceIPAddress"", "'ServicePort'" e "'Scheme'".  Ad esempio: "Schema" ""IndirizzoIPServizio": "PortaServizio"|-|
|DockerTargetOS| dcproj (inmodo) | Sistema operativo di destinazione utilizzato durante la compilazione dell'immagine Docker.|-|

## <a name="example"></a>Esempio

Se si modifica il percorso della finestra mobile `DockerComposeBaseFilePath` comporre i file, impostando su un percorso relativo, è inoltre necessario assicurarsi che il contesto di compilazione viene modificato in modo che faccia riferimento alla cartella della soluzione. Ad esempio, se il file docker compose è una cartella denominata *DockerComposeFiles*, il file di composizione docker deve impostare il contesto di compilazione su ".." o ".. /..", a seconda di dove si trova rispetto alla cartella della soluzione.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0" Sdk="Microsoft.Docker.Sdk">
  <PropertyGroup Label="Globals">
    <ProjectVersion>2.1</ProjectVersion>
    <DockerTargetOS>Windows</DockerTargetOS>
    <ProjectGuid>154022c1-8014-4e9d-bd78-6ff46670ffa4</ProjectGuid>
    <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
    <DockerServiceUrl>{Scheme}://{ServiceIPAddress}{ServicePort}</DockerServiceUrl>
    <DockerServiceName>webapplication1</DockerServiceName>
    <DockerComposeBaseFilePath>DockerComposeFiles\mydockercompose</DockerComposeBaseFilePath>
    <AdditionalComposeFilePaths>AdditionalComposeFiles\myadditionalcompose.yml</AdditionalComposeFilePaths>
  </PropertyGroup>
  <ItemGroup>
    <None Include="DockerComposeFiles\mydockercompose.override.yml">
      <DependentUpon>DockerComposeFiles\mydockercompose.yml</DependentUpon>
    </None>
    <None Include="DockerComposeFiles\mydockercompose.yml" />
    <None Include=".dockerignore" />
  </ItemGroup>
</Project>
```

Il file *mydockercompose.yml* dovrebbe essere simile al seguente, con il contesto di `..`compilazione impostato sul percorso relativo della cartella della soluzione (in questo caso, ).

```yml
version: '3.4'

services:
  webapplication1:
    image: ${DOCKER_REGISTRY-}webapplication1
    build:
      context: ..
      dockerfile: WebApplication1\Dockerfile
```

> [!NOTE]
> DockerComposeBuildArguments, DockerComposeDownArguments e DockerComposeUpArguments sono nuovi in Visual Studio 2019 versione 16.3.

## <a name="docker-compose-file-labels"></a>Docker Compose etichette file

È inoltre possibile eseguire l'override di determinate impostazioni inserendo un file denominato *docker-compose.vs.debug.yml* (per la configurazione **Debug)** o *docker-compose.vs.release.yml* (per la configurazione **di rilascio)** nella stessa directory del file *docker-compose.yml.*  In questo file, è possibile specificare le impostazioni come segue:

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

Racchiudere i valori tra virgolette doppie e usare la barra rovesciata come carattere di escape per le barre rovesciate nei percorsi.

|Nome etichetta|Descrizione|
|----------|-----------|
|com.microsoft.visualstudio.debuggee.arguments (informazioni in lingua lingua instato tutti i problemi)|Argomenti passati al programma all'avvio del debug. Per le app .NET Core, questi argomenti sono in genere percorsi di ricerca aggiuntivi per i pacchetti NuGet seguiti dal percorso dell'assembly di output del progetto.|
|com.microsoft.visualstudio.debuggee.killprogram (informazioni in lingua inlinguatta)|Questo comando viene utilizzato per arrestare il programma di debug in esecuzione all'interno del contenitore (se necessario).|
|com.microsoft.visualstudio.debuggee.program|Programma avviato all'avvio del debug. Per le app .NET Core, questa impostazione è in genere **dotnet**.|
|com.microsoft.visualstudio.debuggee.directorydilavoro|Directory utilizzata come directory iniziale all'avvio del debug. Questa impostazione è in genere */app* per i contenitori Linux o *C: .*|

## <a name="customize-the-app-startup-process"></a>Personalizzare il processo di avvio dell'app

Puoi eseguire un comando o uno script personalizzato `entrypoint` prima di avviare l'app usando l'impostazione e rendendola dipendente dalla configurazione. Ad esempio, se è necessario impostare **Debug** un certificato `update-ca-certificates`solo in modalità Debug eseguendo , ma non in modalità **di rilascio,** è possibile aggiungere il codice seguente solo in *docker-compose.vs.debug.yml*:

```yml
services:
  webapplication1:
    entrypoint: "sh -c 'update-ca-certificates && tail -f /dev/null'"
    labels:
      ...
```

Se si ostoga *docker-compose.vs.release.yml* o *docker-compose.vs.debug.yml,* Visual Studio ne genera una in base alle impostazioni predefinite.

## <a name="next-steps"></a>Passaggi successivi

Per informazioni sulle proprietà MSBuild in genere, vedere [Proprietà MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Vedere anche

[Proprietà di compilazione degli strumenti contenitoreContainer Tools build properties](container-msbuild-properties.md)

[Impostazioni di avvio degli strumenti contenitore](container-launch-settings.md)

[Proprietà di MSBuild riservate e note](../msbuild/msbuild-reserved-and-well-known-properties.md)
