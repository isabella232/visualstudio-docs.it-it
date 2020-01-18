---
title: Compilazione e creazione di build
ms.date: 07/14/2017
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b5f00b3e71f0deb15d6266640db39751f2ae22f
ms.sourcegitcommit: e3c3d2b185b689c5e32ab4e595abc1ac60b6b9a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2020
ms.locfileid: "76269094"
---
# <a name="compile-and-build-in-visual-studio"></a>Compilazione e creazione in Visual Studio

Per un'introduzione iniziale alla compilazione nell'ambiente IDE, vedere [Procedura dettagliata: Compilazione di un'applicazione](walkthrough-building-an-application.md).

Per compilare un'applicazione è possibile usare uno di questi metodi: IDE di Visual Studio, strumenti da riga di comando MSBuild e Azure Pipelines:

| Metodo di compilazione | Vantaggi |
| --- |--- | --- |
| IDE |- Creazione immediata di build e test in un debugger.<br />- Esecuzione di compilazioni multiprocessore per progetti C++ e C#.<br />- Personalizzazione di vari aspetti del sistema di compilazione. |
| CMake | -Compilare progetti con lo strumento CMake<br />-USA lo stesso sistema di compilazione tra piattaforme Linux e Windows. |
| Riga di comando MSBuild| - Compilazione di progetti senza installare Visual Studio.<br />- Esecuzione di compilazioni multiprocessore per tutti i tipi di progetto.<br />- Personalizzazione della maggior parte delle aree del sistema di compilazione.|
| Azure Pipelines | - Automazione della compilazione come parte di un processo di integrazione continua/recapito continuo.<br />- Implementazione di test automatizzati con ogni compilazione.<br />- Uso di risorse di codice praticamente illimitate per i processi di compilazione.<br />- Modifica del flusso di lavoro di compilazione e creazione di attività di compilazione per eseguire attività personalizzate specifiche.|

La documentazione di questa sezione approfondisce i dettagli del processo di compilazione basato su IDE. Per informazioni sugli altri metodi, vedere rispettivamente [MSBuild](../msbuild/msbuild.md) e [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Compilazione e creazione in Visual Studio per Mac](/visualstudio/mac/compiling-and-building).

## <a name="overview-of-building-from-the-ide"></a>Panoramica della compilazione nell'ambiente IDE

Quando si crea un progetto, Visual Studio crea configurazioni della build predefinite per il progetto e la soluzione che contiene il progetto.  Queste configurazioni definiscono come vengono compilati e distribuiti i progetti e le soluzioni. Le configurazioni di progetto, in particolare, sono univoche per la piattaforma di destinazione (ad esempio Windows o Linux) e il tipo di compilazione (ad esempio, di debug o di rilascio). È possibile modificare queste configurazioni come desiderato e anche creare configurazioni personalizzate in base alle esigenze.

Per un'introduzione iniziale alla compilazione nell'ambiente IDE, vedere [Procedura dettagliata: Compilazione di un'applicazione](walkthrough-building-an-application.md).

Quindi vedere [Compilazione e pulizia di progetti e soluzioni in Visual Studio](building-and-cleaning-projects-and-solutions-in-visual-studio.md) per informazioni sulle personalizzazioni applicabili ai diversi aspetti del processo. Le personalizzazioni includono la [modifica della directory dell'output](how-to-change-the-build-output-directory.md), la [definizione di eventi di compilazione personalizzati](specifying-custom-build-events-in-visual-studio.md), la [gestione delle dipendenze del progetto](how-to-create-and-remove-project-dependencies.md), la [gestione dei file di log di compilazione](how-to-view-save-and-configure-build-log-files.md) e la [disattivazione della visualizzazione degli avvisi del compilatore](how-to-suppress-compiler-warnings.md).

Successivamente è possibile esplorare molte altre attività:
- [Informazioni sulle configurazioni della build](understanding-build-configurations.md)
- [Informazioni sulle piattaforme di compilazione](understanding-build-platforms.md)
- [Gestire le proprietà di progetti e soluzioni](managing-project-and-solution-properties.md).
- Definizione degli eventi di compilazione in [C#](how-to-specify-build-events-csharp.md) e [Visual Basic](how-to-specify-build-events-visual-basic.md)
- [Impostazione delle opzioni di compilazione](reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Compilazione di più progetti in parallelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).

## <a name="see-also"></a>Vedere anche

- [Compilazione di progetti di siti Web](https://msdn.microsoft.com/Library/a9cbb88c-8fff-4c67-848b-98fbfd823193)
- [Compilazione e creazione (Visual Studio per Mac)](/visualstudio/mac/compiling-and-building)
- [Progetti CMake in Visual Studio](/cpp/build/cmake-projects-in-visual-studio)
