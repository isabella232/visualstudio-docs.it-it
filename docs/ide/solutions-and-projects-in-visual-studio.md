---
title: Soluzioni e progetti in Visual Studio
ms.date: 10/05/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.addnewsolutionitem
- vs.environment.projects
- vs.openproject
- vs.addnewitem
- vs.addexistingitem
- VS.SolutionExplorer
- vs.newproject
- vs.addexistingsolutionitem
- vs.environment.solutions
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solution items [Visual Studio]
- solutions [Visual Studio]
- project items [Visual Studio]
- solutions [Visual Studio], designing
- projects [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8dc94838423cea7eeab8cef6357267609394352b
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="solutions-and-projects-in-visual-studio"></a>Soluzioni e progetti in Visual Studio

## <a name="projects"></a>Progetti

Quando si crea un’app, un sito Web, un plug-in e così via in Visual Studio, si comincia con un *progetto*. In senso logico, un progetto contiene tutti i file del codice sorgente, icone, immagini, file di dati e così via, compilati in un file eseguibile, una libreria o un sito Web. Un progetto contiene anche le impostazioni del compilatore e altri file di configurazione che potrebbero essere necessari per i vari servizi o componenti con cui il programma comunica.

> [!NOTE]
> Non è necessario usare soluzioni o progetti in Visual Studio per modificare, compilare ed eseguire il debug del codice. È sufficiente aprire la cartella che contiene i file di origine in Visual Studio e iniziare ad apportare le modifiche. Per altre informazioni, vedere [Sviluppare codice in Visual Studio senza progetti o soluzioni](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

Un progetto è definito in un file XML con un'estensione di tipo *.vbproj*, *.csproj*, o *.vcxproj*. Questo file contiene una gerarchia di cartelle virtuali e i percorsi a tutti gli elementi del progetto. Contiene anche le impostazioni di compilazione.

> [!TIP]
> Per esaminare il contenuto di un file di progetto in Visual Studio, scaricare prima il progetto selezionando il nome del progetto in **Esplora soluzioni** e scegliendo **Scarica progetto** dal menu di scelta rapida. Aprire di nuovo il menu di scelta rapida e scegliere **Modifica \<nomeprogetto\>**.

In Visual Studio, il file di progetto viene utilizzato da **Esplora soluzioni** per visualizzare il contenuto e le impostazioni del progetto. Quando si compila il progetto, il motore MSBuild utilizza il file di progetto per creare il file eseguibile. È anche possibile personalizzare i progetti per produrre altri tipi di output.

## <a name="solutions"></a>Soluzioni

Un progetto è contenuto all'interno di una *soluzione*. Una soluzione contiene uno o più progetti correlati, insieme alle informazioni di compilazione, alle impostazioni della finestra di Visual Studio e a vari file non associati a un progetto particolare. Una soluzione è descritta da un file di testo (estensione *.sln*) con un formato univoco specifico, di cui non è prevista la modifica manuale.

Una soluzione ha un file con estensione *suo* associato che archivia le impostazioni, le preferenze e le informazioni di configurazione per ogni utente che ha lavorato al progetto.

## <a name="create-new-projects"></a>Crea nuovi progetti

Il modo più semplice per creare un nuovo progetto è iniziare da un modello di progetto per un tipo particolare di applicazione o sito Web. Un modello di progetto è costituito da un set di base di file di codice, file di configurazione, risorse e impostazioni già generati. Questi modelli sono quelli visualizzati nella finestra di dialogo **Nuovo progetto** o **Nuovo sito Web** quando si sceglie **File** > **Nuovo** > **Progetto** o **File** > **Nuovo** > **Sito Web**. Per altre informazioni, vedere [Creare soluzioni e progetti](../ide/creating-solutions-and-projects.md).

È inoltre possibile creare modelli di progetto e modelli di elemento personalizzati. Per altre informazioni, vedere [Creare modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md).

## <a name="manage-projects-in-solution-explorer"></a>Gestire progetti in Esplora soluzioni

Dopo aver creato un nuovo progetto, è possibile usare **Esplora soluzioni** per visualizzare e gestire il progetto e la soluzione, nonché gli elementi associati. La figura seguente illustra **Esplora soluzioni** con una soluzione C# contenente due progetti.

![Esplora soluzioni](../ide/media/vs2015_solution_explorer.png "vs2015_solution_explorer")

## <a name="see-also"></a>Vedere anche

- [IDE di Visual Studio](../ide/visual-studio-ide.md)