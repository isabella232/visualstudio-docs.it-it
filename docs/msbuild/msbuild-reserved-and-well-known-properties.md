---
title: Proprietà riservate e note MSBuild | Microsoft Docs
description: Informazioni sulle proprietà riservate e note di MSBuild, proprietà predefinite che archiviano informazioni sul file di progetto e sui file binari di MSBuild.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e2edfd4b9391beed5c379817c55871759ff02eec
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384928"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>Proprietà riservate e note MSBuild

MSBuild fornisce un set di proprietà predefinite che archiviano informazioni sul file di progetto e sui file binari di MSBuild. Queste proprietà vengono valutate nello stesso modo delle altre proprietà di MSBuild. Ad esempio, per usare la proprietà `MSBuildProjectFile`, è necessario digitare `$(MSBuildProjectFile)`.

 MSBuild usa i valori indicati nella tabella seguente per predefinire le proprietà riservate e quelle note. L'override può essere eseguito solo per le proprietà note usando proprietà globali, proprietà di ambiente con nomi identici o proprietà dichiarate nel file di progetto.

## <a name="reserved-and-well-known-properties"></a>Proprietà riservate e note

La tabella in questa sezione mostra le proprietà predefinite di MSBuild. La colonna di esempio nella tabella è correlata al file di progetto di esempio seguente, che si presuppone si trovi in e mostra i valori di queste proprietà quando si accede al file di progetto, quando MSBuild viene richiamato senza opzioni speciali della riga di comando, con una build di anteprima di `C:\Source\Repos\ConsoleApp1\ConsoleApp1` Visual Studio 2019 versione 16.7 installata.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

