---
title: Attività MarkupCompilePass2 | Microsoft Docs
description: Informazioni su come MSBuild usa l'attività MarkupCompilePass2 per eseguire la compilazione del markup del secondo passaggio sui file XAML che fanno riferimento ai tipi nello stesso progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- performing second-pass markup [WPF MSBuild], MarkupCompilePass2 task
- MarkupCompilePass2 task [WPF MSBuild]
- MarkupCompilePass2 task [WPF MSBuild], parameters
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7425e0342974c3b000486f57227f768aac47b9ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966175"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2 (attività)

L' <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> attività esegue la compilazione del markup del secondo passaggio sui file XAML che fanno riferimento ai tipi nello stesso progetto.

## <a name="task-parameters"></a>Parametri dell'attività

| Parametro | Descrizione |
| - | - |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Parametro **booleano** facoltativo.<br /><br /> Specifica se eseguire l'attività in un <xref:System.AppDomain> separato. Se questo parametro restituisce **false**, l'attività viene eseguita in modo analogo a <xref:System.AppDomain> MSBuild e viene eseguita più velocemente. Se il parametro restituisce **true**, l'attività viene eseguita in un secondo <xref:System.AppDomain> isolato da MSBuild ed eseguito più lentamente. |
| `AssembliesGeneratedDuringBuild` | Parametro **String []** facoltativo.<br /><br /> Specifica i riferimenti ad assembly che vengono modificati durante il processo di compilazione. Ad esempio, una soluzione Visual Studio può contenere un progetto che fa riferimento all'output compilato di un altro progetto. In questo caso, l'output compilato del secondo progetto può essere aggiunto a **AssembliesGeneratedDuringBuild**.<br /><br /> Nota: **AssembliesGeneratedDuringBuild** deve contenere riferimenti al set completo di assembly generati da una soluzione di compilazione. |
| `AssemblyName` | Parametro **String** obbligatorio.<br /><br /> Specifica il nome breve dell'assembly generato per un progetto. Se, ad esempio, un progetto genera un eseguibile il cui nome è *WinExeAssembly.exe*, il parametro **AssemblyName** avrà il valore **WinExeAssembly**. |
| `GeneratedBaml` | Parametro di output facoltativo **ITaskItem[]**.<br /><br /> Contiene l'elenco dei file generati nel formato binario XAML. |
| `KnownReferencePaths` | Parametro **String []** facoltativo.<br /><br /> Specifica i riferimenti ad assembly che non vengono mai modificati durante il processo di compilazione. Include gli assembly che si trovano nella Global Assembly Cache (GAC), in una directory di installazione di .NET e così via. |
| `Language` | Parametro **String** obbligatorio.<br /><br /> Specifica il linguaggio gestito supportato dal compilatore. Le opzioni valide sono **C#**, **VB**, **JScript** e **C++**. |
| `LocalizationDirectivesToLocFile` | Parametro **stringa** facoltativo.<br /><br /> Specifica la modalità di generazione delle informazioni di localizzazione per ogni file XAML di origine. Le opzioni valide sono **None**, **CommentsOnly** e **All**. |
| `OutputPath` | Parametro **String** obbligatorio.<br /><br /> Specifica la directory in cui vengono generati i file di formato binario XAML generati. |
| `OutputType` | Parametro **String** obbligatorio.<br /><br /> Specifica il tipo di assembly generato da un progetto. Le opzioni valide sono **winexe**, **exe**, **library** e **netmodule**. |
| `References` | Parametro **ITaskItem []** facoltativo.<br /><br /> Specifica l'elenco di riferimenti da file agli assembly che contengono i tipi utilizzati nei file XAML. Un riferimento è relativo all'assembly generato dall'attività <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly>, che deve essere eseguita prima dell'attività <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>. |
| `RootNamespace` | Parametro **stringa** facoltativo.<br /><br /> Specifica lo spazio dei nomi radice per le classi all'interno del progetto. **RootNamespace** viene utilizzato anche come spazio dei nomi predefinito di un file di codice gestito generato quando il file XAML corrispondente non include l' `x:Class` attributo. |
| `XAMLDebuggingInformation` | Parametro **booleano** facoltativo.<br /><br /> Se è **true**, le informazioni di diagnostica vengono generate e incluse nel codice XAML compilato per facilitare il debug. |

## <a name="remarks"></a>Commenti

Prima di eseguire **MarkupCompilePass2**, è necessario generare un assembly temporaneo che contenga i tipi utilizzati dai file XAML il cui passaggio di compilazione del markup è stato posticipato. L'assembly temporaneo viene generato mediante l'esecuzione dell'attività **GenerateTemporaryTargetAssembly**.

Al momento dell'esecuzione viene fornito un riferimento all'assembly temporaneo generato <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> , consentendo la compilazione in formato binario dei file XAML la cui compilazione è stata rinviata nel primo passaggio di compilazione del markup.

## <a name="example"></a>Esempio

L'esempio seguente visualizza come usare l'attività <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> per eseguire un secondo passaggio di compilazione.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass2"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="MarkupCompilePass2Task">
    <MarkupCompilePass2
      AssemblyName="WPFMSBuildSample"
      Language="C#"
      OutputType="WinExe"
      OutputPath="obj\Debug\"
      References=".\obj\debug\WPFMSBuildSample.exe;c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />
  </Target>
</Project>
```

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento su MSBuild WPF](../msbuild/wpf-msbuild-reference.md)
- [Guida di riferimento alle attività MSBuild WPF](../msbuild/wpf-msbuild-task-reference.md)
- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
- [Riferimenti alle attività MSBuild](../msbuild/msbuild-task-reference.md)
- [Creazione di un'applicazione WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Panoramica delle applicazioni browser XAML WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
