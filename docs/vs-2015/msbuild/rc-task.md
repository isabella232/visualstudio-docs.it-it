---
title: Attività RC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
- RC task (MSBuild (Visual C++))
- MSBuild (Visual C++), RC task
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 81f64ec9774410ea55897445836c8633fe98e7bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851736"
---
# <a name="rc-task"></a>Attività RC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esegue il wrapping dello strumento Compilatore di risorse di Microsoft Windows, rc.exe. L'attività **RC** compila le risorse, ad esempio cursori, icone, bitmap, finestre di dialogo e tipi di carattere, in un file di risorse (res). Per altre informazioni, vedere l'articolo sullo strumento Compilatore di risorse nel sito Web [MSDN](https://msdn.microsoft.com/).  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività RC. La maggior parte dei parametri di attività e alcuni set di parametri corrispondono a un'opzione della riga di comando.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|**AdditionalIncludeDirectories**|Parametro **String []** facoltativo.<br /><br /> Aggiunge una directory all'elenco delle directory in cui vengono cercati i file di inclusione.<br /><br /> Per altre informazioni, vedere l'opzione **/I** in [Using RC (The RC Command Line)](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) (Uso di RC (riga di comando RC)) nel sito Web MSDN.|  
|**AdditionalOptions**|Parametro **stringa** facoltativo.<br /><br /> Un elenco di opzioni della riga di comando, ad esempio **"**_/opzione1/opzione2/opzione #_". Usare questo parametro per specificare le opzioni della riga di comando che non sono rappresentate da altri parametri dell'attività **RC**.<br /><br /> Per altre informazioni, vedere le opzioni in [Using RC (The RC Command Line)](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) (Uso di RC (riga di comando RC)) nel sito Web MSDN.|  
|**Cultura**|Parametro **stringa** facoltativo.<br /><br /> Specifica un ID impostazioni locali che rappresenta le impostazioni cultura usate nelle risorse.<br /><br /> Per altre informazioni, vedere l'opzione **/I** in [Using RC (The RC Command Line)](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) (Uso di RC (riga di comando RC)) nel sito Web MSDN.|  
|**IgnoreStandardIncludePath**|Parametro **booleano** facoltativo.<br /><br /> Se `true`, impedisce al compilatore di risorse di verificare la variabile di ambiente INCLUDE durante la ricerca di file di intestazione o file di risorse.<br /><br /> Per altre informazioni, vedere l'opzione **/x** in [Using RC (The RC Command Line)](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) (Uso di RC (riga di comando RC)) nel sito Web MSDN.|  
|**NullTerminateStrings**|Parametro **booleano** facoltativo.<br /><br /> Se `true`, fa terminare con Null tutte le stringhe nella tabella di stringhe.<br /><br /> Per altre informazioni, vedere l'opzione **/n** in [Using RC (The RC Command Line)](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) (Uso di RC (riga di comando RC)) nel sito Web MSDN.|  
|**PreprocessorDefinitions**|Parametro **String []** facoltativo.<br /><br /> Definire uno o più simboli del preprocessore per il compilatore di risorse. Specificare un elenco di simboli di macro.<br /><br /> Per altre informazioni, vedere l'opzione **/d** in [Using RC (The RC Command Line)](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) (Uso di RC (riga di comando RC)) nel sito Web MSDN. Vedere anche **UndefinePreprocessorDefinitions** in questa tabella.|  
|**ResourceOutputFileName**|Parametro **stringa** facoltativo.<br /><br /> Specifica il nome del file di risorse. Specificare un nome di file di risorse.<br /><br /> Per altre informazioni, vedere l'opzione **/fo** in [Using RC (The RC Command Line)](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) (Uso di RC (riga di comando RC)) nel sito Web MSDN.|  
|**ShowProgress**|Parametro **booleano** facoltativo.<br /><br /> Se `true`, visualizza messaggi che segnalano lo stato di avanzamento del compilatore.<br /><br /> Per altre informazioni, vedere l'opzione **/v** in [Using RC (The RC Command Line)](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) (Uso di RC (riga di comando RC)) nel sito Web MSDN.|  
|**Origine**|Parametro `ITaskItem[]` obbligatorio.<br /><br /> Definisce una matrice di elementi del file di origine MSBuild che può essere usata ed emessa dalle attività.|  
|**SuppressStartupBanner**|Parametro **booleano** facoltativo.<br /><br /> Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.<br /><br /> Per altre informazioni, digitare l'opzione della riga di comando **/?** e quindi visualizzare l'opzione **/nologo**.|  
|**TrackerLogDirectory**|Parametro **stringa** facoltativo.<br /><br /> Specifica la directory log di Tracker.|  
|**UndefinePreprocessorDefinitions**|Rimuove la definizione di un simbolo del preprocessore.<br /><br /> Per altre informazioni, vedere l'opzione **/u** in [Using RC (The RC Command Line)](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) (Uso di RC (riga di comando RC)) nel sito Web MSDN. Vedere anche **PreprocessorDefinitions** in questa tabella.|  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento attività](../msbuild/msbuild-task-reference.md)