| Proprietà | Riservata o nota | Descrizione | Esempio |
|----------------------------------|------------------------| - | - |
| `MSBuildBinPath` | Riservato | Percorso assoluto della cartella in cui si trovano i file binari di MSBuild attualmente in uso, ad esempio *\\ \<versionNumber> C:\Windows\Microsoft.Net\Framework*. Questa proprietà è utile se è necessario fare riferimento ai file nella directory MSBuild.<br /><br /> Non includere la barra rovesciata finale in questa proprietà. | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild\Current\Bin` |
| `MSBuildExtensionsPath` | Nota | Introdotta in .NET Framework 4: nessuna differenza tra i valori predefiniti di `MSBuildExtensionsPath` e `MSBuildExtensionsPath32`. È possibile impostare la variabile di ambiente `MSBUILDLEGACYEXTENSIONSPATH` su un valore non Null per abilitare il comportamento del valore predefinito di `MSBuildExtensionsPath` nelle versioni precedenti.<br /><br /> In .NET Framework 3.5 e versioni precedenti il valore predefinito di `MSBuildExtensionsPath` fa riferimento al percorso della sottocartella MSBuild nella cartella *\Programmi\\* o *\Programmi (x86)*, in base al numero di bit del processo corrente. Ad esempio, per un processo a 32 bit in un computer a 64 bit, la proprietà fa riferimento alla cartella *\Programmi (x86)*. Per un processo a 64 bit in un computer a 64 bit, questa proprietà fa riferimento alla cartella *\Programmi*.<br /><br /> Non includere la barra rovesciata finale in questa proprietà.<br /><br /> Questo percorso è ideale per contenere i file di destinazione personalizzati. È ad esempio possibile installare i file di destinazione in *\Programmi\MSBuild\MyFiles\Northwind.targets*, quindi importarli nei file di progetto usando il codice XML seguente:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>` | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild`|
| `MSBuildExtensionsPath32` | Nota | Percorso della sottocartella MSBuild nella *cartella \Programmi* o *\Programmi (x86).* Il percorso fa sempre riferimento alla cartella *\Programmi (x86)* per un computer a 32 bit e alla cartella *\Programmi* per un computer a 64 bit.". Vedere anche `MSBuildExtensionsPath` e `MSBuildExtensionsPath64`.<br /><br /> Non includere la barra rovesciata finale in questa proprietà. | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild`|
| `MSBuildExtensionsPath64` | Nota | Percorso della sottocartella MSBuild nella *cartella \Programmi.* Per un computer a 64 bit, questo percorso fa sempre riferimento alla cartella *\Programmi*. Per un computer a 32 bit, questo percorso è vuoto. Vedere anche `MSBuildExtensionsPath` e `MSBuildExtensionsPath32`.<br /><br /> Non includere la barra rovesciata finale in questa proprietà. | `C:\Program Files\MSBuild`|
| `MSBuildInteractive` | Riservato | `true` se MSBuild viene eseguito in modo interattivo, consentendo l'input dell'utente. Questa impostazione è controllata `-interactive` dall'opzione della riga di comando . | `false` |
| `MSBuildLastTaskResult` | Riservato | `true` se l'attività precedente è stata completata senza errori (anche se erano presenti avvisi) o `false` se l'attività precedente ha generato errori. In genere, quando si verifica un errore in un'attività, l'errore è l'ultimo elemento che si verifica nel progetto. Pertanto, il valore di questa proprietà non è mai `false`, tranne negli scenari seguenti:<br /><br /> - Quando l'attributo `ContinueOnError` dell'[elemento Task (MSBuild)](../msbuild/task-element-msbuild.md) è impostato su `WarnAndContinue` (o `true`) o su `ErrorAndContinue`.<br /><br /> - Quando `Target` ha un [elemento OnError (MSBuild)](../msbuild/onerror-element-msbuild.md) come elemento figlio. | `true` |
| `MSBuildNodeCount` | Riservato | Numero massimo di processi simultanei usati durante la compilazione. Si tratta del valore specificato per **-maxcpucount** nella riga di comando. Se l'opzione **-maxcpucount** è stata specificata senza un valore, `MSBuildNodeCount` specifica il numero di processori nel computer. Per altre informazioni, vedere [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md) e [Compilazione di più progetti in parallelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md). | 1 |
| `MSBuildProgramFiles32` | Riservato | Percorso della cartella del programma a 32 bit, ad esempio *C:\Programmi (x86)*.<br /><br /> Non includere la barra rovesciata finale in questa proprietà. | `C:\Program Files (x86)`|
| `MSBuildProjectDefaultTargets` | Riservato | L'elenco completo delle destinazioni specificate nell'attributo `DefaultTargets` dell'elemento `Project`. L'elemento `Project` seguente conterrebbe, ad esempio, una proprietà `MSBuildDefaultTargets` con valore `A;B;C`:<br /><br /> `<Project DefaultTargets="A;B;C" >` | `Build`|
| `MSBuildProjectDirectory` | Riservato | Percorso assoluto della directory in cui si trova il file di progetto, ad esempio *C:\MyCompany\MyProduct*.<br /><br /> Non includere la barra rovesciata finale in questa proprietà. | `C:\Source\Repos\ConsoleApp1\ConsoleApp1` |
| `MSBuildProjectDirectoryNoRoot` | Riservato | Il valore della proprietà `MSBuildProjectDirectory`, esclusa l'unità radice.<br /><br /> Non includere la barra rovesciata finale in questa proprietà. | `Source\Repos\ConsoleApp1\ConsoleApp1`|
| `MSBuildProjectExtension` | Riservato | Estensione di file del file di progetto, incluso il punto. ad esempio. *proj*. | `.csproj`|
| `MSBuildProjectFile` | Riservato | Nome file completo del progetto, inclusa l'estensione del nome file, ad esempio *MyApp.proj*. | `ConsoleApp1.csproj`|
| `MSBuildProjectFullPath` | Riservato | Percorso assoluto e nome file completo del progetto, inclusa l'estensione del nome file, ad esempio *C:\MyCompany\MyProduct\MyApp.proj*. | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\ConsoleApp1.csproj`|
| `MSBuildProjectName` | Riservato | Nome file del file di progetto senza l'estensione, ad esempio *MyApp*. | `ConsoleApp1` |
| `MSBuildRuntimeType` | Riservato | Il tipo di runtime che è attualmente in esecuzione. Introdotto in MSBuild 15. Il valore può essere indefinito (prima di MSBuild 15), che indica che MSBuild è in esecuzione nel .NET Framework desktop, a indicare che MSBuild è in esecuzione `Full` in .NET Core (ad esempio in ) o che MSBuild è in esecuzione in `Core` `dotnet build` `Mono` Mono. | `Full` |
| `MSBuildStartupDirectory` | Riservato | Percorso assoluto della cartella in cui viene chiamato MSBuild. Usando questa proprietà, è possibile compilare tutti gli elementi al di sotto di un punto specifico in un albero di progetto senza creare file con estensione *\<dirs> proj* in ogni directory. È invece presente un solo progetto, ad esempio *c:\traversal.proj*, come illustrato di seguito:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Per compilare a un punto qualsiasi dell'albero, digitare:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Non includere la barra rovesciata finale in questa proprietà. | `c:\Source\Repos\ConsoleApp1` |
| `MSBuildThisFile` | Riservato | Il nome file e la parte dell'estensione di `MSBuildThisFileFullPath`. | `ConsoleApp1.csproj` |
| `MSBuildThisFileDirectory` | Riservato | La parte di directory di `MSBuildThisFileFullPath`.<br /><br /> Includere la barra rovesciata finale nel percorso. | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\` |
| `MSBuildThisFileDirectoryNoRoot` | Riservato | La parte di directory di `MSBuildThisFileFullPath`, esclusa l'unità radice.<br /><br /> Includere la barra rovesciata finale nel percorso. | `Source\Repos\ConsoleApp1\ConsoleApp1\` |
| `MSBuildThisFileExtension` | Riservato | La parte di estensione del nome file di `MSBuildThisFileFullPath`. | `.csproj` |
| `MSBuildThisFileFullPath` | Riservato | Percorso assoluto del file di progetto o di destinazioni che contiene la destinazione in esecuzione.<br /><br /> Suggerimento: è possibile specificare un percorso relativo in un file di destinazioni che sia relativo al file di destinazioni e non al file di progetto originale. | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\ConsoleApp1.csproj` |
| `MSBuildThisFileName` | Riservato | La parte di nome file di `MSBuildThisFileFullPath`, senza l'estensione. | `ConsoleApp1` |
| `MSBuildToolsPath` | Riservato | Percorso di installazione della versione di MSBuild associata al valore di `MSBuildToolsVersion` .<br /><br /> Non includere la barra rovesciata finale nel percorso.<br /><br /> Questa proprietà non può essere sottoposta a override. | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild\Current\Bin` |
| `MSBuildToolsVersion` | Riservato | Versione del set di strumenti di MSBuild usato per compilare il progetto.<br /><br /> Nota: un set di strumenti di MSBuild è costituito da attività, destinazioni e strumenti usati per compilare un'applicazione. Gli strumenti includono compilatori come *csc.exe* e *vbc.exe*. Per altre informazioni, vedere [Set di strumenti (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)e [Configurazioni standard e personalizzate del set di strumenti.](../msbuild/standard-and-custom-toolset-configurations.md) | `Current` |
| `MSBuildVersion` | Riservato | Versione di MSBuild usata per compilare il progetto. <br /><br/> Questa proprietà non può essere sottoposta a override. In caso contrario, viene restituito il messaggio di errore `MSB4004 - The 'MSBuildVersion' property is reserved, and can not be modified.`. | 16.11.0 |
| `MSBuildAssemblyVersion` | Riservato | Versione degli assembly MSBuild usati per compilare il progetto. | 16,0 |
| `MSBuildFileVersion` | Riservato | Versione in 4 parti degli assembly MSBuild usata per compilare il progetto. | 16.11.0.30701 |
| `MSBuildSemanticVersion` | Riservato | Versione completa 2.0 degli assembly MSBuild usati per compilare il progetto. | 16.11.0-preview-21302-05+5e37cc992 |

## <a name="names-that-conflict-with-msbuild-elements"></a>Nomi in conflitto con gli elementi di MSBuild

Oltre a quanto sopra, i nomi corrispondenti a elementi del linguaggio MSBuild non possono essere usati per proprietà, elementi o metadati di elementi definiti dall'utente:

* VisualStudioProject
* Destinazione
* PropertyGroup
* Output
* ItemGroup
* UsingTask
* ProjectExtensions
* OnError
* ImportGroup
* Choose
* Se
* Otherwise

## <a name="see-also"></a>Vedi anche

- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)

- [proprietà di MSBuild](../msbuild/msbuild-properties.md)
