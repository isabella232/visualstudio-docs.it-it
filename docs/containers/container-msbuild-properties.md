---
title: Visual Studio Proprietà di compilazione di Strumenti contenitore
author: ghogen
description: Informazioni su come modificare le proprietà di compilazione di Strumenti contenitore per personalizzare Visual Studio compilazione ed esecuzione di un progetto contenitore.
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-container-tools
ms.topic: reference
ms.openlocfilehash: b284296e4f7bc0f2d641e3094717f95161aef2d7
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631764"
---
# <a name="container-tools-build-properties"></a>Proprietà di compilazione di Strumenti contenitore

È possibile personalizzare la Visual Studio compila i progetti contenitore impostando le proprietà MSBuild per compilare il progetto. Ad esempio, è possibile modificare il nome del Dockerfile, specificare tag ed etichette per le immagini, fornire argomenti aggiuntivi passati ai comandi Docker e controllare se Visual Studio esegue determinate ottimizzazioni delle prestazioni, ad esempio la compilazione all'esterno dell'ambiente contenitore. È anche possibile impostare le proprietà di debug, ad esempio il nome del file eseguibile da avviare e gli argomenti della riga di comando da fornire.

Per impostare il valore di una proprietà, modificare il file di progetto. Si supponga, ad esempio, che il dockerfile sia *denominato MyDockerfile*. È possibile impostare la `DockerfileFile` proprietà nel file di progetto come indicato di seguito.

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

È possibile aggiungere l'impostazione della proprietà a un elemento esistente oppure, se non ce `PropertyGroup` n'è uno, creare un nuovo `PropertyGroup` elemento.

La tabella seguente illustra le proprietà MSBuild disponibili per i progetti contenitore. La NuGet del pacchetto si applica a [Microsoft.VisualStudio.Azure.Containers.Tools.Targets.](https://www.nuget.org/packages/Microsoft.VisualStudio.Azure.Containers.Tools.Targets/)

| Nome proprietà | Descrizione | Valore predefinito  | Versione del pacchetto NuGet|
|---------------|-------------|----------------|----------------------|
| ContainerDevelopmentMode | Controlla se l'ottimizzazione "build-on-host" ("debug in modalità rapida") è abilitata.  I valori consentiti **sono Fast** e **Regular.** | Veloce |1.0.1872750 o versione più recente|
| ContainerVsDbgPath | Percorso del debugger VSDBG. | `%USERPROFILE%\vsdbg\vs2017u5` |1.0.1985401 o versione più recente|
| DockerDebuggeeArguments | Durante il debug, al debugger viene richiesto di passare questi argomenti all'eseguibile avviato. | Non applicabile ai ASP.NET .NET Framework progetto |1.7.8 o versione più recente|
| DockerDebuggeeProgram | Durante il debug, al debugger viene richiesto di avviare questo eseguibile. | Per i progetti .NET Core: dotnet, ASP.NET .NET Framework progetti: Non applicabile (IIS viene sempre usato) |1.7.8 o versione più recente|
| DockerDebuggeeKillProgram | Questo comando viene usato per elaborare il processo in esecuzione in un contenitore. | Non applicabile ai ASP.NET .NET Framework progetto |1.7.8 o versione più recente|
| DockerDebuggeeWorkingDirectory | Durante il debug, al debugger viene richiesto di usare questo percorso come directory di lavoro. | C:\app (Windows) o /app (Linux) |1.7.8 o versione più recente|
| DockerDefaultTargetOS | Sistema operativo di destinazione predefinito usato durante la compilazione dell'immagine Docker. | Impostare in base Visual Studio. |1.0.1985401 o versione più recente|
| DockerImageLabels | Set predefinito di etichette applicate all'immagine Docker. | com.microsoft.created-by=visual-studio;com.microsoft.visual-studio.project-name=$(MSBuildProjectName) |1.5.4 o versione più recente|
| DockerFastModeProjectMountDirectory|In **modalità veloce** questa proprietà controlla dove la directory di output del progetto è montata su volume nel contenitore in esecuzione.|C:\app (Windows) o /app (Linux)|1.9.2 o versione più recente|
| DockerfileBuildArguments | Argomenti aggiuntivi passati al [comando di compilazione Docker.](https://docs.docker.com/engine/reference/commandline/build/) | Non applicabile. |1.0.1872750 o versione più recente|
| DockerfileContext | Contesto predefinito usato durante la compilazione dell'immagine Docker, come percorso relativo a Dockerfile. | Impostare in base Visual Studio. |1.0.1872750 o versione più recente|
| DockerfileFastModeStage | Fase Dockerfile (ovvero destinazione) da usare quando si compila l'immagine in modalità di debug. | Prima fase trovata nel Dockerfile (base) |
| DockerfileFile | Descrive il Dockerfile predefinito che verrà usato per compilare/eseguire il contenitore per il progetto. Può trattarsi anche di un percorso. | Dockerfile |1.0.1872750 o versione più recente|
| DockerfileRunArguments | Argomenti aggiuntivi passati al [comando docker run.](https://docs.docker.com/engine/reference/commandline/run/) | Non applicabile. |1.0.1872750 o versione più recente|
| DockerfileRunEnvironmentFiles | Elenco delimitato da punto e virgola dei file di ambiente applicati durante l'esecuzione di Docker. | Non applicabile. |1.0.1872750 o versione più recente|
| DockerfileTag | Tag che verrà usato durante la compilazione dell'immagine Docker. Nel debug viene aggiunto un :d ev al tag . | Nome dell'assembly dopo l'stripping di caratteri non alfanumerici con le regole seguenti: <br/> Se il tag risultante è tutto numerico, "image" viene inserito come prefisso (ad esempio, image2314) <br/> Se il tag risultante è una stringa vuota, come tag viene usato "image". |1.0.1872750 o versione più recente|

## <a name="example"></a>Esempio

Il file di progetto seguente mostra esempi di alcune di queste impostazioni.

```xml
 <Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <UserSecretsId>feae72bf-2368-4487-b6c6-546c19338cb1</UserSecretsId>
    <DockerDefaultTargetOS>Linux</DockerDefaultTargetOS>
    <!-- In CI/CD scenarios, you might need to change the context. By default, Visual Studio uses the
         folder above the Dockerfile. The path is relative to the Dockerfile, so here the context is
         set to the same folder as the Dockerfile. -->
    <DockerfileContext>.</DockerfileContext>
    <!-- Set `docker run` arguments to mount a volume -->
    <DockerfileRunArguments>-v $(pwd)/host-folder:/container-folder:ro</DockerfileRunArguments>
    <!-- Set `docker build` arguments to add a custom tag -->
    <DockerfileBuildArguments>-t contoso/front-end:v2.0</DockerfileBuildArguments>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.VisualStudio.Azure.Containers.Tools.Targets" Version="1.10.6" />
  </ItemGroup>

</Project>
```

## <a name="next-steps"></a>Passaggi successivi

Per informazioni sulle proprietà MSBuild in generale, vedere MSBuild [proprietà](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Vedi anche

[Docker Compose proprietà di compilazione](docker-compose-properties.md)

[Impostazioni di avvio di Strumenti contenitore](container-launch-settings.md)

[Proprietà riservate e note MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
