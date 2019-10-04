---
title: Proprietà di compilazione degli strumenti contenitore di Visual Studio
author: ghogen
description: Panoramica del processo di compilazione degli strumenti contenitore
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 987d358abcccadf36d15593722ff55ba4b879d03
ms.sourcegitcommit: 6ae0a289f1654dec63b412bfa22035511a2ef5ad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950695"
---
# <a name="container-tools-build-properties"></a>Proprietà di compilazione degli strumenti contenitore

È possibile personalizzare il modo in cui Visual Studio compila i progetti contenitore impostando le proprietà utilizzate da MSBuild per compilare il progetto. Ad esempio, è possibile modificare il nome del Dockerfile, specificare tag ed etichette per le immagini, fornire argomenti aggiuntivi passati ai comandi di Docker e controllare se Visual Studio esegue determinate ottimizzazioni delle prestazioni, ad esempio la compilazione all'esterno del ambiente contenitore. È anche possibile impostare le proprietà di debug, ad esempio il nome del file eseguibile da avviare e gli argomenti della riga di comando da fornire.

Per impostare il valore di una proprietà, modificare il file di progetto. Si supponga, ad esempio, che il Dockerfile sia denominato *MyDockerfile*. È possibile impostare la proprietà `DockerfileFile` nel file di progetto come indicato di seguito.

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

È possibile aggiungere l'impostazione della proprietà a un elemento `PropertyGroup` esistente o, se non ne esiste uno, creare un nuovo elemento `PropertyGroup`.

La tabella seguente illustra le proprietà MSBuild disponibili per i progetti contenitore. La versione del pacchetto NuGet si applica a [Microsoft. VisualStudio. Azure. container. Tools. targets](https://www.nuget.org/packages/Microsoft.VisualStudio.Azure.Containers.Tools.Targets/).

| Nome proprietà | Descrizione | Valore predefinito  | Versione del pacchetto NuGet|
|---------------|-------------|----------------|----------------------|
| ContainerDevelopmentMode | Controlla se è abilitata l'ottimizzazione "compilazione su host" (debug in modalità rapida).  I valori consentiti sono **veloce** e **normale**. | Fast |1.0.1872750 o versione successiva|
| ContainerVsDbgPath | Percorso del debugger VSDBG. | `%USERPROFILE%\vsdbg\vs2017u5` |1.0.1985401 o versione successiva|
| DockerDebuggeeArguments | Quando si esegue il debug, al debugger viene richiesto di passare questi argomenti all'eseguibile avviato. | Non applicabile ai progetti ASP.NET .NET Framework |1.7.8 o versione successiva|
| DockerDebuggeeProgram | Quando si esegue il debug, al debugger viene richiesto di avviare questo eseguibile. | Per i progetti .NET Core: dotnet, ASP.NET .NET Framework projects: Non applicabile (IIS viene sempre usato) |1.7.8 o versione successiva|
| DockerDebuggeeKillProgram | Questo comando viene usato per terminare il processo in esecuzione in un contenitore. | Non applicabile ai progetti ASP.NET .NET Framework |1.7.8 o versione successiva|
| DockerDebuggeeWorkingDirectory | Quando si esegue il debug, al debugger viene richiesto di utilizzare questo percorso come directory di lavoro. | C:\app (Windows) o/app (Linux) |1.7.8 o versione successiva|
| DockerDefaultTargetOS | Sistema operativo di destinazione predefinito usato durante la compilazione dell'immagine docker. | Impostata da Visual Studio. |1.0.1985401 o versione successiva|
| DockerImageLabels | Set predefinito di etichette applicato all'immagine docker. | com. Microsoft. created-by = Visual-Studio; com. Microsoft. Visual-Studio. Project-Name = $ (MSBuildProjectName) |1.5.4 o versione successiva|
| DockerFastModeProjectMountDirectory|In **modalità rapida**questa proprietà controlla il punto in cui la directory di output del progetto viene montata sul volume nel contenitore in esecuzione.|C:\app (Windows) o/app (Linux)|1.9.2 o versione successiva|
| DockerfileBuildArguments | Argomenti aggiuntivi passati al comando di compilazione docker. | Non applicabile. |1.0.1872750 o versione successiva|
| DockerfileContext | Contesto predefinito usato durante la compilazione dell'immagine docker. | Impostata da Visual Studio. |1.0.1872750 o versione successiva|
| DockerfileFastModeStage | Fase Dockerfile (ovvero destinazione) da utilizzare quando si compila l'immagine in modalità di debug. | Prima fase trovata in Dockerfile (base) |
| DockerfileFile | Descrive il valore predefinito di Dockerfile che verrà usato per compilare o eseguire il contenitore per il progetto. Può trattarsi anche di un percorso. | Dockerfile |1.0.1872750 o versione successiva|
| DockerfileRunArguments | Argomenti aggiuntivi passati al comando Docker Run. | Non applicabile. |1.0.1872750 o versione successiva|
| DockerfileRunEnvironmentFiles | Elenco delimitato da punti e virgola dei file dell'ambiente applicati durante l'esecuzione di Docker. | Non applicabile. |1.0.1872750 o versione successiva|
| DockerfileTag | Tag che verrà usato durante la compilazione dell'immagine docker. Durante il debug, al tag viene aggiunto ":d EV". | Nome dell'assembly dopo la rimozione dei caratteri non alfanumerici con le regole seguenti: <br/> Se il tag risultante è un valore numerico, "image" viene inserito come prefisso, ad esempio image2314 <br/> Se il tag risultante è una stringa vuota, come tag viene usato "image". |1.0.1872750 o versione successiva|

## <a name="next-steps"></a>Passaggi successivi

Per informazioni sulle proprietà di MSBuild in genere, vedere [proprietà di MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Vedere anche

[Proprietà di compilazione Docker Compose](docker-compose-properties.md)

[Impostazioni di avvio degli strumenti contenitore](container-launch-settings.md)

[Proprietà riservate e note MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
