---
title: Attività RC | Microsoft Docs
description: Informazioni su MSBuild'attività RC per eseguire il wrapping dello strumento compilatore di risorse di Microsoft Windows, rc.exe, che compila le risorse in un file con estensione res.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions
- vc.task.rc
- VC.Project.VCResourceCompilerTool.SuppressStartupBanner
- VC.Project.VCResourceCompilerTool.NullTerminateStrings
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- RC task (MSBuild (C++))
- MSBuild (C++), RC task
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 393e34bf68745df58f7f3e7dc4d45afb308c6c80
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711607"
---
# <a name="rc-task"></a>RC (attività)

Esegue il wrapping dello strumento Compilatore di risorse di Microsoft Windows, *rc.exe*. L'attività **RC** compila le risorse, ad esempio cursori, icone, bitmap, finestre di dialogo e tipi di carattere, in un file di risorse *(RES)*. Per altre informazioni, vedere [-resource (opzioni del compilatore C#)](/windows/desktop/menurc/resource-compiler).

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività RC. La maggior parte dei parametri di attività e alcuni set di parametri corrispondono a un'opzione della riga di comando.

|Parametro|Descrizione|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|Parametro **String[]** facoltativo.<br /><br /> Aggiunge una directory all'elenco delle directory in cui vengono cercati i file di inclusione.<br /><br /> Per altre informazioni, vedere l'opzione **/I** in [Using RC (The RC Command Line)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**Opzioni aggiuntive**|Parametro **String** facoltativo.<br /><br /> Elenco di opzioni della riga di comando. ad esempio / \<option1>  / \<option2>  / \<option#> . Usare questo parametro per specificare le opzioni della riga di comando che non sono rappresentate da altri parametri dell'attività **RC**.<br /><br /> Per altre informazioni, vedere le opzioni in [ Using RC (The RC Command Line)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**Impostazioni cultura**|Parametro **String** facoltativo.<br /><br /> Specifica un ID impostazioni locali che rappresenta le impostazioni cultura usate nelle risorse.<br /><br /> Per altre informazioni, vedere l'opzione **/l** in [Using RC (The RC Command Line)](/windows/win32/menurc/using-rc-the-rc-command-line-) (Uso di RC (riga di comando RC)).|
|**IgnoreStandardIncludePath**|Parametro **booleano** facoltativo.<br /><br /> Se `true`, impedisce al compilatore di risorse di verificare la variabile di ambiente INCLUDE durante la ricerca di file di intestazione o file di risorse.<br /><br /> Per altre informazioni, vedere l'opzione **/x** in [Using RC (The RC Command Line)](/windows/win32/menurc/using-rc-the-rc-command-line-) (Uso di RC (riga di comando RC)).|
|**NullTerminateStrings**|Parametro **booleano** facoltativo.<br /><br /> Se `true`, fa terminare con Null tutte le stringhe nella tabella di stringhe.<br /><br /> Per altre informazioni, vedere l'opzione **/n** in [Using RC (The RC Command Line)](/windows/win32/menurc/using-rc-the-rc-command-line-) (Uso di RC (riga di comando RC)).|
|**PreprocessorDefinitions**|Parametro **String[]** facoltativo.<br /><br /> Definire uno o più simboli del preprocessore per il compilatore di risorse. Specificare un elenco di simboli di macro.<br /><br /> Per altre informazioni, vedere l'opzione **/d** in [ Using RC (The RC Command Line)](/windows/win32/menurc/using-rc-the-rc-command-line-) (Uso di RC (riga di comando RC)). Vedere anche **UndefinePreprocessorDefinitions** in questa tabella.|
|**ResourceOutputFileName**|Parametro **String** facoltativo.<br /><br /> Specifica il nome del file di risorse. Specificare un nome di file di risorse.<br /><br /> Per altre informazioni, vedere l'opzione **/fo** in [Using RC (The RC Command Line)](/windows/win32/menurc/using-rc-the-rc-command-line-) (Uso di RC (riga di comando RC)).|
|**ShowProgress**|Parametro **booleano** facoltativo.<br /><br /> Se `true`, visualizza messaggi che segnalano lo stato di avanzamento del compilatore.<br /><br /> Per altre informazioni, vedere l'opzione **/v** in [Using RC (The RC Command Line)](/windows/win32/menurc/using-rc-the-rc-command-line-) (Uso di RC (riga di comando RC)).|
|**Origine**|Parametro `ITaskItem[]` obbligatorio.<br /><br /> Definisce una matrice di elementi del file di origine MSBuild che può essere usata ed emessa dalle attività.|
|**SuppressStartupBanner**|Parametro **booleano** facoltativo.<br /><br /> Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.<br /><br /> Per altre informazioni, digitare l'opzione della riga di comando **/?** e quindi visualizzare l'opzione **/nologo**.|
|**TrackerLogDirectory**|Parametro **String** facoltativo.<br /><br /> Specifica la directory log di Tracker.|
|**UndefinePreprocessorDefinitions**|Rimuove la definizione di un simbolo del preprocessore.<br /><br /> Per altre informazioni, vedere l'opzione **/v** in [Using RC (The RC Command Line)](/windows/win32/menurc/using-rc-the-rc-command-line-) (Uso di RC (riga di comando RC)). Vedere anche **PreprocessorDefinitions** in questa tabella.|

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)