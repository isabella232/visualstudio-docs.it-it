---
title: Docker Compose di compilazione
author: ghogen
description: Informazioni su come modificare le proprietà Docker Compose compilazione per personalizzare la modalità Visual Studio compilazione ed esecuzione di un Docker Compose app Docker Compose personalizzata.
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 04/06/2021
ms.technology: vs-container-tools
ms.topic: reference
ms.openlocfilehash: b541568567d7af7002ecf576700099fec1aeb2d7
ms.sourcegitcommit: ff81d69902e869b227d9ceb6e95023d1c63425b1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/06/2021
ms.locfileid: "129595131"
---
# <a name="docker-compose-build-properties"></a>Docker Compose proprietà di compilazione

Oltre alle proprietà che controllano i singoli progetti Docker, descritte in Container [Tools build properties](container-msbuild-properties.md)(Proprietà di compilazione di Strumenti contenitore), è anche possibile personalizzare il modo in cui Visual Studio compila i progetti Docker Compose impostando le proprietà di Docker Compose che MSBuild usa per compilare la soluzione. È anche possibile controllare il modo in cui Visual Studio debugger esegue le app Docker Compose impostando etichette di file nei file Docker Compose di configurazione.

## <a name="how-to-set-the-msbuild-properties"></a>Come impostare le MSBuild predefinite

Per impostare il valore di una proprietà, modificare il file di progetto. Per Docker Compose proprietà, questo file di progetto è quello con estensione dcproj, se non diversamente indicato nella tabella nella sezione successiva. Si supponga, ad esempio, di voler specificare per avviare il browser quando si avvia il debug. È possibile impostare la `DockerLaunchAction` proprietà nel file di progetto con estensione dcproj come indicato di seguito.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

È possibile aggiungere l'impostazione della proprietà a un elemento esistente oppure, se non è `PropertyGroup` presente, creare un nuovo `PropertyGroup` elemento.

## <a name="docker-compose-msbuild-properties"></a>Proprietà d MSBuild per Docker Compose

La tabella seguente illustra le MSBuild disponibili per i Docker Compose progetto.

