---
title: Informazioni di riferimento sulle attività MSBuild WPF | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 51a052dea0a828201400086e25880124cb4a05c1
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "54776983"
---
# <a name="wpf-msbuild-task-reference"></a>Informazioni di riferimento sulle attività MSBuild WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Il processo di compilazione di Windows Presentation Foundation (WPF) estende Microsoft Build Engine (MSBuild) con un set aggiuntivo di attività di compilazione, tra cui attività di compilazione del markup ed elaborazione di risorse.  
  
## <a name="in-this-section"></a>In questa sezione  
 [FileClassifier](../msbuild/fileclassifier-task.md)  
 Classifica un set di risorse di origine come quelle che verranno incorporate in un assembly. Se una risorsa non è localizzabile, viene incorporata nell'assembly dell'applicazione principale. In caso contrario, viene incorporata in un assembly satellite.  
  
 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)  
 Genera un assembly se in un progetto almeno una pagina [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] fa riferimento a un tipo dichiarato localmente nel progetto. L'assembly generato viene rimosso dopo il completamento del processo di compilazione o in caso di esito negativo del processo.  
  
 [GetWinFXPath](../msbuild/getwinfxpath-task.md)  
 Restituisce la directory del runtime [!INCLUDE[TLA#tla_winfx](../includes/tlasharptla-winfx-md.md)] corrente.  
  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)  
 Converte i file di progetto [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] non localizzabili in formato binario compilato.  
  
 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)  
 Esegue la compilazione del markup del secondo passaggio sui file [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] che fanno riferimento ai tipi nello stesso progetto.  
  
 [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)  
 Unisce i commenti e gli attributi di localizzazione di uno o più file in formato binario [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] in un singolo file per l'intero assembly.  
  
 [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)  
 Incorpora una o più risorse (jpg, ico, bmp, [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] in formato binario e altri tipi di estensione) in un file con estensione resources.  
  
 [UidManager](../msbuild/uidmanager-task.md)  
 Controlla, aggiorna o rimuove gli identificatori univoci (UID) per localizzare tutti gli elementi [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] inclusi nei file [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] di origine.  
  
 [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)  
 Aggiunge l'elemento **\<hostInBrowser />** al manifesto dell'applicazione (*nomeprogetto*.exe.manifest) quando viene compilato un progetto [!INCLUDE[TLA#tla_xbap](../includes/tlasharptla-xbap-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [MSBuild](http://msdn.microsoft.com/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)
