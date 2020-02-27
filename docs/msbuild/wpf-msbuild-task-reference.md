---
title: Informazioni di riferimento sulle attività MSBuild WPF | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70d994e32b717ff566a2e38acee732c7525d1bb0
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630847"
---
# <a name="wpf-msbuild-task-reference"></a>Informazioni di riferimento sulle attività MSBuild WPF

Il processo di compilazione di Windows Presentation Foundation (WPF) estende Microsoft Build Engine (MSBuild) con un set aggiuntivo di attività di compilazione, tra cui attività di compilazione del markup ed elaborazione di risorse.

## <a name="in-this-section"></a>Contenuto della sezione

- [FileClassifier](../msbuild/fileclassifier-task.md)

 Classifica un set di risorse di origine come quelle che verranno incorporate in un assembly. Se una risorsa non è localizzabile, viene incorporata nell'assembly dell'applicazione principale. In caso contrario, viene incorporata in un assembly satellite.

- [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)

 Genera un assembly se almeno una pagina XAML in un progetto fa riferimento a un tipo dichiarato localmente nel progetto. L'assembly generato viene rimosso dopo il completamento del processo di compilazione o in caso di esito negativo del processo.

- [GetWinFXPath](../msbuild/getwinfxpath-task.md)

 Restituisce la directory del runtime di .NET Framework corrente.

- [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)

 Converte i file di progetto XAML non localizzabili in formato binario compilato.

- [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)

 Esegue la compilazione del markup del secondo passaggio sui file XAML che fanno riferimento ai tipi nello stesso progetto.

- [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)

 Unisce gli attributi di localizzazione e i commenti di uno o più file in formato binario XAML in un singolo file per l'intero assembly.

- [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)

 Incorpora una o più risorse (*jpg*, *ico*, *BMP*, XAML in formato binario e altri tipi di estensione) in un file con estensione *Resources* .

- [UidManager](../msbuild/uidmanager-task.md)

 Controlla, aggiorna o rimuove gli identificatori univoci (UID) per localizzare tutti gli elementi XAML inclusi nei file XAML di origine.

- [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)

 Aggiunge l'elemento **\<HostInBrowser/>** al manifesto dell'applicazione ( *\<NomeProgetto >. exe. manifest*) quando viene compilato un progetto di applicazione browser XAML (XBAP).

## <a name="see-also"></a>Vedere anche

- [MSBuild](../msbuild/msbuild.md)