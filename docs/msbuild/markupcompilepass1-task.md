---
title: Attività MarkupCompilePass1 | Microsoft Docs
description: Informazioni su come MSBuild usa l'attività MarkupCompilePass1 per convertire i file di progetto XAML non localizzabili in formato binario compilato.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 775884692963da226947a8fac524a8bd440d6c8d
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2020
ms.locfileid: "92904274"
---
# <a name="markupcompilepass1-task"></a>Attività MarkupCompilePass1

L' <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> attività converte i file di progetto XAML non localizzabili in formato binario compilato.

## <a name="task-parameters"></a>Parametri dell'attività

| Parametro | Descrizione |
| - | - |
| `AllGeneratedFiles` | Parametro di output facoltativo **ITaskItem[]** .<br /><br /> Contiene un elenco completo dei file generati dall'attività <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>. |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Parametro **booleano** facoltativo.<br /><br /> Specifica se eseguire l'attività in un <xref:System.AppDomain> separato. Se questo parametro restituisce **false** , l'attività viene eseguita in modo analogo a <xref:System.AppDomain> MSBuild e viene eseguita più velocemente. Se il parametro restituisce **true** , l'attività viene eseguita in un secondo <xref:System.AppDomain> isolato da MSBuild ed eseguito più lentamente. |
| `ApplicationMarkup` | Parametro **ITaskItem []** facoltativo.<br /><br /> Specifica il nome del file XAML della definizione dell'applicazione. |
| `AssembliesGeneratedDuringBuild` | Parametro **String []** facoltativo.<br /><br /> Specifica i riferimenti ad assembly che vengono modificati durante il processo di compilazione. Ad esempio, una soluzione Visual Studio può contenere un progetto che fa riferimento all'output compilato di un altro progetto. In questo caso, l'output compilato del secondo progetto può essere aggiunto al parametro **AssembliesGeneratedDuringBuild** .<br /><br /> Nota: il parametro **AssembliesGeneratedDuringBuild** deve contenere riferimenti all'insieme completo di assembly generati da una soluzione di compilazione. |
| `AssemblyName` | Parametro di **stringa** obbligatorio.<br /><br /> Specifica il nome breve dell'assembly generato per un progetto. Se, ad esempio, un progetto genera un eseguibile Windows il cui nome è *WinExeAssembly.exe* , il parametro **AssemblyName** avrà il valore **WinExeAssembly** . |
| `AssemblyPublicKeyToken` | Parametro **stringa** facoltativo.<br /><br /> Specifica il token di chiave pubblica per l'assembly. |
| `AssemblyVersion` | Parametro **stringa** facoltativo.<br /><br /> Specifica il numero di versione dell'assembly. |
| `ContentFiles` | Parametro **ITaskItem []** facoltativo.<br /><br /> Specifica l'elenco dei file di contenuto separati. |
| `DefineConstants` | Parametro **stringa** facoltativo.<br /><br /> Specifica che viene mantenuto il valore corrente di **DefineConstants** , che influiscono sulla generazione dell'assembly di destinazione; Se questo parametro viene modificato, l'API pubblica nell'assembly di destinazione può essere modificata e la compilazione di file XAML che fanno riferimento a tipi locali può essere interessata. |
| `ExtraBuildControlFiles` | Parametro **ITaskItem []** facoltativo.<br /><br /> Specifica un elenco di file che controllano l'attivazione di una ricompilazione durante la riesecuzione dell'attività <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>. La ricompilazione viene attivata in caso di modifica di uno di questi file. |
| `GeneratedBamlFiles` | Parametro di output facoltativo **ITaskItem[]** .<br /><br /> Contiene l'elenco dei file generati nel formato binario XAML. |
| `GeneratedCodeFiles` | Parametro di output facoltativo **ITaskItem[]** .<br /><br /> Contiene l'elenco dei file di codice gestito generati. |
| `GeneratedLocalizationFiles` | Parametro di output facoltativo **ITaskItem[]** .<br /><br /> Contiene l'elenco dei file di localizzazione generati per ogni file XAML localizzabile. |
| `HostInBrowser` | Parametro **stringa** facoltativo.<br /><br /> Specifica se l'assembly generato è un'applicazione browser XAML (XBAP). Le opzioni valide sono **true** e **false** . Se **true** , verrà generato codice per supportare l'hosting del browser. |
| `KnownReferencePaths` | Parametro **String []** facoltativo.<br /><br /> Specifica i riferimenti ad assembly che non vengono modificati durante il processo di compilazione. Include gli assembly che si trovano nella Global Assembly Cache (GAC), in una directory di installazione di .NET e così via. |
| `Language` | Parametro **String** obbligatorio.<br /><br /> Specifica il linguaggio gestito supportato dal compilatore. Le opzioni valide sono **C#** , **VB** , **JScript** e **C++** . |
| `LanguageSourceExtension` | Parametro **stringa** facoltativo.<br /><br /> Specifica l'estensione aggiunta all'estensione del file di codice gestito generato:<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> Se il parametro **LanguageSourceExtension** non è impostato con un valore specifico, viene utilizzata l'estensione predefinita del nome del file di origine per una lingua: *. vb* per Visual Basic, *CSharp* per C#. |
| `LocalizationDirectivesToLocFile` | Parametro **stringa** facoltativo.<br /><br /> Specifica la modalità di generazione delle informazioni di localizzazione per ogni file XAML di origine. Le opzioni valide sono **None** , **CommentsOnly** e **All** . |
| `OutputPath` | Parametro **String** obbligatorio.<br /><br /> Specifica la directory in cui vengono generati i file di codice gestito e i file in formato binario XAML generati. |
| `OutputType` | Parametro **String** obbligatorio.<br /><br /> Specifica il tipo di assembly generato da un progetto. Le opzioni valide sono **winexe** , **exe** , **library** e **netmodule** . |
| `PageMarkup` | Parametro **ITaskItem []** facoltativo.<br /><br /> Specifica un elenco di file XAML da elaborare. |
| `References` | Parametro **ITaskItem []** facoltativo.<br /><br /> Specifica l'elenco di riferimenti da file agli assembly che contengono i tipi utilizzati nei file XAML. |
| `RequirePass2ForMainAssembly` | Parametro di output **Boolean** facoltativo.<br /><br /> Indica se il progetto contiene file XAML non localizzabili che fanno riferimento ai tipi locali incorporati nell'assembly principale. |
| `RequirePass2ForSatelliteAssembly` | Parametro di output **Boolean** facoltativo.<br /><br /> Indica se il progetto contiene file XAML localizzabili che fanno riferimento ai tipi locali incorporati nell'assembly principale. |
| `RootNamespace` | Parametro **stringa** facoltativo.<br /><br /> Specifica lo spazio dei nomi radice per le classi all'interno del progetto. **RootNamespace** viene utilizzato anche come spazio dei nomi predefinito di un file di codice gestito generato quando il file XAML corrispondente non include l' `x:Class` attributo. |
| `SourceCodeFiles` | Parametro **ITaskItem []** facoltativo.<br /><br /> Specifica l'elenco dei file di codice per il progetto corrente. L'elenco non include file di codice gestito generati specifici del linguaggio. |
| `UICulture` | Parametro **stringa** facoltativo.<br /><br /> Specifica l'assembly satellite per le impostazioni cultura dell'interfaccia utente in cui sono incorporati i file di formato binario XAML generati. Se **UICulture** non è impostato, i file di formato binario XAML generati vengono incorporati nell'assembly principale. |
| `XAMLDebuggingInformation` | Parametro **booleano** facoltativo.<br /><br /> Se è **true** , le informazioni di diagnostica vengono generate e incluse nel codice XAML compilato per facilitare il debug. |

