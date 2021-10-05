---
title: Docker Compose di compilazione
author: ghogen
description: Informazioni su come modificare le Docker Compose di compilazione per personalizzare il modo in cui Visual Studio compila ed esegue un'Docker Compose applicazione.
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 04/06/2021
ms.technology: vs-container-tools
ms.topic: reference
ms.openlocfilehash: e165f25d8f757bbf60cd7b71e9ebd9e411b98c74
ms.sourcegitcommit: 2eb12954b7b0ac9508fff11a86c54e880f3d104f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2021
ms.locfileid: "129439717"
---
# <a name="docker-compose-build-properties"></a>Docker Compose proprietà di compilazione

Oltre alle proprietà che controllano singoli progetti Docker, descritte [in](container-msbuild-properties.md)Proprietà di compilazione di Strumenti contenitori, è anche possibile personalizzare il modo in cui Visual Studio compila i progetti Docker Compose impostando le proprietà Docker Compose che MSBuild usa per compilare la soluzione. È anche possibile controllare il modo in cui il debugger Visual Studio le app Docker Compose impostando etichette di file nei Docker Compose di configurazione.

## <a name="how-to-set-the-msbuild-properties"></a>Come impostare le proprietà MSBuild personalizzate

Per impostare il valore di una proprietà, modificare il file di progetto. Per Docker Compose proprietà, questo file di progetto è quello con estensione dcproj, se non diversamente indicato nella tabella nella sezione successiva. Si supponga, ad esempio, di voler specificare per avviare il browser quando si avvia il debug. È possibile impostare la `DockerLaunchAction` proprietà nel file di progetto con estensione dcproj come indicato di seguito.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

È possibile aggiungere l'impostazione della proprietà a un elemento esistente oppure, se non ce `PropertyGroup` n'è uno, creare un nuovo `PropertyGroup` elemento.

## <a name="docker-compose-msbuild-properties"></a>Proprietà d MSBuild per Docker Compose

La tabella seguente illustra le MSBuild disponibili per i Docker Compose progetto.

