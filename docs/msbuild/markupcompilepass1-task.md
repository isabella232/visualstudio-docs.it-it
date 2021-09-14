---
title: Attività MarkupCompilePass1 | Microsoft Docs
description: Informazioni su MSBuild'attività MarkupCompilePass1 per convertire i file di progetto XAML non localizzabili in formato binario compilato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- converting XAML to binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], parameters
- converting XAML projects to compiled binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], converting XAML to binary format
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: dba71fed7c4cc248e3e7648f264e3ccd531af5e0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625638"
---
# <a name="markupcompilepass1-task"></a>Attività MarkupCompilePass1

L'attività converte i file di progetto XAML non localizzabili <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> in formato binario compilato.

## <a name="task-parameters"></a>Parametri dell'attività

| Parametro | Descrizione |
| - | - |
| `AllGeneratedFiles` | Parametro di output facoltativo **ITaskItem[]**.<br /><br /> Contiene un elenco completo dei file generati dall'attività <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>. |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Parametro **booleano** facoltativo.<br /><br /> Specifica se eseguire l'attività in un <xref:System.AppDomain> separato. Se questo parametro restituisce **false,** l'attività viene eseguita nello stesso MSBuild <xref:System.AppDomain> e viene eseguita più velocemente. Se il parametro restituisce **true,** l'attività viene eseguita in un secondo isolato dal MSBuild <xref:System.AppDomain> viene eseguito più lentamente. |
| `ApplicationMarkup` | Parametro **ITaskItem[]** facoltativo.<br /><br /> Specifica il nome del file XAML di definizione dell'applicazione. |
| `AssembliesGeneratedDuringBuild` | Parametro **String[]** facoltativo.<br /><br /> Specifica i riferimenti ad assembly che vengono modificati durante il processo di compilazione. Ad esempio, una soluzione Visual Studio può contenere un progetto che fa riferimento all'output compilato di un altro progetto. In questo caso, l'output compilato del secondo progetto può essere aggiunto al parametro **AssembliesGeneratedDuringBuild**.<br /><br /> Nota: il parametro **AssembliesGeneratedDuringBuild** deve contenere riferimenti all'insieme completo di assembly generati da una soluzione di compilazione. |
| `AssemblyName` | Parametro **stringa** obbligatorio.<br /><br /> Specifica il nome breve dell'assembly generato per un progetto. Ad esempio, se un progetto genera un file eseguibile Windows il cui nome è *WinExeAssembly.exe*, il parametro **AssemblyName** ha il valore **WinExeAssembly**. |
| `AssemblyPublicKeyToken` | Parametro **String** facoltativo.<br /><br /> Specifica il token di chiave pubblica per l'assembly. |
| `AssemblyVersion` | Parametro **String** facoltativo.<br /><br /> Specifica il numero di versione dell'assembly. |
| `ContentFiles` | Parametro **ITaskItem[]** facoltativo.<br /><br /> Specifica l'elenco dei file di contenuto separati. |
| `DefineConstants` | Parametro **String** facoltativo.<br /><br /> Specifica che viene mantenuto il valore corrente di **DefineConstants**, che influisce sulla generazione dell'assembly di destinazione; Se questo parametro viene modificato, l'API pubblica nell'assembly di destinazione può essere modificata e la compilazione di file XAML che fanno riferimento a tipi locali potrebbe essere interessata. |
| `ExtraBuildControlFiles` | Parametro **ITaskItem[]** facoltativo.<br /><br /> Specifica un elenco di file che controllano l'attivazione di una ricompilazione durante la riesecuzione dell'attività <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>. La ricompilazione viene attivata in caso di modifica di uno di questi file. |
| `GeneratedBamlFiles` | Parametro di output facoltativo **ITaskItem[]**.<br /><br /> Contiene l'elenco dei file generati in formato binario XAML. |
| `GeneratedCodeFiles` | Parametro di output facoltativo **ITaskItem[]**.<br /><br /> Contiene l'elenco dei file di codice gestito generati. |
| `GeneratedLocalizationFiles` | Parametro di output facoltativo **ITaskItem[]**.<br /><br /> Contiene l'elenco dei file di localizzazione generati per ogni file XAML localizzabile. |
| `HostInBrowser` | Parametro **String** facoltativo.<br /><br /> Specifica se l'assembly generato è un'applicazione browser XAML (XBAP). Le opzioni valide sono **true** e **false**. Se **true**, verrà generato codice per supportare l'hosting del browser. |
| `KnownReferencePaths` | Parametro **String[]** facoltativo.<br /><br /> Specifica i riferimenti ad assembly che non vengono modificati durante il processo di compilazione. Include gli assembly che si trovano nella Global Assembly Cache (GAC), in una directory di installazione di .NET e così via. |
| `Language` | Parametro **String** obbligatorio.<br /><br /> Specifica il linguaggio gestito supportato dal compilatore. Le opzioni valide sono **C#**, **VB**, **JScript** e **C++**. |
| `LanguageSourceExtension` | Parametro **String** facoltativo.<br /><br /> Specifica l'estensione aggiunta all'estensione del file di codice gestito generato:<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> Se il **parametro LanguageSourceExtension** non è impostato con un valore specifico, viene usata l'estensione di file di origine predefinita per un linguaggio: *vb* per Visual Basic, *csharp* per C#. |
| `LocalizationDirectivesToLocFile` | Parametro **String** facoltativo.<br /><br /> Specifica come generare informazioni di localizzazione per ogni file XAML di origine. Le opzioni valide sono **None**, **CommentsOnly** e **All**. |
| `OutputPath` | Parametro **String** obbligatorio.<br /><br /> Specifica la directory in cui vengono generati i file di codice gestito generati e i file di formato binario XAML. |
| `OutputType` | Parametro **String** obbligatorio.<br /><br /> Specifica il tipo di assembly generato da un progetto. Le opzioni valide sono **winexe**, **exe**, **library** e **netmodule**. |
| `PageMarkup` | Parametro **ITaskItem[]** facoltativo.<br /><br /> Specifica un elenco di file XAML da elaborare. |
| `References` | Parametro **ITaskItem[]** facoltativo.<br /><br /> Specifica l'elenco di riferimenti da file ad assembly che contengono i tipi usati nei file XAML. |
| `RequirePass2ForMainAssembly` | Parametro di output **Boolean** facoltativo.<br /><br /> Indica se il progetto contiene file XAML non localizzabili che fanno riferimento a tipi locali incorporati nell'assembly principale. |
| `RequirePass2ForSatelliteAssembly` | Parametro di output **Boolean** facoltativo.<br /><br /> Indica se il progetto contiene file XAML localizzabili che fanno riferimento a tipi locali incorporati nell'assembly principale. |
| `RootNamespace` | Parametro **String** facoltativo.<br /><br /> Specifica lo spazio dei nomi radice per le classi all'interno del progetto. **RootNamespace** viene usato anche come spazio dei nomi predefinito di un file di codice gestito generato quando il file XAML corrispondente non include `x:Class` l'attributo . |
| `SourceCodeFiles` | Parametro **ITaskItem[]** facoltativo.<br /><br /> Specifica l'elenco dei file di codice per il progetto corrente. L'elenco non include file di codice gestito generati specifici del linguaggio. |
| `UICulture` | Parametro **String** facoltativo.<br /><br /> Specifica l'assembly satellite per le impostazioni cultura dell'interfaccia utente in cui sono incorporati i file di formato binario XAML generati. Se **UICulture non** è impostato, i file di formato binario XAML generati vengono incorporati nell'assembly principale. |
| `XAMLDebuggingInformation` | Parametro **booleano** facoltativo.<br /><br /> Se **true,** le informazioni di diagnostica vengono generate e incluse nel codice XAML compilato per facilitare il debug. |