## <a name="remarks"></a>Osservazioni

L' <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> attività Compila in genere XAML in formato binario e genera file di codice. Se un file XAML contiene riferimenti a tipi definiti nello stesso progetto, la relativa compilazione in formato binario viene rinviata da **MarkupCompilePass1** a un secondo passaggio di compilazione del markup ( **MarkupCompilePass2** ). La compilazione di tali file deve essere rinviata poiché è necessario attendere la compilazione dei tipi definiti localmente a cui si fa riferimento. Tuttavia, se un file XAML dispone di un `x:Class` attributo, <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> genera il file di codice specifico del linguaggio.

Un file XAML è localizzabile se contiene elementi che usano l' `x:Uid` attributo:

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Uid="Page1Uid"
    >
  ...
</Page>
```

Un file XAML fa riferimento a un tipo definito localmente quando dichiara uno spazio dei nomi XML che usa il `clr-namespace` valore per fare riferimento a uno spazio dei nomi nel progetto corrente:

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

Se un file XAML è localizzabile o fa riferimento a un tipo definito localmente, è necessario un secondo passaggio di compilazione del markup, che richiede l'esecuzione di [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) e quindi [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come convertire tre file XAML di *pagina* in file di formato binario. *Page1* contiene un riferimento a un tipo, `Class1`, che si trova nello spazio dei nomi radice del progetto e pertanto non viene convertito nei file di formato binario in questo passaggio di compilazione del markup. Viene invece eseguito [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md), seguito da [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).

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

## <a name="see-also"></a>Vedere anche

- [Informazioni di riferimento su MSBuild WPF](../msbuild/wpf-msbuild-reference.md)
- [Guida di riferimento alle attività MSBuild WPF](../msbuild/wpf-msbuild-task-reference.md)
- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
- [Riferimenti alle attività MSBuild](../msbuild/msbuild-task-reference.md)
- [Creazione di un'applicazione WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Panoramica delle applicazioni browser XAML WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)