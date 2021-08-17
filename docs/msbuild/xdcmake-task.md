---
title: Attività XDCMake | Microsoft Docs
description: Informazioni su come MSBuild'attività XDCMake per eseguire il wrapping dello strumento documentazione XML xdcmake.exe, che unisce i file di commento del documento XML in un file .xml xml.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: b5821f567ae06717665f055f23ec19348855d6da
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108148"
---
# <a name="xdcmake-task"></a>attività XDCMake

Esegue il wrapping dello strumento documentazione XML (*xdcmake.exe*), che unisce i file di commento del documento XML (con estensione *xdc)* in un file *.xml* file.

 Un file *con estensione xdc* viene creato quando si forniscono commenti alla documentazione nel codice sorgente C++ e si esegue la compilazione usando l'opzione del compilatore [/doc.](/cpp/build/reference/doc-process-documentation-comments-c-cpp) Per altre informazioni, vedere [Riferimento a XDCMake](/cpp/build/reference/xdcmake-reference), [Pagina delle proprietà dello strumento generatore di documenti XML](/cpp/build/reference/xml-document-generator-tool-property-pages) e l'opzione della riga di comando per la visualizzazione della Guida (**/?**) relativa a *xdcmake.exe*.

## <a name="remarks"></a>Commenti

 Per impostazione predefinita lo strumento *xdcmake.exe* supporta solo alcune opzioni della riga di comando. Vengono supportate altre opzioni quando si specifica l'opzione **/old** della riga di comando.

## <a name="parameters"></a>Parametri

 La tabella seguente descrive i parametri dell'attività **XDCMake**.

|Parametro|Descrizione|
|---------------|-----------------|
|**AdditionalDocumentFile**|Parametro **Facoltativo String[].**<br /><br /> Consente di specificare uno o più file aggiuntivi con estensione *xdc* da unire.<br /><br /> Per altre informazioni, vedere la descrizione di **File di documentazione aggiuntivi** in [Pagina delle proprietà dello strumento generatore di documenti XML](/cpp/build/reference/xml-document-generator-tool-property-pages). Vedere anche le opzioni della riga di comando **/old** e **/Fs** *perxdcmake.exe*.|
|**AdditionalOptions**|Parametro **String** facoltativo.<br /><br /> Un elenco di opzioni come specificato sulla riga di comando. Ad esempio, / \<option1>  / \<option2>  / \<option#> . Usare questo parametro per specificare le opzioni che non sono rappresentate da altri parametri dell'attività **XDCMake**.<br /><br /> Per altre informazioni, vedere Informazioni di riferimento [su XDCMake](/cpp/build/reference/xdcmake-reference), Pagine delle proprietà dello strumento generatore di documenti [XML](/cpp/build/reference/xml-document-generator-tool-property-pages)e Guida della riga di comando (**/?**) *per* xdcmake.exe.|
|**DocumentLibraryDependencies**|Parametro **booleano** facoltativo.<br /><br /> Se è `true` e il progetto corrente contiene una dipendenza a un progetto di libreria statica (con estensione *lib*) nella soluzione, i file con estensione *xdc* di quel progetto di libreria sono inclusi nel file *xml* di output del progetto corrente.<br /><br /> Per altre informazioni, vedere la descrizione di **Dipendenze raccolte documenti** in [Pagina delle proprietà dello strumento generatore di documenti XML](/cpp/build/reference/xml-document-generator-tool-property-pages).|
|**Outputfile**|Parametro **String** facoltativo.<br /><br /> Esegue l'override del nome del file di output predefinito. Il nome predefinito è derivato dal nome del primo file con estensione *xdc* elaborato.<br /><br /> Per altre informazioni, vedere **l'opzione \<filename> /out:** in Informazioni di riferimento su [XDCMake.](/cpp/build/reference/xdcmake-reference) Vedere anche le opzioni **/old** e **/Fo** della riga di comando per *xdcmake.exe*.|
|**Nome progetto**|Parametro **String** facoltativo.<br /><br /> Nome del progetto corrente.|
|**SlashOld**|Parametro **booleano** facoltativo.<br /><br /> Se è `true`, abilita opzioni aggiuntive di *xdcmake.exe*.<br /><br /> Per altre informazioni, vedere l'opzione della riga di comando **/old** relativa a *xdcmake.exe*.|
|**recenti**|Parametro `ITaskItem[]` obbligatorio.<br /><br /> Definisce una matrice di elementi del file di origine MSBuild che può essere usata ed emessa dalle attività.|
|**SuppressStartupBanner**|Parametro **booleano** facoltativo.<br /><br /> Se `true`, impedisce la visualizzazione del messaggio sul copyright e sul numero di versione all'avvio dell'attività.<br /><br /> Per altre informazioni, vedere l'opzione **/nologo** in [Riferimento a XDCMake](/cpp/build/reference/xdcmake-reference).|
|**TrackerLogDirectory**|Parametro **String** facoltativo.<br /><br /> Specifica la directory per il log di Tracker.|

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)