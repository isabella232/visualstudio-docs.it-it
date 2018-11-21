---
title: Compilazione e creazione in Visual Studio
ms.date: 07/14/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9d2ad9e3e6644f3f0ffc2d4fbf163968f16065f3
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349133"
---
# <a name="compile-and-build-in-visual-studio"></a>Compilazione e creazione in Visual Studio

Quando si compila il codice sorgente, il motore di compilazione crea assembly e applicazioni eseguibili. A livello generale il processo di compilazione è molto simile tra progetti di tipi diversi, quali Windows, ASP.NET, app per dispositivi mobili e altri ancora. Il processo di compilazione è anche simile tra linguaggi di programmazione come C#, Visual Basic, C++ e F#.

Compilando spesso il codice è possibile identificare rapidamente gli errori in fase di compilazione, ad esempio sintassi non corretta, parole chiave con errori di digitazione e tipi non corrispondenti. È inoltre possibile rilevare e risolvere gli errori di runtime, ad esempio errori logici e semantici, compilando ed eseguendo le versioni di debug del codice.

Una compilazione riuscita conferma che la sintassi del codice sorgente dell'applicazione è corretta e che tutti i riferimenti statici a librerie, assembly e altri componenti possono essere risolti. Il risultato è un file eseguibile dell'applicazione che può essere testato per il funzionamento corretto sia in un [ambiente di debug](../debugger/index.md), sia mediante vari test manuali e automatici per la [convalida della qualità del codice](../test/improve-code-quality.md). Dopo aver testato completamente l'applicazione è possibile compilare una versione di rilascio da distribuire ai clienti. Per un'introduzione a questo processo, vedere [Procedura dettagliata: Compilazione di un'applicazione](../ide/walkthrough-building-an-application.md).

Per compilare un'applicazione è possibile usare uno di questi metodi: IDE di Visual Studio, strumenti da riga di comando MSBuild e Azure Pipelines:

| Metodo di compilazione | Vantaggi |
| --- |--- | --- |
| IDE |- Creazione immediata di build e test in un debugger.<br />- Esecuzione di compilazioni multiprocessore per progetti C++ e C#.<br />- Personalizzazione di vari aspetti del sistema di compilazione. |
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