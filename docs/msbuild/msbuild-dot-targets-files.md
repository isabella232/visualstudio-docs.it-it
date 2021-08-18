---
title: MSBuild file con estensione targets | Microsoft Docs
description: Informazioni sui file MSBuild con estensione targets che contengono elementi, proprietà, destinazioni e attività per scenari comuni.
ms.custom: SEO-VS-2020
ms.date: 02/24/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .targets files
- MSBuild, .targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: b30aaf73a49c1ef75f0778e619cbfb4a4b69846d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093624"
---
# <a name="msbuild-targets-files"></a>File con estensione targets di MSBuild

MSBuild include diversi *file con estensione targets* che contengono elementi, proprietà, destinazioni e attività per scenari comuni. Questi file vengono importati automaticamente nella maggior parte dei Visual Studio di progetto per semplificare la manutenzione e la leggibilità.

 I progetti importano generalmente uno o più file con estensione *targets* per definire il processo di compilazione. Ad esempio, un progetto C# creato da Visual Studio importerà *Microsoft.CSharp.targets* che importa *Microsoft.Common.targets*. Il progetto C# stesso definirà gli elementi e le proprietà specifici di tale progetto, ma le regole di compilazione standard per un progetto C# sono definite nei file con estensione *targets* importati.

 Il valore `$(MSBuildToolsPath)` specifica il percorso di questi file comuni con estensione *targets*. Se è 4.0, i file si trova nel percorso `ToolsVersion` seguente: *\<WindowsInstallationPath> \Microsoft.NET\Framework\v4.0.30319 \\*

> [!NOTE]
> Per informazioni su come creare destinazioni personalizzate, vedere [Destinazioni](../msbuild/msbuild-targets.md). Per informazioni su come usare l'elemento `Import` per inserire un file di progetto in un altro file di progetto, vedere [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md) e [Procedura: Usare la stessa destinazione in più file di progetto](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).

## <a name="common-targets-files"></a>File comuni con estensione targets

| File con estensione *targets* | Descrizione |
|---------------------------------| - |
| *Microsoft.Common.targets* | Definisce i passaggi del processo di compilazione standard per i Visual Basic e C#.<br /><br /> Importato dai file *Microsoft.CSharp.targets* e *Microsoft.VisualBasic.targets*, che includono l'istruzione seguente: `<Import Project="Microsoft.Common.targets" />` |
| *Microsoft.CSharp.targets* | Definisce i passaggi nel processo di compilazione standard per i progetti di Visual C#.<br /><br /> Importato da file di progetto di Visual C# (con estensione *csproj*), che includono l'istruzione seguente: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` |
| *Microsoft.VisualBasic.targets* | Definisce i passaggi nel processo di compilazione standard per i progetti di Visual Basic.<br /><br /> Importato da file di progetto di Visual Basic (con estensione *vbproj*), che includono l'istruzione seguente: `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />` |

## <a name="directorybuildtargets"></a>Directory.Build.targets

*Directory.Build.targets* è un file definito dall'utente che specifica le personalizzazioni dei progetti in una directory. Questo file viene importato automaticamente da *Microsoft.Common.targets*, a meno che la proprietà **ImportDirectoryBuildTargets** sia impostata su **False**. Per altre informazioni, vedere [Personalizzare la compilazione](customize-your-build.md).

## <a name="see-also"></a>Vedi anche

- [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md)
- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
