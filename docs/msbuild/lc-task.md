---
title: Attività LC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#LC
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, LC task
- LC task [MSBuild]
ms.assetid: d5a53472-6f2a-42b8-a6db-593ca99c9790
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5759be35cda11557847d128233811d8aaffced7
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55938930"
---
# <a name="lc-task"></a>LC (attività)
Esegue il wrapping di *LC.exe*, uno strumento che genera un file con estensione *license* da un file con estensione *licx*. Per altre informazioni su *LC.exe*, vedere [Lc.exe (License Compiler)](/dotnet/framework/tools/lc-exe-license-compiler).

## <a name="parameters"></a>Parametri
La tabella seguente descrive i parametri dell'attività `LC`.

|Parametro|Descrizione|
|---------------|-----------------|
|`LicenseTarget`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio.<br /><br /> Specifica l'eseguibile per cui vengono generati i file con estensione *licenses*.|
|`NoLogo`|Parametro `Boolean` facoltativo.<br /><br /> Evita la visualizzazione del messaggio di avvio Microsoft.|
|`OutputDirectory`|Parametro `String` facoltativo.<br /><br /> Specifica la directory in cui inserire i file di output con estensione *licenses*.|
|`OutputLicense`|Parametro di ouput facoltativo <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Specifica il nome del file con estensione *licenses*. Se non si specifica un nome, viene usato il nome del file con estensione *licx* e il file con estensione *licenses* viene inserito nella directory contenente il file con estensione *licx*.|
|`ReferencedAssemblies`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica i componenti a cui si fa riferimento da caricare durante la generazione del file con estensione *license*.|
|`SdkToolsPath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso degli strumenti SDK, ad esempio *resgen.exe*.|
|`Sources`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica gli elementi che contengono componenti concessi in licenza da includere nel file con estensione *licenses*. Per altre informazioni, vedere la documentazione relativa all'opzione `/complist` in [Lc.exe (License Compiler)](/dotnet/framework/tools/lc-exe-license-compiler).|

 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.ToolTask>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [Classe di base ToolTaskExtension](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Esempio
Nell'esempio seguente l'attività `LC` viene usata per compilare le licenze.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
<!-- Item declarations, etc -->

    <Target Name="CompileLicenses">
        <LC
            Sources="@(LicxFile)"
            LicenseTarget="$(TargetFileName)"
            OutputDirectory="$(IntermediateOutputPath)"
            OutputLicenses="$(IntermediateOutputPath)$(TargetFileName).licenses"
            ReferencedAssemblies="@(ReferencePath);@(ReferenceDependencyPaths)">

            <Output
                TaskParameter="OutputLicenses"
                ItemName="CompiledLicenseFile"/>
        </LC>
    </Target>
</Project>
```

## <a name="see-also"></a>Vedere anche
[Attività](../msbuild/msbuild-tasks.md)  
[Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)
