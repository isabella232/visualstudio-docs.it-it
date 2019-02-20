---
title: Attività BscMake | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
- MSBuild (Visual C++), tasks
- BscMake task (MSBuild (Visual C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c21c14b8c84246545d9ffb3e3dc59210b56fe84e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54777152"
---
# <a name="bscmake-task"></a>Attività BscMake
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
IMPORTANT]
>  Lo strumento bscmake non viene più usato dall'IDE di Visual Studio. A partire da Visual Studio 2008, le informazioni di visualizzazione vengono automaticamente archiviate in un file sdf nella cartella della soluzione.  
  
 Esegue il wrapping dello strumento Microsoft Browse Information Maintenance Utility (bscmake.exe).  Lo strumento bscmake.exe genera un file di informazioni di visualizzazione (con estensione bsc) dai file browser di origine (con estensione sbr) creati durante la compilazione. Usare il **Visualizzatore oggetti** per visualizzare un file con estensione bsc. Per altre informazioni, vedere [Riferimenti a BSCMAKE](http://msdn.microsoft.com/library/b97ad994-1355-4809-98db-6abc12c6fb13).  
  
## <a name="parameters"></a>Parametri  
 La tabella seguente illustra i parametri dell'attività **BscMake**. La maggior parte dei parametri attività corrisponde a un'opzione della riga di comando.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|**AdditionalOptions**|Parametro **String** facoltativo.<br /><br /> Un elenco di opzioni come specificato sulla riga di comando. Ad esempio, "/*option1* /*option2* /*option#*". Usare questo parametro per specificare le opzioni che non sono rappresentate da altri parametri dell'attività **BscMake**.<br /><br /> Per altre informazioni, vedere le opzioni in [Opzioni di BSCMAKE](http://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**OutputFile**|Parametro **String** facoltativo.<br /><br /> Specifica un nome di file che esegue l'override del nome del file di output predefinito.<br /><br /> Per altre informazioni, vedere l'opzione **/o** in [Opzioni di BSCMAKE](http://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**PreserveSBR**|Parametro **Boolean** facoltativo.<br /><br /> Se `true`, forza una compilazione non incrementale. Viene eseguita una compilazione completa, non incrementale indipendentemente dall'esistenza di un file BSC e impedisce che i file SBR vengano troncati.<br /><br /> Per altre informazioni, vedere l'opzione **/n** in [Opzioni di BSCMAKE](http://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**Sources**|Parametro **ITaskItem[]** facoltativo.<br /><br /> Definisce una matrice di elementi del file di origine MSBuild che può essere usata ed emessa dalle attività.|  
|**SuppressStartupBanner**|Parametro **Boolean** facoltativo.<br /><br /> Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.<br /><br /> Per altre informazioni, vedere l'opzione **/NOLOGO** in [Opzioni di BSCMAKE](http://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**TrackerLogDirectory**|Parametro **String** facoltativo.<br /><br /> Specifica la directory per il log di Tracker.|  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti alle attività](../msbuild/msbuild-task-reference.md)
