---
title: Usare l'attività AspNetCompiler per precompilare ASP.NET
description: Usare l'attività MSBuild AspNetCompiler per eseguire il wrapping aspnet_compiler.exe, un'utilità per la precompilazione delle applicazioni ASP.NET.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: e77316628f2251fd44d27edaec4c91354fd81a4b
ms.sourcegitcommit: 02445b684e69c1a665a7e06e9b46072d3fcd7ba6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2020
ms.locfileid: "96516093"
---
# <a name="aspnetcompiler-task"></a>AspNetCompiler (attività)

L' `AspNetCompiler` attività esegue il wrapping *aspnet_compiler.exe*, un'utilità per la precompilazione delle applicazioni ASP.NET.

## <a name="task-parameters"></a>Parametri dell'attività

Nella tabella che segue vengono descritti i parametri dell'attività `AspNetCompiler` .

|Parametro|Descrizione|
|---------------|-----------------|
|`AllowPartiallyTrustedCallers`|Parametro `Boolean` facoltativo.<br /><br /> Se questo parametro è `true`, l'assembly con nome sicuro consentirà chiamanti parzialmente attendibili.|
|`Clean`|Parametro `Boolean` facoltativo<br /><br /> Se questo parametro è `true`, verrà eseguita una precompilazione pulita dell'applicazione. I componenti compilati in precedenza verranno ricompilati. Il valore predefinito è `false`. Questo parametro corrisponde all'opzione **-c** in *aspnet_compiler.exe*.|
|`Debug`|Parametro `Boolean` facoltativo.<br /><br /> Se questo parametro è `true`, durante la compilazione verranno restituite informazioni di debug (file con estensione pdb). Il valore predefinito è `false`. Questo parametro corrisponde all'opzione **-d** in *aspnet_compiler.exe*.|
|`DelaySign`|Parametro `Boolean` facoltativo.<br /><br /> Se questo parametro è `true`, al momento della creazione l'assembly verrà firmato solo parzialmente.|
|`FixedNames`|Parametro `Boolean` facoltativo.<br /><br /> Se questo parametro è `true`, agli assembly compilati verranno assegnati nomi fissi.|
|`Force`|Parametro `Boolean` facoltativo<br /><br /> Se questo parametro è `true`, l'attività sovrascriverà la directory di destinazione, se già esistente. Il contenuto esistente andrà perso. Il valore predefinito è `false`. Questo parametro corrisponde all'opzione **-f** in *aspnet_compiler.exe*.|
|`KeyContainer`|Parametro `String` facoltativo.<br /><br /> Specifica un contenitore di chiavi con nome sicuro.|
|`KeyFile`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso fisico del file di chiave con nome sicuro.|
|`MetabasePath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso completo della metabase IIS dell'applicazione. Questo parametro non può essere combinato con il parametro `VirtualPath` o `PhysicalPath`. Questo parametro corrisponde all'opzione **-m** *aspnet_compiler.exe*.|
|`PhysicalPath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso fisico dell'applicazione da compilare. Se questo parametro non è specificato, per individuare l'applicazione verrà usata la metabase di IIS. Questo parametro corrisponde all'opzione **-p** *aspnet_compiler.exe*.|
|`TargetFrameworkMoniker`|Parametro `String` facoltativo.<br /><br /> Specifica il TargetFrameworkMoniker che indica la versione .NET Framework di *aspnet_compiler.exe* da usare. Vengono accettati solo moniker di .NET Framework.|
|`TargetPath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso fisico in cui viene compilata l'applicazione. Se non è specificato, l'applicazione verrà precompilata sul posto.|
|`Updateable`|Parametro `Boolean` facoltativo.<br /><br /> Se questo parametro è `true`, l'applicazione precompilata sarà aggiornabile.  Il valore predefinito è `false`. Questo parametro corrisponde all'opzione **-u** *aspnet_compiler.exe*.|
|`VirtualPath`|Parametro `String` facoltativo.<br /><br /> Percorso virtuale dell'applicazione da compilare. Se `PhysicalPath` è specificato, per individuare l'applicazione verrà usato il percorso fisico. In caso contrario verrà usata la metabase IIS, presupponendo che l'applicazione si trovi nel sito predefinito. Questo parametro corrisponde all'opzione **-v** nel *aspnet_compiler.exe*.|

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Esempio

Nell'esempio di codice seguente viene usata l' `AspNetCompiler` attività per precompilare un'applicazione ASP.NET.

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
* [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
* [Strumento di compilazione ASP.NET (aspnet_compiler.exe)](/previous-versions/ms229863(v=vs.100))