## <a name="remarks"></a>Commenti

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>L'attività in genere compila XAML in formato binario e genera file di codice. Se un file XAML contiene riferimenti a tipi definiti nello stesso progetto, la compilazione in formato binario viene posticipata da **MarkupCompilePass1** a un secondo passaggio di compilazione del markup (**MarkupCompilePass2**). La compilazione di tali file deve essere rinviata poiché è necessario attendere la compilazione dei tipi definiti localmente a cui si fa riferimento. Tuttavia, se un file XAML ha un attributo , genera il file di codice `x:Class` <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> specifico del linguaggio.

Un file XAML è localizzabile se contiene elementi che usano `x:Uid` l'attributo :

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Uid="Page1Uid"
    >
  ...
</Page>
```

Un file XAML fa riferimento a un tipo definito localmente quando dichiara uno spazio dei nomi XML che usa il valore per fare riferimento a uno spazio dei `clr-namespace` nomi nel progetto corrente:

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:localNamespace="clr-namespace:WPFMSBuildSample"
    >
    <Grid>
      <Grid.Resources>
        <localNameSpace:LocalType x:Key="localType" />
      </Grid.Resources>
      ...
    </Grid>
</Page>
```

Se un file XAML è localizzabile o fa riferimento a un tipo definito in locale, è necessario un secondo passaggio di compilazione del markup, che richiede l'esecuzione di [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) e quindi [di MarkupCompilePass2.](../msbuild/markupcompilepass2-task.md)

## <a name="example"></a>Esempio

L'esempio seguente illustra come convertire tre *file XAML page* in file in formato binario. *Page1* contiene un riferimento a un tipo, `Class1`, che si trova nello spazio dei nomi radice del progetto e pertanto non viene convertito nei file di formato binario in questo passaggio di compilazione del markup. Viene invece eseguito [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md), seguito da [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass1"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="MarkupCompilePass1Task">
    <MarkupCompilePass1
      AssemblyName="WPFMSBuildSample"
      Language="C#"
      OutputType="WinExe"
      OutputPath="obj\Debug\"
      ApplicationMarkup="App.xaml"
      PageMarkup="Page1.xaml;Page2.xaml;Page3.xaml"
      SourceCodeFiles="Class1.cs"
      References="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />
  </Target>
</Project>
```

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento su MSBuild WPF](../msbuild/wpf-msbuild-reference.md)
- [Informazioni di riferimento MSBuild attività wpf](../msbuild/wpf-msbuild-task-reference.md)
- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild riferimento alle attività](../msbuild/msbuild-task-reference.md)
- [Creazione di un'applicazione WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Panoramica delle applicazioni browser XAML WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)