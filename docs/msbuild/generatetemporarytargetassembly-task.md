---
title: Attività GenerateTemporaryTargetAssembly | Microsoft Docs
description: Usare l MSBuild generateTemporaryTargetAssembly per generare un assembly se un progetto fa riferimento a un tipo dichiarato in locale.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- build process [WPF MSBuild], XAML page refers to a locally declared type
- GenerateTemporaryTargetAssembly task [WPF MSBuild]
- GenerateTemporaryTargetAssembly task [WPF MSBuild], parameters
- creating an assembly [WPF MSBuild], XAML page refers to a locally declared type
ms.assetid: 92b6539c-6897-45e0-8989-0c234bbfe782
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 505eb1370dd1ccbcfe782211bf9f1a4e958ef10906da4afcd9c1deb3fa4bf0bd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121443490"
---
# <a name="generatetemporarytargetassembly-task"></a>Attività GenerateTemporaryTargetAssembly

L'attività genera un assembly se almeno una pagina XAML in un progetto fa riferimento a un tipo <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> dichiarato localmente nel progetto. L'assembly generato viene rimosso dopo il completamento del processo di compilazione o in caso di esito negativo del processo.

## <a name="task-parameters"></a>Parametri dell'attività

| Parametro | Descrizione |
|--------------------------| - |
| `AssemblyName` | Parametro **String** obbligatorio.<br /><br /> Specifica il nome breve dell'assembly generato per un progetto ed è anche il nome dell'assembly di destinazione generato temporaneamente. Ad esempio, se un progetto genera un file eseguibile Windows il cui nome èWinExeAssembly.exe *,* il **parametro AssemblyName** ha il valore **WinExeAssembly**. |
| `CompileTargetName` | Parametro **String** obbligatorio.<br /><br /> Specifica il nome della destinazione MSBuild utilizzata per generare assembly dai file di codice sorgente. Il valore tipico per **CompileTargetName** è **CoreCompile**. |
| `CompileTypeName` | Parametro **String** obbligatorio.<br /><br /> Specifica il tipo di compilazione eseguito dalla destinazione specificata dal parametro **CompileTargetName**. Per la destinazione **CoreCompile** questo valore è **Compile**. |
| `CurrentProject` | Parametro **String** obbligatorio.<br /><br /> Specifica il percorso completo del file MSBuild progetto per il progetto che richiede un assembly di destinazione temporaneo. |
| `GeneratedCodeFiles` | Parametro **ITaskItem[]** facoltativo.<br /><br /> Specifica l'elenco di file di codice gestito specifici del linguaggio generati dall'attività [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md). |
| `IntermediateOutputPath` | Parametro **String** obbligatorio.<br /><br /> Specifica la directory in cui viene generato l'assembly di destinazione temporaneo. |
| `MSBuildBinPath` | Parametro **String** obbligatorio.<br /><br /> Specifica il percorso di *MSBuild.exe*, necessario per compilare l'assembly di destinazione temporaneo. |
| `ReferencePath` | Parametro **ITaskItem[]** facoltativo.<br /><br /> Specifica un elenco di assembly, per percorso e nome file, a cui fanno riferimento i tipi compilati nell'assembly di destinazione temporaneo. |
| `ReferencePathTypeName` | Parametro **String** obbligatorio.<br /><br /> Specifica il parametro usato dal parametro di destinazione della compilazione (**CompileTargetName**), che specifica l'elenco di riferimenti ad assembly (**ReferencePath**). Il valore appropriato è **ReferencePath**. |

## <a name="remarks"></a>Commenti

Il primo passaggio di compilazione del markup, eseguito da [MarkupCompilePass1,](../msbuild/markupcompilepass1-task.md)compila i file XAML in formato binario. Di conseguenza, il compilatore necessita di un elenco degli assembly a cui si fa riferimento che contengono i tipi usati dai file XAML. Tuttavia, se un file XAML usa un tipo definito nello stesso progetto, un assembly corrispondente per tale progetto non viene creato fino a quando il progetto non viene compilato. Pertanto, non è possibile fornire un riferimento all'assembly durante il primo passaggio di compilazione del markup.

**MarkupCompilePass1** rinvia invece la conversione dei file XAML che contengono riferimenti ai tipi nello stesso progetto in un secondo passaggio di compilazione del markup, eseguito da [MarkupCompilePass2.](../msbuild/markupcompilepass2-task.md) Prima dell'esecuzione di **MarkupCompilePass2**, viene generato un assembly temporaneo Questo assembly contiene i tipi usati dai file XAML il cui passaggio di compilazione del markup è stato posticipato. Un riferimento all'assembly generato viene fornito a **MarkupCompilePass2** quando viene eseguito per consentire la conversione dei file XAML di compilazione posticipata in formato binario.

## <a name="example"></a>Esempio

Nell'esempio seguente viene generato un assembly temporaneo poiché *Page1.xaml* contiene un riferimento a un tipo che si trova nello stesso progetto.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="GenerateTemporaryTargetAssemblyTask">
    <GenerateTemporaryTargetAssembly
      AssemblyName="WPFMSBuildSample"
      CompileTargetName="CoreCompile"
      CompileTypeName="Compile"
      CurrentProject="FullBuild.proj"
      GeneratedCodeFiles="obj\debug\app.g.cs;obj\debug\Page1.g.cs;obj\debug\Page2.g.cs"
      ReferencePath="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll"
      IntermediateOutputPath=".\obj\debug\"
      MSBuildBinPath="$(MSBuildBinPath)"
      ReferencePathTypeName="ReferencePath"/>
  </Target>
</Project>
```

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento su MSBuild WPF](../msbuild/wpf-msbuild-reference.md)
- [Informazioni di riferimento sulle attività](../msbuild/wpf-msbuild-task-reference.md)
- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
- [Creazione di un'applicazione WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Panoramica delle applicazioni browser XAML WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
