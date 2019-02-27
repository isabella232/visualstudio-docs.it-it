---
title: Attività XDCMake | Microsoft Docs
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb27b631458cba0c36dd9b260ff62bf370773e8d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56623190"
---
# <a name="xdcmake-task"></a>attività XDCMake
Esegue il wrapping dello strumento Documentazione XML, *xdcmake.ex*  che unisce i file di commento con estensione *xdc* del documento XML in un file con estensione *xml*.

 Viene creato un file con estensione *xdc* quando si aggiungono commenti alla documentazione nel codice sorgente di Visual C++ e si compila con l'opzione [/doc](/cpp/build/reference/doc-process-documentation-comments-c-cpp) del compilatore. Per altre informazioni, vedere [Riferimento a XDCMake](/cpp/ide/xdcmake-reference), [Pagina delle proprietà dello strumento generatore di documenti XML](/cpp/ide/xml-document-generator-tool-property-pages) e l'opzione della riga di comando per la visualizzazione della Guida (**/?**) relativa a *xdcmake.exe*.

## <a name="remarks"></a>Osservazioni
 Per impostazione predefinita lo strumento *xdcmake.exe* supporta solo alcune opzioni della riga di comando. Vengono supportate altre opzioni quando si specifica l'opzione **/old** della riga di comando.

## <a name="parameters"></a>Parametri
 La tabella seguente descrive i parametri dell'attività **XDCMake**.

|Parametro|Description|
|---------------|-----------------|
|**AdditionalDocumentFile**|Parametro **String[]** facoltativo.<br /><br /> Consente di specificare uno o più file aggiuntivi con estensione *xdc* da unire.<br /><br /> Per altre informazioni, vedere la descrizione di **File di documentazione aggiuntivi** in [Pagina delle proprietà dello strumento generatore di documenti XML](/cpp/ide/xml-document-generator-tool-property-pages). Vedere anche le opzioni della riga di comando **/old** e **/Fs** per *xdcmake.exe*.|
|**AdditionalOptions**|Parametro **String** facoltativo.<br /><br /> Un elenco di opzioni come specificato sulla riga di comando. Ad esempio, /\<opzione1> /\<opzione2> /\<opzione#>. Usare questo parametro per specificare le opzioni che non sono rappresentate da altri parametri dell'attività **XDCMake**.<br /><br /> Per altre informazioni, vedere [Riferimento a XDCMake](/cpp/ide/xdcmake-reference), [Pagina delle proprietà dello strumento generatore di documenti XML](/cpp/ide/xml-document-generator-tool-property-pages) e l'opzione della riga di comando per la visualizzazione della Guida (**/?**) relativa a *xdcmake.exe*.|
|**DocumentLibraryDependencies**|Parametro **Boolean** facoltativo.<br /><br /> Se è `true` e il progetto corrente contiene una dipendenza a un progetto di libreria statica (con estensione *lib*) nella soluzione, i file con estensione *xdc* di quel progetto di libreria sono inclusi nel file *xml* di output del progetto corrente.<br /><br /> Per altre informazioni, vedere la descrizione di **Dipendenze raccolte documenti** in [Pagina delle proprietà dello strumento generatore di documenti XML](/cpp/ide/xml-document-generator-tool-property-pages).|
|**OutputFile**|Parametro **String** facoltativo.<br /><br /> Esegue l'override del nome del file di output predefinito. Il nome predefinito è derivato dal nome del primo file con estensione *xdc* elaborato.<br /><br /> Per altre informazioni, vedere l'opzione **/out:\<nomefile>** in [Riferimento a XDCMake](/cpp/ide/xdcmake-reference). Vedere anche le opzioni **/old** e **/Fo** della riga di comando per *xdcmake.exe*.|
|**ProjectName**|Parametro **String** facoltativo.<br /><br /> Nome del progetto corrente.|
|**SlashOld**|Parametro **Boolean** facoltativo.<br /><br /> Se è `true`, abilita opzioni aggiuntive di *xdcmake.exe*.<br /><br /> Per altre informazioni, vedere l'opzione della riga di comando **/old** relativa a *xdcmake.exe*.|
|**Sources**|Parametro `ITaskItem[]` obbligatorio.<br /><br /> Definisce una matrice di elementi del file di origine MSBuild che può essere usata ed emessa dalle attività.|
|**SuppressStartupBanner**|Parametro **Boolean** facoltativo.<br /><br /> Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.<br /><br /> Per altre informazioni, vedere l'opzione **/nologo** in [Riferimento a XDCMake](/cpp/ide/xdcmake-reference).|
|**TrackerLogDirectory**|Parametro **String** facoltativo.<br /><br /> Specifica la directory per il log di Tracker.|

## <a name="see-also"></a>Vedere anche
- [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)