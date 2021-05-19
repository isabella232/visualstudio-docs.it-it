---
title: Docker Compose di compilazione
author: ghogen
description: Informazioni su come modificare le Docker Compose di compilazione per personalizzare il modo in cui Visual Studio compila ed esegue un'Docker Compose applicazione.
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 04/06/2021
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: b3744640aada798179c86cc60d2c8ce7b02ccfaa
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973479"
---
# <a name="docker-compose-build-properties"></a>Docker Compose proprietà di compilazione

Oltre alle proprietà che controllano singoli progetti Docker, descritte [in](container-msbuild-properties.md)Proprietà di compilazione di Strumenti contenitori, è anche possibile personalizzare il modo in cui Visual Studio compila i progetti Docker Compose impostando le proprietà Docker Compose utilizzate da MSBuild per compilare la soluzione. È anche possibile controllare il modo in cui il debugger Visual Studio le app Docker Compose impostando etichette di file nei Docker Compose di configurazione.

## <a name="how-to-set-the-msbuild-properties"></a>Come impostare le proprietà di MSBuild

Per impostare il valore di una proprietà, modificare il file di progetto. Per Docker Compose proprietà, questo file di progetto è quello con estensione dcproj, se non diversamente indicato nella tabella nella sezione successiva. Si supponga, ad esempio, di voler specificare per avviare il browser quando si avvia il debug. È possibile impostare la proprietà nel file di `DockerLaunchAction` progetto con estensione dcproj come indicato di seguito.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

È possibile aggiungere l'impostazione della proprietà a un elemento esistente oppure, se non ce `PropertyGroup` n'è uno, creare un nuovo `PropertyGroup` elemento.

## <a name="docker-compose-msbuild-properties"></a>Proprietà d MSBuild per Docker Compose

La tabella seguente illustra le proprietà di MSBuild disponibili per Docker Compose progetto.

