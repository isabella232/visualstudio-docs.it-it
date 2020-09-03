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
- XDCMake task (MSBuild (C++))
- MSBuild (C++), XDCMake task
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c41bfc2015f29cbb73b33df3594b3a3430af3f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "77630652"
---
# <a name="xdcmake-task"></a>attività XDCMake

Esegue il wrapping dello strumento di documentazione XML (*xdcmake.exe*), che unisce i file di commento del documento XML (con*estensione xdc*) in un file con estensione *XML* .

 Un file con *estensione xdc* viene creato quando si forniscono commenti alla documentazione nel codice sorgente C++ e si compila usando l'opzione del compilatore [/doc](/cpp/build/reference/doc-process-documentation-comments-c-cpp) . Per altre informazioni, vedere [Riferimento a XDCMake](/cpp/build/reference/xdcmake-reference), [Pagina delle proprietà dello strumento generatore di documenti XML](/cpp/build/reference/xml-document-generator-tool-property-pages) e l'opzione della riga di comando per la visualizzazione della Guida (**/?**) relativa a *xdcmake.exe*.

## <a name="remarks"></a>Osservazioni

 Per impostazione predefinita lo strumento *xdcmake.exe* supporta solo alcune opzioni della riga di comando. Vengono supportate altre opzioni quando si specifica l'opzione **/old** della riga di comando.

## <a name="parameters"></a>Parametri

 La tabella seguente descrive i parametri dell'attività **XDCMake**.

|Parametro|Descrizione|
|---------------|-----------------|
|**AdditionalDocumentFile**|Parametro **String []** facoltativo.<br /><br /> Consente di specificare uno o più file aggiuntivi con estensione *xdc* da unire.<br /><br /> Per altre informazioni, vedere la descrizione di **File di documentazione aggiuntivi** in [Pagina delle proprietà dello strumento generatore di documenti XML](/cpp/build/reference/xml-document-generator-tool-property-pages). Vedere anche le opzioni della riga di comando **/Old** e **/FS** per *xdcmake.exe*.|
|**AdditionalOptions**|Parametro **stringa** facoltativo.<br /><br /> Un elenco di opzioni come specificato sulla riga di comando. Ad esempio,/ \<option1>  / \<option2>  / \<option#> . Usare questo parametro per specificare le opzioni che non sono rappresentate da altri parametri dell'attività **XDCMake**.<br /><br /> Per ulteriori informazioni, vedere [riferimento a XDCMake](/cpp/build/reference/xdcmake-reference), [pagine delle proprietà dello strumento generatore di documenti XML](/cpp/build/reference/xml-document-generator-tool-property-pages)e guida della riga di comando (**/?**) per *xdcmake.exe*.|
|**DocumentLibraryDependencies**|Parametro **booleano** facoltativo.<br /><br /> Se è `true` e il progetto corrente contiene una dipendenza a un progetto di libreria statica (con estensione *lib*) nella soluzione, i file con estensione *xdc* di quel progetto di libreria sono inclusi nel file *xml* di output del progetto corrente.<br /><br /> Per altre informazioni, vedere la descrizione di **Dipendenze raccolte documenti** in [Pagina delle proprietà dello strumento generatore di documenti XML](/cpp/build/reference/xml-document-generator-tool-property-pages).|
|**OutputFile**|Parametro **stringa** facoltativo.<br /><br /> Esegue l'override del nome del file di output predefinito. Il nome predefinito è derivato dal nome del primo file con estensione *xdc* elaborato.<br /><br /> Per ulteriori informazioni, vedere l'opzione **/out \<filename> :** in [riferimento a XDCMake](/cpp/build/reference/xdcmake-reference). Vedere anche le opzioni **/old** e **/Fo** della riga di comando per *xdcmake.exe*.|
|**Nome progetto**|Parametro **stringa** facoltativo.<br /><br /> Nome del progetto corrente.|
|**SlashOld**|Parametro **booleano** facoltativo.<br /><br /> Se è `true`, abilita opzioni aggiuntive di *xdcmake.exe*.<br /><br /> Per altre informazioni, vedere l'opzione della riga di comando **/old** relativa a *xdcmake.exe*.|
|**recenti**|Parametro `ITaskItem[]` obbligatorio.<br /><br /> Definisce una matrice di elementi del file di origine MSBuild che può essere usata ed emessa dalle attività.|
|**SuppressStartupBanner**|Parametro **booleano** facoltativo.<br /><br /> Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.<br /><br /> Per altre informazioni, vedere l'opzione **/nologo** in [Riferimento a XDCMake](/cpp/build/reference/xdcmake-reference).|
|**TrackerLogDirectory**|Parametro **stringa** facoltativo.<br /><br /> Specifica la directory per il log di Tracker.|

## <a name="see-also"></a>Vedere anche

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)