| Nome proprietà | Location | Descrizione | Valore predefinito  |
|---------------|----------|-------------|----------------|
|AdditionalComposeFilePaths|dcproj|Specifica altri file compose in un elenco delimitato da punto e virgola da inviare al docker-compose.exe per tutti i comandi. Sono consentiti percorsi relativi dal file di progetto docker-compose (dcproj).|-|
|DockerComposeBaseFilePath|dcproj|Specifica la prima parte dei nomi file dei file docker-compose, senza *l'estensione yml.* Ad esempio: <br>1. DockerComposeBaseFilePath = null/undefined: usare il percorso del file di base *docker-compose* e i file verranno denominati *docker-compose.yml* e *docker-compose.override.yml.*<br>2. DockerComposeBaseFilePath = *mydockercompose*: i file verranno denominati *mydockercompose.yml* e *mydockercompose.override.yml*.<br> 3. DockerComposeBaseFilePath = *.. \mydockercompose:* i file saranno di un livello superiore. |docker-compose|
|DockerComposeBuildArguments|dcproj|Specifica i parametri aggiuntivi da passare al `docker-compose build` comando. Ad esempio, `--parallel --pull`. |
|DockerComposeDownArguments|dcproj|Specifica i parametri aggiuntivi da passare al `docker-compose down` comando. Ad esempio, `--timeout 500`.|-|  
|DockerComposeProjectName| dcproj | Se specificato, esegue l'override del nome del progetto per un progetto docker-compose. | "dockercompose" + hash generato automaticamente |
|DockerComposeProjectPath|csproj o vbproj|Percorso relativo del file di progetto docker-compose (dcproj). Impostare questa proprietà quando si pubblica il progetto di servizio per trovare le impostazioni di compilazione dell'immagine associate archiviate nel file docker-compose.yml.|-|
|DockerComposeProjectsToIgnore|dcproj| Specifica i progetti che docker-compose devono ignorare durante il debug. Questa proprietà può essere utilizzata per qualsiasi progetto. I percorsi dei file possono essere specificati in uno dei due modi seguenti: <br> 1. Relativo a dcproj. Ad esempio, `<DockerComposeProjectsToIgnore>path\to\AngularProject1.csproj</DockerComposeProjectsToIgnore>`. <br> 2. Percorsi assoluti.<br> **Nota:** i percorsi devono essere separati dal carattere di delimitazione `;` .|-|
|DockerComposeUpArguments|dcproj|Specifica i parametri aggiuntivi da passare al `docker-compose up` comando. Ad esempio, `--timeout 500`.|-|
|DockerDevelopmentMode| dcproj | Controlla se il progetto utente è compilato nel contenitore. I valori consentiti **di Fast** **o Regular** [controllano quali fasi vengono compilate](https://aka.ms/containerfastmode) in un Dockerfile. La configurazione di debug è la modalità rapida per impostazione predefinita e la modalità normale in caso contrario. | Veloce |
|DockerLaunchAction| dcproj | Specifica l'azione di avvio da eseguire su F5 o CTRL+F5.  I valori consentiti sono None, LaunchBrowser e LaunchWCFTestClient. | Nessuno |
|DockerLaunchBrowser| dcproj | Indica se avviare il browser. Ignorato se viene specificato DockerLaunchAction. | Falso |
|DockerServiceName| dcproj| Se si specifica DockerLaunchAction o DockerLaunchBrowser, DockerServiceName specifica il servizio a cui viene fatto riferimento nel file docker-compose da avviare.|-|
|DockerServiceUrl| dcproj | URL da usare all'avvio del browser.  I token di sostituzione validi sono "{ServiceIPAddress}", "{ServicePort}" e "{Scheme}".  Ad esempio: {Scheme}://{ServiceIPAddress}:{ServicePort}|-|
|DockerTargetOS| dcproj | Sistema operativo di destinazione usato durante la compilazione dell'immagine Docker.|-|

## <a name="example"></a>Esempio

Se si modifica il percorso dei file docker compose, impostando su un percorso relativo, è anche necessario assicurarsi che il contesto di compilazione sia stato modificato in modo che faccia riferimento alla cartella `DockerComposeBaseFilePath` della soluzione. Ad esempio, se il file docker compose è una cartella denominata *DockerComposeFiles,* il file docker compose deve impostare il contesto di compilazione su ".." o ".. /..", a seconda della posizione relativa alla cartella della soluzione.

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

Il file *mydockercompose.yml* dovrebbe essere simile al seguente, con il contesto di compilazione impostato sul percorso relativo della cartella della soluzione (in questo caso, `..` ).

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
> DockerComposeBuildArguments, DockerComposeDownArguments e DockerComposeUpArguments sono le novità di Visual Studio 2019 versione 16.3.

## <a name="overriding-visual-studios-docker-compose-configuration"></a>Override della Visual Studio della Docker Compose predefinita

In *genere docker-compose.override.yml* viene usato per eseguire l'override di determinate impostazioni in *docker-compose.yml.* Inoltre, Visual Studio genera file di override *docker-compose.vs.debug.g,yml* (per la modalità rapida) e *docker-compose.vs.release.g.yml* (per la modalità regolare) con impostazioni specifiche per l'esecuzione dell'applicazione all'interno di Visual Studio.   È possibile eseguire l'override di queste impostazioni di Visual Studio inserendo un file denominato  *docker-compose.vs.debug.yml* (per la  modalità rapida) o *docker-compose.vs.release.yml* (per la modalità regolare) nella stessa directory del file *docker-compose.yml.* Fare clic con il pulsante destro del mouse sul progetto docker-compose e scegliere Apri cartella **in Esplora file** , quindi usare Aggiungi elemento esistente per aggiungere il file al  >   progetto docker-compose.

>[!TIP] 
>Per trovare i valori predefiniti per una delle impostazioni di Visual Studio, cercare nella directory di output intermedia (ad *esempio, obj/Docker*) per *docker-compose.vs.debug.g.yml* o *docker-compose.vs.release.g.yml*. Questi file vengono generati da Visual Studio e non devono essere modificati.

### <a name="docker-compose-file-labels"></a>Docker Compose etichette dei file

 In *docker-compose.vs.debug.yml* o *docker-compose.vs.release.yml* è possibile definire etichette specifiche dell'override come indicato di seguito:

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

Usare le virgolette doppie per i valori, come nell'esempio precedente, e usare la barra rovesciata come carattere di escape per le barre rovesciate nei percorsi.

|Nome etichetta|Descrizione|
|----------|-----------|
|com.microsoft.visualstudio.debuggee.arguments|Argomenti passati al programma all'avvio del debug. Per le app .NET Core, questi argomenti sono in genere percorsi di ricerca aggiuntivi per NuGet pacchetti seguiti dal percorso dell'assembly di output del progetto.|
|com.microsoft.visualstudio.debuggee.program|Programma avviato all'avvio del debug. Per le app .NET Core, questa impostazione è in genere **dotnet**.|
|com.microsoft.visualstudio.debuggee.workingdirectory|Directory utilizzata come directory iniziale all'avvio del debug. Questa impostazione è in *genere /app* per contenitori Linux o *C:\app* per Windows contenitori.|
|com.microsoft.visualstudio.debuggee.killprogram|Questo comando viene usato per arrestare il programma oggetto del debug in esecuzione all'interno del contenitore (quando necessario).|

### <a name="customize-the-docker-build-process"></a>Personalizzare il processo di compilazione di Docker

È possibile dichiarare la fase da compilare nel Dockerfile usando `target` l'impostazione nella `build` proprietà . Questo override può essere usato solo in *docker-compose.vs.debug.yml* o *docker-compose.vs.release.yml* 

```yml
services:
  webapplication1:
    build:
      target: customStage
    labels:
      ...
```

### <a name="customize-the-app-startup-process"></a>Personalizzare il processo di avvio dell'app

È possibile eseguire un comando o uno script personalizzato prima di avviare l'app usando `entrypoint` l'impostazione e rendendola dipendente da `DockerDevelopmentMode` . Ad esempio, se è necessario configurare un certificato solo **in** modalità rapida eseguendo , ma non in modalità normale, è possibile aggiungere il codice seguente solo `update-ca-certificates` in  *docker-compose.vs.debug.yml:* 

```yml
services:
  webapplication1:
    entrypoint: "sh -c 'update-ca-certificates && tail -f /dev/null'"
    labels:
      ...
```

## <a name="next-steps"></a>Passaggi successivi

Per informazioni sulle proprietà MSBuild, vedere proprietà [MSBuild .](../msbuild/msbuild-properties.md)

## <a name="see-also"></a>Vedi anche

[Proprietà di compilazione di Strumenti contenitore](container-msbuild-properties.md)

[Impostazioni di avvio di Strumenti contenitore](container-launch-settings.md)

[Gestire i profili di avvio Docker Compose in Visual Studio](launch-profiles.md)

[Proprietà riservate e note MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