| Nome proprietà | Location | Descrizione | Valore predefinito  |
|---------------|----------|-------------|----------------|
|AdditionalComposeFilePaths|dcproj|Specifica altri file compose in un elenco delimitato da punto e virgola da inviare a docker-compose.exe per tutti i comandi. Sono consentiti percorsi relativi dal file di progetto docker-compose (dcproj).|-|
|DockerComposeBaseFilePath|dcproj|Specifica la prima parte dei nomi file dei file docker-compose, senza *l'estensione yml.* Ad esempio: <br>1. DockerComposeBaseFilePath = null/undefined: usare il percorso del file di base *docker-compose* e i file saranno denominati *docker-compose.yml* e *docker-compose.override.yml.*<br>2. DockerComposeBaseFilePath = *mydockercompose*: i file saranno denominati *mydockercompose.yml* e *mydockercompose.override.yml.*<br> 3. DockerComposeBaseFilePath = *.. \mydockercompose:* i file saranno di un livello superiore. |docker-compose|
|DockerComposeBuildArguments|dcproj|Specifica i parametri aggiuntivi da passare al `docker-compose build` comando. Ad esempio, `--parallel --pull`. |
|DockerComposeDownArguments|dcproj|Specifica i parametri aggiuntivi da passare al `docker-compose down` comando. Ad esempio, `--timeout 500`.|-|  
|DockerComposeProjectName| dcproj | Se specificato, esegue l'override del nome del progetto per un progetto docker-compose. | "dockercompose" + hash generato automaticamente |
|DockerComposeProjectPath|csproj o vbproj|Percorso relativo del file di progetto docker-compose (dcproj). Impostare questa proprietà quando si pubblica il progetto di servizio per trovare le impostazioni di compilazione dell'immagine associate archiviate nel file docker-compose.yml.|-|
|DockerComposeProjectsToIgnore|dcproj| Specifica i progetti che devono essere ignorati dagli strumenti docker-compose durante il debug. Questa proprietà può essere usata per qualsiasi progetto. I percorsi di file possono essere specificati in uno dei due modi seguenti: <br> 1. Relativo a dcproj. Ad esempio, `<DockerComposeProjectsToIgnore>path\to\AngularProject1.csproj</DockerComposeProjectsToIgnore>`. <br> 2. Percorsi assoluti.<br> **Nota:** i percorsi devono essere separati dal carattere di delimitazione `;` .|-|
|DockerComposeUpArguments|dcproj|Specifica i parametri aggiuntivi da passare al `docker-compose up` comando. Ad esempio, `--timeout 500`.|-|
|DockerDevelopmentMode| dcproj | Controlla se il progetto utente è compilato nel contenitore. I valori consentiti di **Fast** **o Regular** [controllano le fasi compilate](https://aka.ms/containerfastmode) in un Dockerfile. Per impostazione predefinita, la configurazione di Debug è modalità veloce e la modalità normale in caso contrario. | Veloce |
|DockerLaunchAction| dcproj | Specifica l'azione di avvio da eseguire su F5 o CTRL+F5.  I valori consentiti sono None, LaunchBrowser e LaunchWCFTestClient. | Nessuno |
|DockerLaunchBrowser| dcproj | Indica se avviare il browser. Ignorato se viene specificato DockerLaunchAction. | Falso |
|DockerServiceName| dcproj| Se si specifica DockerLaunchAction o DockerLaunchBrowser, DockerServiceName specifica il servizio a cui viene fatto riferimento nel file docker-compose.|-|
|DockerServiceUrl| dcproj | URL da utilizzare all'avvio del browser.  I token di sostituzione validi sono "{ServiceIPAddress}", "{ServicePort}" e "{Scheme}".  Ad esempio: {Scheme}://{ServiceIPAddress}:{ServicePort}|-|
|DockerTargetOS| dcproj | Sistema operativo di destinazione usato durante la compilazione dell'immagine Docker.|-|

## <a name="example"></a>Esempio

Se si modifica il percorso dei file docker compose impostando su un percorso relativo, è anche necessario assicurarsi che il contesto di compilazione sia stato modificato in modo che faccia riferimento alla cartella `DockerComposeBaseFilePath` della soluzione. Ad esempio, se il file docker compose è una cartella denominata *DockerComposeFiles,* il file docker compose deve impostare il contesto di compilazione su ".." o ".. /..", a seconda della posizione in cui si trova rispetto alla cartella della soluzione.

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
> DockerComposeBuildArguments, DockerComposeDownArguments e DockerComposeUpArguments sono nuovi Visual Studio 2019 versione 16.3.

## <a name="overriding-visual-studios-docker-compose-configuration"></a>Override della Visual Studio configurazione Docker Compose predefinita

Il modo normale che Docker fornisce per eseguire l'override delle impostazioni Docker Compose standard è usare i file *docker-compose.override.debug.yml* e *docker-compose.override.release.yml,* ma non è possibile eseguire l'override delle impostazioni specifiche di Visual Studio in tali file. È possibile eseguire l'override delle impostazioni di Visual Studio inserendo un file denominato *docker-compose.vs.debug.yml* (per la modalità rapida) o *docker-compose.vs.release.yml* (per **la** modalità regolare) nella stessa directory del file  *docker-compose.yml.* Creare il file usando il Esplora file e quindi usare **Aggiungi** elemento esistente per aggiungere il  >   file al progetto docker-compose.

>[!TIP] 
>Per trovare i valori predefiniti per una delle impostazioni Visual Studio, cercare direttamente nell'output intermedio (ad esempio *obj/Docker*) per *docker-compose.vs.debug.g.yml* o *docker-compose.vs.release.g.yml.* Questi file vengono generati da Visual Studio e non devono essere modificati.

### <a name="docker-compose-file-labels"></a>Docker Compose etichette di file

 In *docker-compose.vs.debug.yml* o *docker-compose.vs.release.yml* è possibile definire etichette specifiche dell'override come indicato di seguito:

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

Usare le virgolette doppie intorno ai valori, come nell'esempio precedente, e usare la barra rovesciata come carattere di escape per le barre rovesciate nei percorsi.

|Nome etichetta|Descrizione|
|----------|-----------|
|com.microsoft.visualstudio.debuggee.arguments|Argomenti passati al programma all'avvio del debug. Per le app .NET Core, questi argomenti sono in genere percorsi di ricerca aggiuntivi per NuGet pacchetti seguiti dal percorso dell'assembly di output del progetto.|
|com.microsoft.visualstudio.debuggee.program|Programma avviato all'avvio del debug. Per le app .NET Core, questa impostazione è in genere **dotnet**.|
|com.microsoft.visualstudio.debuggee.workingdirectory|Directory utilizzata come directory iniziale all'avvio del debug. Questa impostazione è in *genere /app* per contenitori Linux o *C:\app* per Windows contenitori.|
|com.microsoft.visualstudio.debuggee.killprogram|Questo comando viene usato per arrestare il programma oggetto del debug in esecuzione all'interno del contenitore (quando necessario).|

### <a name="customize-the-docker-build-process"></a>Personalizzare il processo di compilazione di Docker

È possibile dichiarare quale fase compilare nel Dockerfile usando `target` l'impostazione nella `build` proprietà . Questo override può essere usato solo in *docker-compose.vs.debug.yml* o *docker-compose.vs.release.yml* 

```yml
services:
  webapplication1:
    build:
      target: customStage
    labels:
      ...
```

### <a name="customize-the-app-startup-process"></a>Personalizzare il processo di avvio dell'app

È possibile eseguire un comando o uno script personalizzato prima di avviare l'app usando `entrypoint` l'impostazione e rendendola dipendente da `DockerDevelopmentMode` . Ad esempio, se è necessario configurare un certificato solo **in** modalità rapida eseguendo , ma non in modalità normale, è possibile aggiungere il codice seguente solo `update-ca-certificates` in  *docker-compose.vs.debug.yml*: 

```yml
services:
  webapplication1:
    entrypoint: "sh -c 'update-ca-certificates && tail -f /dev/null'"
    labels:
      ...
```

## <a name="next-steps"></a>Passaggi successivi

Per informazioni sulle proprietà MSBuild in genere, [vedere MSBuild proprietà](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Vedi anche

[Proprietà di compilazione di Strumenti contenitore](container-msbuild-properties.md)

[Impostazioni di avvio di Strumenti contenitore](container-launch-settings.md)

[Gestire i profili di avvio Docker Compose in Visual Studio](launch-profiles.md)

[Proprietà riservate e note MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
