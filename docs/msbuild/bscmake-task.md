---
title: Attività BscMake | Microsoft Docs
description: Informazioni su BscMake, che ha eseguito il wrapping dello strumento Microsoft Browse Information Maintenance Utility bscmake.exe. L Visual Studio IDE non usa più BscMake.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.task.bscmake
- VC.Project.VCBscMakeTool.PreserveSBR
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), tasks
- BscMake task (MSBuild (C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 5bb683e6ad8fdfef162fb21f52d4fdffaae9e851fd336372b9816eddaf70b8a6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121428653"
---
# <a name="bscmake-task"></a>Attività BscMake

> [!IMPORTANT]
> Lo strumento BscMake non viene più usato dall'IDE di Visual Studio. A partire da Visual Studio 2008 le informazioni di visualizzazione vengono automaticamente archiviate in un file *SDF* nella cartella della *soluzione*.

 Esegue il wrapping dello strumento Microsoft Browse Information Maintenance Utility (*bscmake.exe*).  Lo strumento *bscmake.exe* genera un file di informazioni di visualizzazione (*BSC*) dai file browser di origine (*SBR*) creati durante la compilazione. Usare il **Visualizzatore oggetti** per visualizzare un file *BSC*. Per altre informazioni, vedere [Riferimenti a BSCMAKE](/cpp/build/reference/bscmake-reference).

## <a name="parameters"></a>Parametri

 La tabella seguente illustra i parametri dell'attività **BscMake**. La maggior parte dei parametri attività corrisponde a un'opzione della riga di comando.

|Parametro|Descrizione|
|---------------|-----------------|
|**Opzioni aggiuntive**|Parametro **String** facoltativo.<br /><br /> Un elenco di opzioni come specificato sulla riga di comando. Ad esempio, / \<option1>  / \<option2>  / \<option#> . Usare questo parametro per specificare le opzioni che non sono rappresentate da altri parametri dell'attività **BscMake**.<br /><br /> Per altre informazioni, vedere le opzioni in [Opzioni di BSCMAKE](/cpp/build/reference/bscmake-options).|
|**Outputfile**|Parametro **String** facoltativo.<br /><br /> Specifica un nome di file che esegue l'override del nome del file di output predefinito.<br /><br /> Per altre informazioni, vedere l'opzione **/o** in [Opzioni di BSCMAKE](/cpp/build/reference/bscmake-options).|
|**PreserveSBR**|Parametro **booleano** facoltativo.<br /><br /> Se `true`, forza una compilazione non incrementale. Viene eseguita una compilazione completa, non incrementale indipendentemente dall'esistenza di un file *BSC* e impedisce che i file *SBR* vengano troncati.<br /><br /> Per altre informazioni, vedere l'opzione **/n** in [Opzioni di BSCMAKE](/cpp/build/reference/bscmake-options).|
|**recenti**|Parametro **ITaskItem[]** facoltativo.<br /><br /> Definisce una matrice di elementi del file di origine MSBuild che può essere usata ed emessa dalle attività.|
|**SuppressStartupBanner**|Parametro **booleano** facoltativo.<br /><br /> Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.<br /><br /> Per altre informazioni, vedere l'opzione **/NOLOGO** in [Opzioni di BSCMAKE](/cpp/build/reference/bscmake-options).|
|**TrackerLogDirectory**|Parametro **String** facoltativo.<br /><br /> Specifica la directory per il log di Tracker.|

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
