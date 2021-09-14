---
title: Compilazione e creazione di build
description: Informazioni su come usare il Visual Studio di compilazione IDE, il metodo di compilazione MSBuild strumenti da riga di comando o Azure Pipelines metodo di compilazione per compilare un'applicazione.
ms.custom: SEO-VS-2020
ms.date: 07/14/2017
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 61abd28890fe92918c8ee2c9067820a781fac9c4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627239"
---
# <a name="compile-and-build-in-visual-studio"></a>Compilazione e creazione in Visual Studio

Per una prima introduzione alla compilazione all'interno dell'IDE, vedere [Procedura dettagliata: Compilazione di un'applicazione](walkthrough-building-an-application.md).

Per compilare un'applicazione è possibile usare uno di questi metodi: IDE di Visual Studio, strumenti da riga di comando MSBuild e Azure Pipelines:

| Metodo di compilazione | Vantaggi |
| --- |--- | --- |
| IDE |- Creazione immediata di build e test in un debugger.<br />- Esecuzione di compilazioni multiprocessore per progetti C++ e C#.<br />- Personalizzazione di vari aspetti del sistema di compilazione. |
| CMake | - Compilare progetti con lo strumento CMake<br />- Usare lo stesso sistema di compilazione in linux e Windows piattaforme. |
| Riga di comando MSBuild| - Compilazione di progetti senza installare Visual Studio.<br />- Esecuzione di compilazioni multiprocessore per tutti i tipi di progetto.<br />- Personalizzazione della maggior parte delle aree del sistema di compilazione.|
| Azure Pipelines | - Automazione della compilazione come parte di un processo di integrazione continua/recapito continuo.<br />- Implementazione di test automatizzati con ogni compilazione.<br />- Uso di risorse di codice praticamente illimitate per i processi di compilazione.<br />- Modifica del flusso di lavoro di compilazione e creazione di attività di compilazione per eseguire attività personalizzate specifiche.|

La documentazione di questa sezione approfondisce i dettagli del processo di compilazione basato su IDE. Per informazioni sugli altri metodi, vedere rispettivamente [MSBuild](../msbuild/msbuild.md) e [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true).

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Compilazione e creazione in Visual Studio per Mac](/visualstudio/mac/compiling-and-building).

## <a name="overview-of-building-from-the-ide"></a>Panoramica della compilazione nell'ambiente IDE

Quando si crea un progetto, Visual Studio crea configurazioni della build predefinite per il progetto e la soluzione che contiene il progetto.  Queste configurazioni definiscono come vengono compilati e distribuiti i progetti e le soluzioni. Le configurazioni di progetto, in particolare, sono univoche per la piattaforma di destinazione (ad esempio Windows o Linux) e il tipo di compilazione (ad esempio, di debug o di rilascio). È possibile modificare queste configurazioni come desiderato e anche creare configurazioni personalizzate in base alle esigenze.

Per una prima introduzione alla compilazione all'interno dell'IDE, vedere [Procedura dettagliata: Compilazione di un'applicazione](walkthrough-building-an-application.md).

Quindi vedere [Compilazione e pulizia di progetti e soluzioni in Visual Studio](building-and-cleaning-projects-and-solutions-in-visual-studio.md) per informazioni sulle personalizzazioni applicabili ai diversi aspetti del processo. Le personalizzazioni includono la [modifica della directory dell'output](how-to-change-the-build-output-directory.md), la [definizione di eventi di compilazione personalizzati](specifying-custom-build-events-in-visual-studio.md), la [gestione delle dipendenze del progetto](how-to-create-and-remove-project-dependencies.md), la [gestione dei file di log di compilazione](how-to-view-save-and-configure-build-log-files.md) e la [disattivazione della visualizzazione degli avvisi del compilatore](how-to-suppress-compiler-warnings.md).

Successivamente è possibile esplorare molte altre attività:
- [Informazioni sulle configurazioni della build](understanding-build-configurations.md)
- [Informazioni sulle piattaforme di compilazione](understanding-build-platforms.md)
- [Gestire le proprietà del progetto e della soluzione](managing-project-and-solution-properties.md).
- Definizione degli eventi di compilazione in [C#](how-to-specify-build-events-csharp.md) e [Visual Basic](how-to-specify-build-events-visual-basic.md)
- [Impostazione delle opzioni di compilazione](reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Compilare più progetti in parallelo.](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)

## <a name="see-also"></a>Vedi anche

- [Compilazione di progetti di siti Web](/previous-versions/hwxa5aha(v=vs.140))
- [Compilazione e creazione (Visual Studio per Mac)](/visualstudio/mac/compiling-and-building)
- [Progetti CMake in Visual Studio](/cpp/build/cmake-projects-in-visual-studio)