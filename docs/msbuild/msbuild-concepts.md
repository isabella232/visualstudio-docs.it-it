---
title: Concetti relativi a MSBuild | Microsoft Docs
description: Informazioni su come specificare componenti e processi di compilazione usando MSBuild, elementi, attività e destinazioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, concepts
ms.assetid: 083b8ba3-e4ad-45af-bb5d-3bc81d406131
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 86b52c8e5207b6dc95af8edad5b7a065d7c415264d5f78c18b269efffd57df08
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121427600"
---
# <a name="msbuild-concepts"></a>Concetti relativi a MSBuild

MSBuild fornisce uno schema XML di base che è possibile usare per controllare la modalità di compilazione del software da parte della piattaforma di compilazione. Per specificare i componenti nella compilazione e come devono essere compilati, usare queste quattro parti di MSBuild: proprietà, elementi, attività e destinazioni.

## <a name="related-topics"></a>Argomenti correlati

| Titolo | Descrizione |
| - | - |
| [proprietà di MSBuild](../msbuild/msbuild-properties.md) | Introduce proprietà e raccolte di proprietà. Le proprietà sono coppie di chiave/valore che è possibile usare per configurare le compilazioni. |
| [Elementi MSBuild](../msbuild/msbuild-items.md) | Presenta gli elementi e le raccolte di elementi. Gli elementi sono input nel sistema di compilazione e, in genere, rappresentano i file. |
| [Destinazioni di MSBuild](../msbuild/msbuild-targets.md) | Spiega come raggruppare le attività in un dato ordine e consentire che determinate sezioni del processo di compilazione vengano richiamate dalla riga di comando. |
| [MSBuild (attività)](../msbuild/msbuild-tasks.md) | Viene illustrato come creare un'unità di codice eseguibile che può essere usata dal MSBuild per eseguire operazioni di compilazione atomica. |
| [Confronto di proprietà ed elementi](../msbuild/comparing-properties-and-items.md) | Confronta le proprietà e gli elementi di MSBuild. Entrambi vengono usati per trasmettere informazioni ad attività, valutare condizioni e archiviare valori a cui poter fare riferimento nel file di progetto. |
| [Caratteri speciali di MSBuild](../msbuild/msbuild-special-characters.md) | Spiega come eseguire l'escape di alcuni caratteri MSBuild riserva per un uso speciale in contesti specifici. |
| [Procedura dettagliata: Creazione di un nuovo file di progetto MSBuild](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | Mostra come creare in modo incrementale un file di progetto di base usando soltanto un editor di testo. |
| [Procedura dettagliata: Uso di MSBuild](../msbuild/walkthrough-using-msbuild.md) | Introduce i blocchi predefiniti di MSBuild e mostra come scrivere, modificare ed eseguire il debug di progetti MSBuild senza chiudere l'ambiente di sviluppo integrato (IDE) di Visual Studio. |
| [Come vengono compilati i progetti in MSBuild](build-process-overview.md) | Descrive il processo di compilazione interno usato all'interno MSBuild |
| [Riferimenti a MSBuild](../msbuild/msbuild-reference.md) | Collegamenti a documenti che contengono informazioni di riferimento. |
| [MSBuild](../msbuild/msbuild.md) | Presenta una panoramica di XML Schema per un file di progetto e illustra come controllare i processi che compilano il software. |
