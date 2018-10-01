---
title: Attività MSBuild specifiche di Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks specific to Visual C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af8de092a21f0e37dc523b6a8604c3c55316c6db
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518373"
---
# <a name="msbuild-tasks-specific-to-visual-c"></a>Attività MSBuild specifiche di Visual C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [attività MSBuild specifiche di Visual C++](https://docs.microsoft.com/visualstudio/msbuild/msbuild-tasks-specific-to-visual-cpp).  
  
  
Le attività forniscono il codice che viene eseguito durante il processo di compilazione. Quando si installa Visual C++, sono disponibili le attività seguenti, oltre a quelle installate con [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Per altre informazioni, vedere [Cenni preliminari su MSBuild (Visual C++)](http://msdn.microsoft.com/library/dd258f6f-ab51-48d9-b274-f7ba911d05ca).  
  
 Ogni attività dispone di parametri propri e anche dei parametri seguenti.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`Condition`|Parametro `String` facoltativo.<br /><br /> Espressione `Boolean` usata dal motore di [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] per determinare se l'attività verrà eseguita. Per altre informazioni sulle condizioni supportate da [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], vedere [Condizioni](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Parametro facoltativo. Può contenere uno dei valori seguenti:<br /><br /> -   **WarnAndContinue** o **true**. Quando un'attività ha esito negativo, l'esecuzione delle attività successive nell'elemento [Target](../msbuild/target-element-msbuild.md) e della compilazione continua e tutti gli errori delle attività vengono considerati avvisi.<br />-   **ErrorAndContinue**. Quando un'attività ha esito negativo, l'esecuzione delle attività successive nell'elemento `Target` e della compilazione continua e tutti gli errori delle attività vengono considerati errori.<br />-   **ErrorAndStop** o **false** (impostazione predefinita). Quando un'attività ha esito negativo, le attività rimanenti nell'elemento `Target` e la compilazione non vengono eseguite e l'intero elemento `Target` e la compilazione vengono considerati come non riusciti.<br /><br /> Le versioni di .NET Framework precedenti alla 4.5 supportano solo i valori `true` e `false`.<br /><br /> Per altre informazioni, vedere [Procedura: Ignorare gli errori nelle attività](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Attività BscMake](../msbuild/bscmake-task.md)|Esegue il wrapping dello strumento Microsoft Browse Information Maintenance Utility (bscmake.exe).|  
|[Attività CL](../msbuild/cl-task.md)|Esegue il wrapping dello strumento del compilatore Visual C++ (cl.exe).|  
|[Attività CPPClean](../msbuild/cppclean-task.md)|Elimina i file temporanei creati da MSBuild al momento della compilazione di un progetto Visual C++.|  
|[Attività LIB](../msbuild/lib-task.md)|Esegue il wrapping dello strumento Gestione librerie Microsoft a 32 bit (lib.exe).|  
|[Attività Link](../msbuild/link-task.md)|Esegue il wrapping dello strumento linker di Visual C++ (link.exe).|  
|[Attività MIDL](../msbuild/midl-task.md)|Esegue il wrapping dello strumento compilatore MIDL (Microsoft Interface Definition Language) (midl.exe).|  
|[Attività MT](../msbuild/mt-task.md)|Esegue il wrapping dello strumento manifesto Microsoft (mt.exe).|  
|[Attività RC](../msbuild/rc-task.md)|Esegue il wrapping dello strumento Compilatore di risorse di Microsoft Windows (rc.exe).|  
|[Attività SetEnv](../msbuild/setenv-task.md)|Imposta o elimina il valore di una variabile di ambiente specificata.|  
|[Attività VCMessage](../msbuild/vcmessage-task.md)|Registra i messaggi di avviso e i messaggi di errore durante una compilazione.|  
|[Attività XDCMake](../msbuild/xdcmake-task.md)|Esegue il wrapping dello strumento Documentazione XML (xdcmake.exe) che unisce i file di commento (.xdc) del documento XML in un file con estensione xml.|  
|[Attività XSD](../msbuild/xsd-task.md)|Esegue il wrapping dello strumento XML Schema Definition (xsd.exe), che genera file di schema o di classe da un'origine.|  
|[Riferimenti a MSBuild](../msbuild/msbuild-reference.md)|Descrive gli elementi del sistema MSBuild.|  
|[Attività](../msbuild/msbuild-tasks.md)|Descrive le attività, che sono unità di codice che possono essere combinate per produrre una compilazione.|  
|[Scrittura di attività](../msbuild/task-writing.md)|Descrive come creare un'attività.|



