---
title: Uso dell'attività AspNetCompiler per la precompilazione delle applicazioni ASP.NET | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AspNetCompiler
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AspNetCompiler task
- AspNetCompiler task [MSBuild]
ms.assetid: f811c019-a67b-4d54-82e6-e29549496f6e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 90b9111d8d8ae78e5b937942df32fb84c97355fa
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56602273"
---
# <a name="aspnetcompiler-task"></a>AspNetCompiler (attività)
L'attività `AspNetCompiler` esegue il wrapping di *aspnet_compiler.exe*, un'utilità per la precompilazione di applicazioni [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

## <a name="task-parameters"></a>Parametri dell'attività
Nella tabella che segue vengono descritti i parametri dell'attività `AspNetCompiler` .

|Parametro|Description|
|---------------|-----------------|
|`AllowPartiallyTrustedCallers`|Parametro `Boolean` facoltativo.<br /><br /> Se questo parametro è `true`, l'assembly con nome sicuro consentirà chiamanti parzialmente attendibili.|
|`Clean`|Parametro `Boolean` facoltativo<br /><br /> Se questo parametro è `true`, verrà eseguita una precompilazione pulita dell'applicazione. I componenti compilati in precedenza verranno ricompilati. Il valore predefinito è `false`. Questo campo corrisponde all'opzione **-c** in *aspnet_compiler.exe*.|
|`Debug`|Parametro `Boolean` facoltativo.<br /><br /> Se questo parametro è `true`, durante la compilazione verranno restituite informazioni di debug (file con estensione pdb). Il valore predefinito è `false`. Questo campo corrisponde all'opzione **-d** in *aspnet_compiler.exe*.|
|`DelaySign`|Parametro `Boolean` facoltativo.<br /><br /> Se questo parametro è `true`, al momento della creazione l'assembly verrà firmato solo parzialmente.|
|`FixedNames`|Parametro `Boolean` facoltativo.<br /><br /> Se questo parametro è `true`, agli assembly compilati verranno assegnati nomi fissi.|
|`Force`|Parametro `Boolean` facoltativo.<br /><br /> Se questo parametro è `true`, l'attività sovrascriverà la directory di destinazione, se già esistente. Il contenuto esistente andrà perso. Il valore predefinito è `false`. Questo campo corrisponde all'opzione **-f** in *aspnet_compiler.exe*.|
|`KeyContainer`|Parametro `String` facoltativo.<br /><br /> Specifica un contenitore di chiavi con nome sicuro.|
|`KeyFile`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso fisico del file di chiave con nome sicuro.|
|`MetabasePath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso completo della metabase IIS dell'applicazione. Questo parametro non può essere combinato con il parametro `VirtualPath` o `PhysicalPath`. Questo campo corrisponde all'opzione **-m** in *aspnet_compiler.exe*.|
|`PhysicalPath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso fisico dell'applicazione da compilare. Se questo parametro non è specificato, per individuare l'applicazione verrà usata la metabase di IIS. Questo campo corrisponde all'opzione **-p** in *aspnet_compiler.exe*.|
|`TargetFrameworkMoniker`|Parametro `String` facoltativo.<br /><br /> Specifica l'elemento TargetFrameworkMoniker che indica la versione .NET Framework di *aspnet_compiler.exe* da usare. Vengono accettati solo moniker di .NET Framework.|
|`TargetPath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso fisico in cui viene compilata l'applicazione. Se non è specificato, l'applicazione verrà precompilata sul posto.|
|`Updateable`|Parametro `Boolean` facoltativo.<br /><br /> Se questo parametro è `true`, l'applicazione precompilata sarà aggiornabile.  Il valore predefinito è `false`. Questo campo corrisponde all'opzione **-u** in *aspnet_compiler.exe*.|
|`VirtualPath`|Parametro `String` facoltativo.<br /><br /> Percorso virtuale dell'applicazione da compilare. Se `PhysicalPath` è specificato, per individuare l'applicazione verrà usato il percorso fisico. In caso contrario verrà usata la metabase IIS, presupponendo che l'applicazione si trovi nel sito predefinito. Questo campo corrisponde all'opzione **-v** in *aspnet_compiler.exe*.|

## <a name="remarks"></a>Osservazioni
Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.ToolTask>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [Classe di base ToolTaskExtension](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Esempio
Nell'esempio di codice seguente l'attività `AspNetCompiler` viene usata per precompilare un'applicazione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="PrecompileWeb">
        <AspNetCompiler
            VirtualPath="/MyWebSite"
            PhysicalPath="c:\inetpub\wwwroot\MyWebSite\"
            TargetPath="c:\precompiledweb\MyWebSite\"
            Force="true"
            Debug="true"
        />
    </Target>
</Project>
```

## <a name="see-also"></a>Vedere anche
* [Attività](../msbuild/msbuild-tasks.md)
* [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)
