---
title: Concetti relativi a MSBuild | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MSBuild, concepts
ms.assetid: 083b8ba3-e4ad-45af-bb5d-3bc81d406131
caps.latest.revision: "13"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e57abdc78bc5b5844959fe2e3077688ec496df49
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="msbuild-concepts"></a>Concetti relativi a MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fornisce un XML Schema di base che è possibile usare per controllare come la piattaforma di compilazione compila il software. Per specificare i componenti nella compilazione e come devono essere compilati, usare queste quattro parti di MSBuild: proprietà, elementi, attività e destinazioni.  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Proprietà di MSBuild](../msbuild/msbuild-properties.md)|Introduce proprietà e raccolte di proprietà. Le proprietà sono coppie di chiave/valore che è possibile usare per configurare le compilazioni.|  
|[Elementi](../msbuild/msbuild-items.md)|Descrive i concetti generali su cui si basa il formato di file di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] e le interazioni fra le singole parti del formato.|  
|[Destinazioni](../msbuild/msbuild-targets.md)|Spiega come raggruppare le attività in un dato ordine e consentire che determinate sezioni del processo di compilazione vengano richiamate dalla riga di comando.|  
|[Attività](../msbuild/msbuild-tasks.md)|Mostra come creare un'unità di codice eseguibile che [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] può usare per eseguire operazioni di compilazione atomiche.|  
|[Confronto di proprietà ed elementi](../msbuild/comparing-properties-and-items.md)|Confronta le proprietà e gli elementi di MSBuild. Entrambi vengono usati per trasmettere informazioni ad attività, valutare condizioni e archiviare valori a cui poter fare riferimento nel file di progetto.|  
|[Caratteri speciali di MSBuild](../msbuild/msbuild-special-characters.md)|Illustra come usare caratteri di escape per alcuni caratteri che in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sono riservati a contesti specifici.|  
|[Procedura dettagliata: creazione di un nuovo file di progetto MSBuild](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)|Mostra come creare in modo incrementale un file di progetto di base usando soltanto un editor di testo.|  
|[Procedura dettagliata: uso di MSBuild](../msbuild/walkthrough-using-msbuild.md)|Introduce i blocchi predefiniti di MSBuild e mostra come scrivere, modificare ed eseguire il debug di progetti MSBuild senza chiudere l'ambiente di sviluppo integrato (IDE) di Visual Studio.|  
|[Riferimenti a MSBuild](../msbuild/msbuild-reference.md)|Collegamenti a documenti che contengono informazioni di riferimento.|  
|[MSBuild](../msbuild/msbuild.md)|Presenta una panoramica di XML Schema per un file di progetto e illustra come controllare i processi che compilano il software.|