| Nome proprietà | Location | Descrizione | Valore predefinito  |
|---------------|----------|-------------|----------------|
|AdditionalComposeFilePaths|dcproj|Specifica altri file compose in un elenco delimitato da punto e virgola da inviare a docker-compose.exe per tutti i comandi. Sono consentiti percorsi relativi dal file di progetto docker-compose (dcproj).|-|
|DockerComposeBaseFilePath|dcproj|Specifica la prima parte dei nomi file dei file docker-compose, senza *l'estensione yml.* Esempio: <br>1. DockerComposeBaseFilePath = null/undefined: usare il percorso del file di base *docker-compose* e i file saranno denominati *docker-compose.yml* e *docker-compose.override.yml.*<br>2. DockerComposeBaseFilePath = *mydockercompose*: i file verranno denominati *mydockercompose.yml* e *mydockercompose.override.yml*.<br> 3. DockerComposeBaseFilePath = *.. \mydockercompose:* i file saranno di un livello superiore. |docker-compose|
|DockerComposeBuildArguments|dcproj|Specifica i parametri aggiuntivi da passare al `docker-compose build` comando. Ad esempio: `--parallel --pull`. |
|DockerComposeDownArguments|dcproj|Specifica i parametri aggiuntivi da passare al `docker-compose down` comando. Ad esempio: `--timeout 500`.|-|  
|DockerComposeProjectName| dcproj | Se specificato, esegue l'override del nome del progetto per un progetto docker-compose. | "dockercompose" + hash generato automaticamente |
|DockerComposeProjectPath|csproj o vbproj|Percorso relativo del file di progetto docker-compose (dcproj). Impostare questa proprietà quando si pubblica il progetto di servizio per trovare le impostazioni di compilazione dell'immagine associate archiviate nel file docker-compose.yml.|-|
|DockerComposeProjectsToIgnore|dcproj| Specifica i progetti che docker-compose devono ignorare durante il debug. Questa proprietà può essere usata per qualsiasi progetto. I percorsi di file possono essere specificati in uno dei due modi seguenti: <br> 1. Relativo a dcproj. Ad esempio: `<DockerComposeProjectsToIgnore>path\to\AngularProject1.csproj</DockerComposeProjectsToIgnore>`. <br> 2. Percorsi assoluti.<br> **Nota:** i percorsi devono essere separati dal carattere di delimitazione `;` .|-|
|DockerComposeUpArguments|dcproj|Specifica i parametri aggiuntivi da passare al `docker-compose up` comando. Ad esempio: `--timeout 500`.|-|
|DockerDevelopmentMode| dcproj | Controlla se il progetto utente è compilato nel contenitore. I valori consentiti di **Fast** **o Regular** [controllano le fasi compilate](https://aka.ms/containerfastmode) in un Dockerfile. Per impostazione predefinita, la configurazione di Debug è modalità veloce e la modalità normale in caso contrario. | Veloce |
|DockerLaunchAction| dcproj | Specifica l'azione di avvio da eseguire su F5 o CTRL+F5.  I valori consentiti sono None, LaunchBrowser e LaunchWCFTestClient. | Nessuno |
|DockerLaunchBrowser| dcproj | Indica se avviare il browser. Ignorato se viene specificato DockerLaunchAction. | Falso |
|DockerServiceName| dcproj| Se si specifica DockerLaunchAction o DockerLaunchBrowser, DockerServiceName specifica il servizio a cui viene fatto riferimento nel file docker-compose da avviare.|-|
|DockerServiceUrl| dcproj | URL da usare all'avvio del browser.  I token di sostituzione validi sono "{ServiceIPAddress}", "{ServicePort}" e "{Scheme}".  Ad esempio: {Scheme}://{ServiceIPAddress}:{ServicePort}|-|
|DockerTargetOS| dcproj | Sistema operativo di destinazione usato durante la compilazione dell'immagine Docker.|-|

## <a name="example"></a>Esempio

Se si modifica il percorso dei file docker compose impostando su un percorso relativo, è anche necessario assicurarsi che il contesto di compilazione sia stato modificato in modo che faccia riferimento alla cartella `DockerComposeBaseFilePath` della soluzione. Ad esempio, se il file docker compose è una cartella denominata *DockerComposeFiles,* il file docker compose deve impostare il contesto di compilazione su ".." o ".. /..", a seconda della posizione relativa alla cartella della soluzione.

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

È possibile eseguire l'override di determinate impostazioni inserendo un file denominato *docker-compose.vs.debug.yml* (per la  modalità **rapida)** o *docker-compose.vs.release.yml* (per la modalità regolare) nella stessa directory del file *docker-compose.yml.* 

>[!TIP] 
>Per trovare i valori predefiniti per una di queste impostazioni, vedere *docker-compose.vs.debug.g.yml* o *docker-compose.vs.release.g.yml.*

### <a name="docker-compose-file-labels"></a>Docker Compose etichette dei file

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
|Com.microsoft.visualstudio.debuggee.arguments|Argomenti passati al programma all'avvio del debug. Per le app .NET Core, questi argomenti sono in genere percorsi di ricerca aggiuntivi per i pacchetti NuGet seguiti dal percorso dell'assembly di output del progetto.|
|Com.microsoft.visualstudio.debuggee.program|Programma avviato all'avvio del debug. Per le app .NET Core, questa impostazione è in genere **dotnet**.|
|Com.microsoft.visualstudio.debuggee.workingdirectory|Directory utilizzata come directory iniziale all'avvio del debug. Questa impostazione è in genere */app* per contenitori Linux o *C:\app* per contenitori Windows.|
|Com.microsoft.visualstudio.debuggee.killprogram|Questo comando viene usato per arrestare il programma dell'oggetto del debug in esecuzione all'interno del contenitore (se necessario).|

### <a name="customize-the-docker-build-process"></a>Personalizzare il processo di compilazione docker

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

È possibile eseguire un comando o uno script personalizzato prima di avviare l'app usando l'impostazione e `entrypoint` rendendola dipendente da `DockerDevelopmentMode` . Ad esempio, se è necessario configurare un certificato solo **in** modalità veloce eseguendo , ma non in modalità normale, è possibile aggiungere il codice seguente `update-ca-certificates` solo in  *docker-compose.vs.debug.yml*: 

```yml
services:
  webapplication1:
    entrypoint: "sh -c 'update-ca-certificates && tail -f /dev/null'"
    labels:
      ...
```

## <a name="next-steps"></a>Passaggi successivi

Per informazioni sulle proprietà di MSBuild in generale, vedere [Proprietà di MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Vedi anche

[Proprietà di compilazione di Strumenti contenitore](container-msbuild-properties.md)

[Impostazioni di avvio di Strumenti contenitore](container-launch-settings.md)

[Gestire i profili di avvio Docker Compose in Visual Studio](launch-profiles.md)

[Proprietà riservate e note MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
