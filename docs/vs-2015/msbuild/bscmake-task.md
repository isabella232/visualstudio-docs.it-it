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
ms.openlocfilehash: 7ed246255fc20b9660d24f234767fdeb451102f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684539"
---
# <a name="bscmake-task"></a>Attività BscMake
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IMPORTANT]
> Lo strumento bscmake non viene più usato dall'IDE di Visual Studio. A partire da Visual Studio 2008, le informazioni di visualizzazione vengono automaticamente archiviate in un file sdf nella cartella della soluzione.  
  
 Esegue il wrapping dello strumento Microsoft Browse Information Maintenance Utility (bscmake.exe).  Lo strumento bscmake.exe genera un file di informazioni di visualizzazione (con estensione bsc) dai file browser di origine (con estensione sbr) creati durante la compilazione. Usare il **Visualizzatore oggetti** per visualizzare un file BSC. Per ulteriori informazioni, vedere [BSCMAKE Reference](https://msdn.microsoft.com/library/b97ad994-1355-4809-98db-6abc12c6fb13).  
  
## <a name="parameters"></a>Parametri  
 La tabella seguente illustra i parametri dell'attività **BscMake**. La maggior parte dei parametri attività corrisponde a un'opzione della riga di comando.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|**AdditionalOptions**|Parametro **stringa** facoltativo.<br /><br /> Un elenco di opzioni come specificato sulla riga di comando. Ad esempio, "/*opzione1*  / *opzione2*  / *Option #*". Usare questo parametro per specificare le opzioni che non sono rappresentate da altri parametri dell'attività **BscMake**.<br /><br /> Per ulteriori informazioni, vedere le opzioni in [Opzioni di BSCMAKE](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**OutputFile**|Parametro **stringa** facoltativo.<br /><br /> Specifica un nome di file che esegue l'override del nome del file di output predefinito.<br /><br /> Per ulteriori informazioni, vedere l'opzione **/o** in [Opzioni di BSCMAKE](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**PreserveSBR**|Parametro **booleano** facoltativo.<br /><br /> Se `true`, forza una compilazione non incrementale. Viene eseguita una compilazione completa, non incrementale indipendentemente dall'esistenza di un file BSC e impedisce che i file SBR vengano troncati.<br /><br /> Per ulteriori informazioni, vedere l'opzione **/n** in [Opzioni di BSCMAKE](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**recenti**|Parametro **ITaskItem []** facoltativo.<br /><br /> Definisce una matrice di elementi del file di origine MSBuild che può essere usata ed emessa dalle attività.|  
|**SuppressStartupBanner**|Parametro **booleano** facoltativo.<br /><br /> Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.<br /><br /> Per ulteriori informazioni, vedere l'opzione **/nologo** in [BSCMAKE Options](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**TrackerLogDirectory**|Parametro **stringa** facoltativo.<br /><br /> Specifica la directory per il log di Tracker.|  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento attività](../msbuild/msbuild-task-reference.md)
