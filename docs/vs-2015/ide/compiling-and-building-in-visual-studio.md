---
title: Compilazione e creazione di build
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7694f0f725af8a20ff3a5a01753b0669c0fd5d9f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60067352"
---
# <a name="compiling-and-building-in-visual-studio"></a>Compilazione e creazione in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile utilizzare Visual Studio per sviluppare applicazioni e creare a intervalli frequenti gli assembly e i programmi eseguibili durante il ciclo di sviluppo. Compilando spesso il codice, è possibile identificare più rapidamente errori in fase di compilazione, ad esempio sintassi non corretta, parole chiave non digitate correttamente e tipi non corrispondenti. È inoltre possibile rilevare e risolvere gli errori di runtime, ad esempio errori logici e semantici, compilando frequentemente ed eseguendo le versioni di debug del codice.

 Quando un progetto o una soluzione è stato completamente sviluppato e sufficientemente sottoposto a debug, è possibile compilare i relativi componenti in una compilazione di rilascio. Per impostazione predefinita, una compilazione di rilascio è ottimizzata e progettata per essere di dimensioni minori ed essere eseguita più velocemente di una versione di debug. Per altre informazioni, vedere [Procedura dettagliata: Compilazione di un'applicazione](../ide/walkthrough-building-an-application.md).

## <a name="choosing-a-build-method"></a>Scelta di un metodo di compilazione
 È possibile compilare un'applicazione utilizzando le opzioni di compilazione predefinite nell'IDE, in un prompt dei comandi o tramite Team Foundation Build. Ognuna di queste opzioni utilizza MSBuild come tecnologia sottostante e ogni approccio presenta vantaggi specifici, come illustrato nella tabella seguente.

|Metodo di compilazione|Vantaggi|Per altre informazioni|
|------------------|--------------|--------------------------|
|Utilizzo di IDE|- È più semplice creare ed eseguire compilazioni immediatamente.<br />- È possibile eseguire compilazioni multiprocessore per progetti C++ e C#.<br />- È possibile personalizzare alcuni aspetti del sistema di compilazione.|[Building and Cleaning Projects and Solutions in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md) (Compilazione e pulizia di progetti e soluzioni in Visual Studio)|
|Esecuzione di una riga di comando di MSBuild|- È possibile compilare progetti senza installare Visual Studio.<br />- È possibile eseguire compilazioni multiprocessore per tutti i tipi di progetto.<br />- È possibile personalizzare la maggior parte delle aree del sistema di compilazione.|[MSBuild](../msbuild/msbuild.md)|
|Uso di Team Foundation Build|- È possibile automatizzare il processo di compilazione. È possibile ad esempio compilare uno o più progetti di notte o ogni volta che il codice viene controllato. È inoltre possibile compilare progetti nei server di compilazione condivisi anziché nel computer di sviluppo.<br />- È possibile specificare rapidamente il codice da compilare, i test da eseguire e altre opzioni comuni.<br />- È possibile modificare il flusso di lavoro di compilazione e, se necessario, creare attività di compilazione per eseguire attività estremamente personalizzate.|[Compilare l'applicazione](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)|

## <a name="building-from-the-ide"></a>Compilazione nell'IDE
 Quando si crea un progetto, vengono definite le relative configurazioni di compilazione predefinite a cui viene assegnata una configurazione di compilazione della soluzione per fornire un contesto per le compilazioni. Le configurazioni per la soluzione definiscono il modo in cui i progetti nella soluzione vengono compilati e distribuiti. Le configurazioni di progetto sono un set di proprietà di progetto univoche per una piattaforma e un tipo di compilazione (ad esempio versione Win32). È possibile modificare le configurazioni predefinite e creare configurazioni personalizzate. Per altre informazioni, vedere [Introduzione a Creazione progetti](http://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7) e [NIB procedura: Modificare le proprietà del progetto e le impostazioni di configurazione](http://msdn.microsoft.com/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67).

 Nell'IDE è possibile eseguire le attività aggiuntive seguenti:

- [Modificare la directory di output della build](../ide/how-to-change-the-build-output-directory.md).

- [Identificare i progetti dipendenti dall'output di un altro progetto per eseguire correttamente la compilazione](../ide/how-to-create-and-remove-project-dependencies.md).

- [Modificare la quantità di informazioni inclusa nel log di compilazione o nella finestra di output per le compilazioni](../ide/how-to-view-save-and-configure-build-log-files.md).

- [Nascondere avvisi del compilatore specifici per Visual C#, Visual C++ o Visual Basic](../ide/how-to-suppress-compiler-warnings.md).

- [Specificare le azioni personalizzate precedenti e successive alla compilazione per una compilazione](../ide/specifying-custom-build-events-in-visual-studio.md).

- Migliorare le prestazioni di compilazione utilizzando compilazioni parallele. Per altre informazioni, vedere [Building Multiple Projects in Parallel with MSBuild](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md) (Compilazione di più progetti in parallelo con MSBuild) o il post di blog [Tuning C++ build parallelism](http://blogs.msdn.com/b/msbuild/archive/2010/03/08/tuning-c-build-parallelism-in-vs2010.aspx) (Ottimizzazione del parallelismo di compilazione C++).

## <a name="see-also"></a>Vedere anche
 [Procedura dettagliata: Compilazione di un'applicazione](../ide/walkthrough-building-an-application.md) [informazioni sulle configurazioni della Build](../ide/understanding-build-configurations.md) [informazioni sulle piattaforme di compilazione](../ide/understanding-build-platforms.md) [compilazione di progetti di siti Web (in fase di compilazione)](http://msdn.microsoft.com/library/a9cbb88c-8fff-4c67-848b-98fbfd823193) [ Come si fa: Creare e rimuovere dipendenze del progetto](../ide/how-to-create-and-remove-project-dependencies.md)
