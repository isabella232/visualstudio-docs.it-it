---
title: Proprietà riservate e note MSBuild | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10b38ca4bfc0ea8a326f015228a4152779a41650
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633252"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>Proprietà riservate e note MSBuild

MSBuild fornisce un set di proprietà predefinite che archiviano informazioni sul file di progetto e sui file binari di MSBuild. Queste proprietà vengono valutate nello stesso modo di altre proprietà MSBuild.These properties are evaluated in the same manner as other MSBuild properties. Ad esempio, per usare la proprietà `MSBuildProjectFile`, è necessario digitare `$(MSBuildProjectFile)`.

 MSBuild usa i valori indicati nella tabella seguente per predefinire le proprietà riservate e quelle note. L'override può essere eseguito solo per le proprietà note usando proprietà globali, proprietà di ambiente con nomi identici o proprietà dichiarate nel file di progetto.

## <a name="reserved-and-well-known-properties"></a>Proprietà riservate e note

 Nella tabella seguente vengono descritte le proprietà predefinite di MSBuild.

| Proprietà | Riservata o nota | Descrizione |
|----------------------------------|------------------------| - |
| `MSBuildBinPath` | Riservato | Il percorso assoluto della cartella in cui si trovano i file binari di MSBuild attualmente in uso (ad esempio, *C\\\<>:. * Questa proprietà è utile se è necessario fare riferimento ai file nella directory MSBuild.This property is useful if you have to refer to files in the MSBuild directory.<br /><br /> Non includere la barra rovesciata finale in questa proprietà. |
| `MSBuildExtensionsPath` | Nota | Introdotta in .NET Framework 4: nessuna differenza tra i valori predefiniti di `MSBuildExtensionsPath` e `MSBuildExtensionsPath32`. È possibile impostare la variabile di ambiente `MSBUILDLEGACYEXTENSIONSPATH` su un valore non Null per abilitare il comportamento del valore predefinito di `MSBuildExtensionsPath` nelle versioni precedenti.<br /><br /> In .NET Framework 3.5 e versioni precedenti il valore predefinito di `MSBuildExtensionsPath` fa riferimento al percorso della sottocartella MSBuild nella cartella *\Programmi\\* o *\Programmi (x86)*, in base al numero di bit del processo corrente. Ad esempio, per un processo a 32 bit in un computer a 64 bit, la proprietà fa riferimento alla cartella *\Programmi (x86)*. Per un processo a 64 bit in un computer a 64 bit, questa proprietà fa riferimento alla cartella *\Programmi*.<br /><br /> Non includere la barra rovesciata finale in questa proprietà.<br /><br /> Questo percorso è ideale per contenere i file di destinazione personalizzati. È ad esempio possibile installare i file di destinazione in *\Programmi\MSBuild\MyFiles\Northwind.targets*, quindi importarli nei file di progetto usando il codice XML seguente:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>` |
| `MSBuildExtensionsPath32` | Nota | Il percorso della sottocartella MSBuild nella cartella , *programmi* o *file di programma (x86).* Il percorso fa sempre riferimento alla cartella *\Programmi (x86)* per un computer a 32 bit e alla cartella *\Programmi* per un computer a 64 bit.". Vedere anche `MSBuildExtensionsPath` e `MSBuildExtensionsPath64`.<br /><br /> Non includere la barra rovesciata finale in questa proprietà. |
| `MSBuildExtensionsPath64` | Nota | Il percorso della sottocartella MSBuild nella cartella *Programmi.* Per un computer a 64 bit, questo percorso fa sempre riferimento alla cartella *\Programmi*. Per un computer a 32 bit, questo percorso è vuoto. Vedere anche `MSBuildExtensionsPath` e `MSBuildExtensionsPath32`.<br /><br /> Non includere la barra rovesciata finale in questa proprietà. |
| `MSBuildInteractive` | Riservato | `true`se MSBuild è in esecuzione in modo interattivo, consentendo l'input dell'utente. Questa impostazione è `-interactive` controllata dall'opzione della riga di comando. |
| `MSBuildLastTaskResult` | Riservato | `true` se l'attività precedente è stata completata senza errori (anche se erano presenti avvisi) o `false` se l'attività precedente ha generato errori. In genere, quando si verifica un errore in un'attività, l'errore è l'ultimo elemento che si verifica nel progetto. Pertanto, il valore di questa proprietà non è mai `false`, tranne negli scenari seguenti:<br /><br /> - Quando l'attributo `ContinueOnError` dell'[elemento Task (MSBuild)](../msbuild/task-element-msbuild.md) è impostato su `WarnAndContinue` (o `true`) o su `ErrorAndContinue`.<br /><br /> - Quando `Target` ha un [elemento OnError (MSBuild)](../msbuild/onerror-element-msbuild.md) come elemento figlio. |
| `MSBuildNodeCount` | Riservato | Numero massimo di processi simultanei usati durante la compilazione. Si tratta del valore specificato per **-maxcpucount** nella riga di comando. Se l'opzione **-maxcpucount** è stata specificata senza un valore, `MSBuildNodeCount` specifica il numero di processori nel computer. Per altre informazioni, vedere [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md) e [Compilazione di più progetti in parallelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md). |
| `MSBuildProgramFiles32` | Riservato | Percorso della cartella del programma a 32 bit, ad esempio *C:\Programmi (x86)*.<br /><br /> Non includere la barra rovesciata finale in questa proprietà. |
| `MSBuildProjectDefaultTargets` | Riservato | L'elenco completo delle destinazioni specificate nell'attributo `DefaultTargets` dell'elemento `Project`. L'elemento `Project` seguente conterrebbe, ad esempio, una proprietà `MSBuildDefaultTargets` con valore `A;B;C`:<br /><br /> `<Project DefaultTargets="A;B;C" >` |
| `MSBuildProjectDirectory` | Riservato | Percorso assoluto della directory in cui si trova il file di progetto, ad esempio *C:\MyCompany\MyProduct*.<br /><br /> Non includere la barra rovesciata finale in questa proprietà. |
| `MSBuildProjectDirectoryNoRoot` | Riservato | Il valore della proprietà `MSBuildProjectDirectory`, esclusa l'unità radice.<br /><br /> Non includere la barra rovesciata finale in questa proprietà. |
| `MSBuildProjectExtension` | Riservato | L'estensione del file di progetto, incluso il punto; ad esempio, *.proj*. |
| `MSBuildProjectFile` | Riservato | Nome file completo del progetto, inclusa l'estensione del nome file, ad esempio *MyApp.proj*. |
| `MSBuildProjectFullPath` | Riservato | Percorso assoluto e nome file completo del progetto, inclusa l'estensione del nome file, ad esempio *C:\MyCompany\MyProduct\MyApp.proj*. |
| `MSBuildProjectName` | Riservato | Nome file del file di progetto senza l'estensione, ad esempio *MyApp*. |
| `MSBuildRuntimeType` | Riservato | Il tipo di runtime che è attualmente in esecuzione. Introdotto in MSBuild 15. Il valore potrebbe non essere definito (prima di MSBuild `Full` 15), che indica `Core` che MSBuild è in esecuzione sul desktop `dotnet build`.NET Framework, a indicare che MSBuild è in esecuzione in .NET Core (ad esempio in ) o `Mono` che indica che MSBuild è in esecuzione su Mono. |
| `MSBuildStartupDirectory` | Riservato | Percorso assoluto della cartella in cui viene chiamato MSBuild. Utilizzando questa proprietà, è possibile compilare tutti gli elementi al di sotto di un punto specifico in un albero del progetto senza creare * \<dirs> file con estensione proj* in ogni directory. È invece presente un solo progetto, ad esempio *c:\traversal.proj*, come illustrato di seguito:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Per compilare a un punto qualsiasi dell'albero, digitare:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Non includere la barra rovesciata finale in questa proprietà. |
| `MSBuildThisFile` | Riservato | Il nome file e la parte dell'estensione di `MSBuildThisFileFullPath`. |
| `MSBuildThisFileDirectory` | Riservato | La parte di directory di `MSBuildThisFileFullPath`.<br /><br /> Includere la barra rovesciata finale nel percorso. |
| `MSBuildThisFileDirectoryNoRoot` | Riservato | La parte di directory di `MSBuildThisFileFullPath`, esclusa l'unità radice.<br /><br /> Includere la barra rovesciata finale nel percorso. |
| `MSBuildThisFileExtension` | Riservato | La parte di estensione del nome file di `MSBuildThisFileFullPath`. |
| `MSBuildThisFileFullPath` | Riservato | Percorso assoluto del file di progetto o di destinazioni che contiene la destinazione in esecuzione.<br /><br /> Suggerimento: è possibile specificare un percorso relativo in un file di destinazioni che sia relativo al file di destinazioni e non al file di progetto originale. |
| `MSBuildThisFileName` | Riservato | La parte di nome file di `MSBuildThisFileFullPath`, senza l'estensione. |
| `MSBuildToolsPath` | Riservato | Percorso di installazione della versione di MSBuild associata al valore di `MSBuildToolsVersion`.<br /><br /> Non includere la barra rovesciata finale nel percorso.<br /><br /> Questa proprietà non può essere sottoposta a override. |
| `MSBuildToolsVersion` | Riservato | Versione del set di strumenti MSBuild utilizzato per compilare il progetto.<br /><br /> Nota: un set di strumenti MSBuild è costituito da attività, destinazioni e strumenti utilizzati per compilare un'applicazione. Gli strumenti includono compilatori come *csc.exe* e *vbc.exe*. Per ulteriori informazioni, vedere Set di strumenti [(ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)e [Configurazioni standard e personalizzate](../msbuild/standard-and-custom-toolset-configurations.md)del set di strumenti . |
| `MSBuildVersion` | Riservato | Versione di MSBuild utilizzata per compilare il progetto. <br /><br/> Questa proprietà non può essere sottoposta a override. In caso contrario, viene restituito il messaggio di errore `MSB4004 - The 'MSBuildVersion' property is reserved, and can not be modified.`. |

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

## <a name="see-also"></a>Vedere anche

- [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)

- [Proprietà di MSBuild](../msbuild/msbuild-properties.md)
