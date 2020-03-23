---
title: Proprietà di compilazione di Visual Studio Container Tools
author: ghogen
description: Panoramica del processo di compilazione degli strumenti contenitore
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 987d358abcccadf36d15593722ff55ba4b879d03
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "71950695"
---
# <a name="container-tools-build-properties"></a>Proprietà di compilazione degli strumenti contenitoreContainer Tools build properties

È possibile personalizzare la modalità di compilazione dei progetti contenitore in Visual Studio impostando le proprietà utilizzate da MSBuild per compilare il progetto. Ad esempio, è possibile modificare il nome del Dockerfile, specificare tag ed etichette per le immagini, fornire argomenti aggiuntivi passati ai comandi Docker e controllare se Visual Studio esegue determinate ottimizzazioni delle prestazioni, ad esempio la compilazione all'esterno del nell'ambiente contenitore. È inoltre possibile impostare le proprietà di debug, ad esempio il nome dell'eseguibile da avviare e gli argomenti della riga di comando da fornire.

Per impostare il valore di una proprietà, modificare il file di progetto. Si supponga, ad esempio, che il Dockerfile sia denominato *MyDockerfile*. È possibile `DockerfileFile` impostare la proprietà nel file di progetto come indicato di seguito.

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

È possibile aggiungere l'impostazione della proprietà a un elemento `PropertyGroup` esistente `PropertyGroup` o, se non è presente, creare un nuovo elemento.

Nella tabella seguente vengono illustrate le proprietà MSBuild disponibili per i progetti contenitore. La versione del pacchetto NuGet si applica a [Microsoft.VisualStudio.Azure.Containers.Tools.Targets](https://www.nuget.org/packages/Microsoft.VisualStudio.Azure.Containers.Tools.Targets/).

| Nome proprietà | Descrizione | Valore predefinito  | Versione del pacchetto NuGet|
|---------------|-------------|----------------|----------------------|
| ContainerDevelopmentMode (Modalità SviluppoContenitore) | Controlla se l'ottimizzazione "build-on-host" (Velocità rapida) è abilitata.  I valori consentiti sono **Veloce** e **Regolare**. | Veloce |1.0.1872750 o più recente|
| ContainerVsDbgPath (percorso) | Percorso del debugger VSDBG. | `%USERPROFILE%\vsdbg\vs2017u5` |1.0.1985401 o più recente|
| DockerDebuggeeArgumentsDockerDebuggeeArguments | Durante il debug, al debugger viene richiesto di passare questi argomenti all'eseguibile avviato. | Non applicabile ai progetti .NET Framework ASP.NET |1.7.8 o più recente|
| DockerDebuggeeProgrammaProgramma | Durante il debug, al debugger viene richiesto di avviare questo eseguibile. | Per i progetti .NET Core: dotnet, ASP.NET progetti .NET Framework: Non applicabile (IIS viene sempre utilizzato) |1.7.8 o più recente|
| DockerDebuggeeKillProgram | Questo comando viene utilizzato per terminare il processo in esecuzione in un contenitore. | Non applicabile ai progetti .NET Framework ASP.NET |1.7.8 o più recente|
| DockerDebuggeeWorkingDirectory | Durante il debug, al debugger viene richiesto di utilizzare questo percorso come directory di lavoro. | C::app (Windows) o /app (Linux) |1.7.8 o più recente|
| DockerDefaultTargetOS | Sistema operativo di destinazione predefinito utilizzato durante la compilazione dell'immagine Docker. | Impostato da Visual Studio. |1.0.1985401 o più recente|
| DockerImageLabels | Il set predefinito di etichette applicate all'immagine Docker. | com.microsoft.created-by-visual-studio;com.microsoft.visual-studio.project-name |1.5.4 o più recente|
| DockerFastModeProjectMountDirectory|In **modalità veloce**, questa proprietà controlla la posizione in cui la directory di output del progetto è montata sul volume nel contenitore in esecuzione.|C::app (Windows) o /app (Linux)|1.9.2 o più recente|
| DockerfileBuildArguments | Argomenti aggiuntivi passati al comando Docker build. | Non applicabile. |1.0.1872750 o più recente|
| Oggetto DockerfileContext | Contesto predefinito utilizzato durante la compilazione dell'immagine Docker. | Impostato da Visual Studio. |1.0.1872750 o più recente|
| DockerfileFastModeStage | Fase Dockerfile (ovvero destinazione) da utilizzare durante la compilazione dell'immagine in modalità di debug. | Prima fase trovata nel Dockerfile (base) |
| FileDockerfileFile | Viene descritto il dockerfile predefinito che verrà utilizzato per compilare/eseguire il contenitore per il progetto. Questo può essere anche un percorso. | Dockerfile |1.0.1872750 o più recente|
| DockerfileRunArguments | Argomenti aggiuntivi passati al comando Docker run. | Non applicabile. |1.0.1872750 o più recente|
| DockerfileRunEnvironmentFiles | Elenco delimitato da punti e virgola di file di ambiente applicati durante l'esecuzione di Docker. | Non applicabile. |1.0.1872750 o più recente|
| Oggetto DockerfileTag | Tag che verrà utilizzato durante la creazione dell'immagine Docker. Durante il debug, un ":dev" viene aggiunto al tag. | Nome dell'assembly dopo la stripping di caratteri non alfanumerici con le regole seguenti: <br/> Se il tag risultante è tutto numerico, "image" viene inserito come prefisso (ad esempio, image2314) <br/> Se il tag risultante è una stringa vuota, "image" viene utilizzato come tag. |1.0.1872750 o più recente|

## <a name="next-steps"></a>Passaggi successivi

Per informazioni sulle proprietà MSBuild in genere, vedere [Proprietà MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Vedere anche

[Docker Compose proprietà di compilazione](docker-compose-properties.md)

[Impostazioni di avvio degli strumenti contenitore](container-launch-settings.md)

[Proprietà di MSBuild riservate e note](../msbuild/msbuild-reserved-and-well-known-properties.md)
