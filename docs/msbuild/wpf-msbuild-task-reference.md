---
title: Informazioni di riferimento sulle attività MSBuild WPF | Microsoft Docs
description: Vedere le informazioni di riferimento sull'attività per il processo di compilazione Windows Presentation Foundation (WPF), che estende MSBuild con attività aggiuntive.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WPF MSBuild task reference [WPF MSBuild], term/definition table
- build tasks [WPF MSBuild], Microsoft build engine
- build tasks using the Microsoft build engine [WPF MSBuild], compile markup and process resources
- WPF MSBuild task reference [WPF MSBuild]
ms.assetid: 96df0370-e50f-4ffc-9771-b12fb8721143
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 19a5fbd6da07648be784b155e3fb6b4dc4e78824
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076958"
---
# <a name="wpf-msbuild-task-reference"></a>Informazioni di riferimento sulle attività MSBuild WPF

Il processo di compilazione di Windows Presentation Foundation (WPF) estende Microsoft Build Engine (MSBuild) con un set aggiuntivo di attività di compilazione, tra cui attività di compilazione del markup ed elaborazione di risorse.

## <a name="in-this-section"></a>Contenuto della sezione

- [FileClassifier](../msbuild/fileclassifier-task.md)

 Classifica un set di risorse di origine come quelle che verranno incorporate in un assembly. Se una risorsa non è localizzabile, viene incorporata nell'assembly dell'applicazione principale. In caso contrario, viene incorporata in un assembly satellite.

- [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)

 Genera un assembly se almeno una pagina XAML in un progetto fa riferimento a un tipo dichiarato localmente nel progetto. L'assembly generato viene rimosso dopo il completamento del processo di compilazione o in caso di esito negativo del processo.

- [GetWinFXPath](../msbuild/getwinfxpath-task.md)

 Restituisce la directory del runtime .NET Framework corrente.

- [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)

 Converte i file di progetto XAML non localizzabili in formato binario compilato.

- [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)

 Esegue la compilazione del markup del secondo passaggio su file XAML che fanno riferimento a tipi nello stesso progetto.

- [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)

 Unisce gli attributi di localizzazione e i commenti di uno o più file di formato binario XAML in un unico file per l'intero assembly.

- [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)

 Incorpora una o più risorse (*.jpg*, *.ico*, *.bmp*, XAML in formato binario e altri tipi di estensione) in un file con *estensione resources.*

- [UidManager](../msbuild/uidmanager-task.md)

 Controlla, aggiorna o rimuove gli identificatori univoci (UID) per localizzare tutti gli elementi XAML inclusi nei file XAML di origine.

- [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)

 Aggiunge **\<hostInBrowser />** l'elemento al manifesto dell'applicazione (*\<projectname>.exe.manifest*) quando viene compilato un progetto di applicazione browser XAML (XBAP).

## <a name="see-also"></a>Vedi anche

- [MSBuild](../msbuild/msbuild.md)