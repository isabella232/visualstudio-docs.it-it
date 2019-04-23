---
title: Attività XDCMake | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.xdcmake
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- XDCMake task (MSBuild (Visual C++))
- MSBuild (Visual C++), XDCMake task
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0d306ec78087ed53ceca44b15f2e184397217650
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59661958"
---
# <a name="xdcmake-task"></a>Attività XDCMake
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esegue il wrapping dello strumento Documentazione XML (xdcmake.exe) che unisce i file di commento (con estensione xdc) del documento XML in un file con estensione xml.  
  
 Viene creato un file con estensione xdc quando si forniscono commenti alla documentazione nel codice sorgente di Visual C++ e si compila con l'opzione [/doc](http://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63) del compilatore. Per altre informazioni, vedere [Riferimento a XDCMake](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac), [Pagina delle proprietà dello strumento generatore di documenti XML](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0) e l'opzione della riga di comando per la visualizzazione della Guida (**/?**) relativa a xdcmake.exe.  
  
## <a name="remarks"></a>Osservazioni  
 Per impostazione predefinita, lo strumento xdcmake.exe supporta solo alcune opzioni della riga di comando. Vengono supportate altre opzioni quando si specifica l'opzione **/old** della riga di comando.  
  
## <a name="parameters"></a>Parametri  
 La tabella seguente descrive i parametri dell'attività **XDCMake**.  
  
|Parametro|Description|  
|---------------|-----------------|  
|**AdditionalDocumentFile**|Parametro **String[]** facoltativo.<br /><br /> Consente di specificare uno o più file aggiuntivi con estensione xdc da unire.<br /><br /> Per altre informazioni, vedere la descrizione di **File di documentazione aggiuntivi** in [Pagina delle proprietà dello strumento generatore di documenti XML](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0). Vedere anche le opzioni **/old** e **/Fs** della riga di comando per xdcmake.exe.|  
|**AdditionalOptions**|Parametro **String** facoltativo.<br /><br /> Un elenco di opzioni come specificato sulla riga di comando. Ad esempio, "*/opzione1 /opzione2 /opzione#*". Usare questo parametro per specificare le opzioni che non sono rappresentate da altri parametri dell'attività **XDCMake**.<br /><br /> Per altre informazioni, vedere [Riferimento a XDCMake](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac), [Pagina delle proprietà dello strumento generatore di documenti XML](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0) e l'opzione della riga di comando per la visualizzazione della Guida (**/?**) relativa a xdcmake.exe.|  
|**DocumentLibraryDependencies**|Parametro **Boolean** facoltativo.<br /><br /> Se è `true` e il progetto corrente contiene una dipendenza a un progetto di libreria statica (con estensione lib) nella soluzione, i file con estensione xdc di quel progetto di libreria sono inclusi nel file XML di output del progetto corrente.<br /><br /> Per altre informazioni, vedere la descrizione di **Dipendenze raccolte documenti** in [Pagina delle proprietà dello strumento generatore di documenti XML](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0).|  
|**OutputFile**|Parametro **String** facoltativo.<br /><br /> Esegue l'override del nome del file di output predefinito. Il nome predefinito è derivato dal nome del primo file con estensione xdc elaborato.<br /><br /> Per altre informazioni, vedere l'opzione **/out:**`filename` in [Riferimento a XDCMake](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac). Vedere anche le opzioni **/old** e **/Fo** della riga di comando per xdcmake.exe.|  
|**ProjectName**|Parametro **String** facoltativo.<br /><br /> Nome del progetto corrente.|  
|**SlashOld**|Parametro **Boolean** facoltativo.<br /><br /> Se è `true`, abilita le opzioni aggiuntive di xdcmake.exe.<br /><br /> Per altre informazioni, vedere l'opzione della riga di comando **/old** relativa a xdcmake.exe.|  
|**Sources**|Parametro `ITaskItem[]` obbligatorio.<br /><br /> Definisce una matrice di elementi del file di origine MSBuild che può essere usata ed emessa dalle attività.|  
|**SuppressStartupBanner**|Parametro **Boolean** facoltativo.<br /><br /> Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.<br /><br /> Per altre informazioni, vedere l'opzione **/nologo** in [Riferimento a XDCMake](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac).|  
|**TrackerLogDirectory**|Parametro **String** facoltativo.<br /><br /> Specifica la directory per il log di Tracker.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti alle attività](../msbuild/msbuild-task-reference.md)
