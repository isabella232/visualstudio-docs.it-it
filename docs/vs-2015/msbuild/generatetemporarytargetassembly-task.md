---
title: Attività GenerateTemporaryTargetAssembly | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3f537e6f9f1712e3d103a0d425265153bf2152e
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "54774683"
---
# <a name="generatetemporarytargetassembly-task"></a>Attività GenerateTemporaryTargetAssembly
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
L'attività <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> genera un assembly se in un progetto almeno una pagina [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] fa riferimento a un tipo dichiarato localmente nel progetto. L'assembly generato viene rimosso dopo il completamento del processo di compilazione o in caso di esito negativo del processo.  
  
## <a name="task-parameters"></a>Parametri dell'attività  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AssemblyName`|Parametro **String** obbligatorio.<br /><br /> Specifica il nome breve dell'assembly generato per un progetto ed è anche il nome dell'assembly di destinazione generato temporaneamente. Se, ad esempio, un progetto genera un eseguibile [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] il cui nome è **WinExeAssembly.exe**, il parametro **AssemblyName** presenterà il valore **WinExeAssembly**.|  
|`CompileTargetName`|Parametro **String** obbligatorio.<br /><br /> Specifica il nome della destinazione [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)] usata per generare assembly dai file di codice sorgente. Il valore tipico per **CompileTargetName** è **CoreCompile**.|  
|`CompileTypeName`|Parametro **String** obbligatorio.<br /><br /> Specifica il tipo di compilazione eseguito dalla destinazione specificata dal parametro **CompileTargetName**. Per la destinazione **CoreCompile** questo valore è **Compile**.|  
|`CurrentProject`|Parametro **String** obbligatorio.<br /><br /> Specifica il percorso completo del file di progetto [!INCLUDE[TLA2#tla_msbuild](../includes/tla2sharptla-msbuild-md.md)] per il progetto che richiede un assembly di destinazione temporaneo.|  
|`GeneratedCodeFiles`|Parametro **ITaskItem[]** facoltativo.<br /><br /> Specifica l'elenco di file di codice gestito specifici del linguaggio generati dall'attività [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md).|  
|`IntermediateOutputPath`|Parametro **String** obbligatorio.<br /><br /> Specifica la directory in cui viene generato l'assembly di destinazione temporaneo.|  
|`MSBuildBinPath`|Parametro **String** obbligatorio.<br /><br /> Specifica il percorso di **MSBuild.exe**, necessario per compilare l'assembly di destinazione temporaneo.|  
|`ReferencePath`|Parametro **ITaskItem[]** facoltativo.<br /><br /> Specifica un elenco di assembly, per percorso e nome file, a cui fanno riferimento i tipi compilati nell'assembly di destinazione temporaneo.|  
|`ReferencePathTypeName`|Parametro **String** obbligatorio.<br /><br /> Specifica il parametro usato dal parametro di destinazione della compilazione (**CompileTargetName**), che specifica l'elenco di riferimenti ad assembly (**ReferencePath**). Il valore appropriato è **ReferencePath**.|  
  
## <a name="remarks"></a>Osservazioni  
 Il primo passaggio di compilazione del markup, eseguito da [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md), compila i file [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] in formato binario. Il compilatore necessita quindi dell'elenco degli assembly a cui si fa riferimento in cui sono contenuti i tipi usati dai file [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)]. Se tuttavia un file [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] usa un tipo definito nello stesso progetto, non viene creato un assembly corrispondente per il progetto fino a quando quest'ultimo non viene compilato. Pertanto, non è possibile fornire un riferimento all'assembly durante il primo passaggio di compilazione del markup.  
  
 **MarkupCompilePass1** rinvia la conversione dei file [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] che contengono riferimenti a tipi dello stesso progetto a un secondo passaggio di compilazione del markup, eseguito da [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md). Prima dell'esecuzione di **MarkupCompilePass2**, viene generato un assembly temporaneo contenente i tipi usati dai file [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] di cui è stato rinviato il passaggio di compilazione del markup. Un riferimento all'assembly generato viene fornito a **MarkupCompilePass2** mentre viene eseguito, in modo da consentire la conversione in formato binario dei file [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] con compilazione rinviata.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene generato un assembly temporaneo poiché `Page1.xaml` contiene un riferimento a un tipo che si trova nello stesso progetto.  
  
```  
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
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento su MSBuild WPF](../msbuild/wpf-msbuild-reference.md)   
 [Riferimento alle attività](../msbuild/wpf-msbuild-task-reference.md)   
 [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)   
 [Compilazione di un'applicazione WPF (WPF)](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [Panoramica delle applicazioni browser XAML di WPF](http://msdn.microsoft.com/library/3a7a86a8-75d5-4898-96b9-73da151e5e16)
