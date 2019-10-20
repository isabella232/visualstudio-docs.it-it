---
title: Soluzioni e progetti
ms.date: 10/05/2017
ms.topic: conceptual
f1_keywords:
- vs.addnewitem
- vs.addnewsolutionitem
- vs.openproject
- vs.addexistingitem
- vs.addexistingsolutionitem
- vs.environment.projects
- vs.environment.solutions
- VS.SolutionExplorer
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ca611d7ae1faa86ae7878b2f824ce27b9872713
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72621572"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Soluzioni e progetti in Visual Studio

Questa pagina descrive il concetto di *progetto* e una *soluzione* in Visual Studio. Vengono inoltre illustrati brevemente la finestra degli strumenti Esplora soluzioni e la modalità di creazione di un nuovo progetto.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Progetti e soluzioni in Visual Studio per Mac](/visualstudio/mac/projects-and-solutions).

## <a name="projects"></a>Progetti

Quando si crea un'app o un sito Web in Visual Studio, si inizia con un *progetto*. In senso logico, un progetto contiene tutti i file compilati in un file eseguibile, in una libreria o in un sito Web. Tali file possono includere codice sorgente, icone, immagini, file di dati e così via. Un progetto contiene anche le impostazioni del compilatore e altri file di configurazione che potrebbero essere necessari per i vari servizi o componenti con cui il programma comunica.

### <a name="project-file"></a>File di progetto

Visual Studio USA [MSBuild](../msbuild/msbuild.md) per compilare ogni progetto in una soluzione e ogni progetto contiene un file di progetto MSBuild. L'estensione di file riflette il tipo di progetto, ad esempio un C# progetto (con estensione csproj), un progetto di Visual Basic (vbproj) o un progetto di database (. dbproj). Il file di progetto è un documento XML contenente tutte le informazioni e le istruzioni necessarie a MSBuild per compilare il progetto, inclusi il contenuto, i requisiti della piattaforma, le informazioni sul controllo delle versioni, le impostazioni del server Web o del server di database e le attività per eseguire.

I file di progetto sono basati sulla [XML schema MSBuild](../msbuild/msbuild-project-file-schema-reference.md). Per esaminare il contenuto dei [file di progetto in stile SDK](../msbuild/how-to-use-project-sdk.md) più recenti in Visual Studio, fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **modifica \<projectname \>** . Per esaminare il contenuto di .NET Framework e di altri progetti dello stile, scaricare prima il progetto (fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e selezionare **Scarica progetto**). Quindi, fare clic con il pulsante destro del mouse sul progetto e scegliere **modifica \<projectname \>** .

> [!NOTE]
> Non è necessario usare soluzioni o progetti in Visual Studio per modificare, compilare ed eseguire il debug del codice. È sufficiente aprire la cartella che contiene i file di origine in Visual Studio e iniziare ad apportare le modifiche. Per altre informazioni, vedere [Sviluppare codice in Visual Studio senza progetti o soluzioni](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions"></a>Soluzioni

Un progetto è contenuto all'interno di una *soluzione*. Nonostante il nome, una soluzione non è una "risposta". È semplicemente un contenitore che include uno o più progetti correlati, insieme a informazioni di compilazione, impostazioni della finestra di Visual Studio e a vari file non associati a un progetto particolare. Una soluzione è descritta da un file di testo (con estensione *sln*) con un formato univoco specifico, per il quale non è prevista la modifica manuale.

Per archiviare le impostazioni delle soluzioni, Visual Studio usa due tipi di file, uno con estensione *sln* e uno con estensione *suo*.

|Estensione|Name|Descrizione|
|---------------|----------|-----------------|
|sln|Soluzione Visual Studio|Organizza progetti, elementi del progetto ed elementi della soluzione nella soluzione.|
|suo|Solution User Options|Archivia le impostazioni a livello di utente e le personalizzazioni, ad esempio i punti di interruzione.|

## <a name="create-new-projects"></a>Crea nuovi progetti

Il modo più semplice per creare un nuovo progetto è iniziare da un modello di progetto per un tipo particolare di applicazione o sito Web. Un modello di progetto è costituito da un set di base di file di codice, file di configurazione, risorse e impostazioni già generati. Questi modelli sono disponibili nella finestra di dialogo in cui si crea un nuovo progetto (**File** > **Nuovo** > **Progetto**). Per altre informazioni, vedere [Creare un nuovo progetto in Visual Studio](create-new-project.md) e [Creare soluzioni e progetti](../ide/creating-solutions-and-projects.md).

Se si personalizzano spesso i progetti in un certo modo, è possibile creare un modello di progetto personalizzato che è possibile utilizzare per creare nuovi progetti da. Per altre informazioni, vedere [Creare modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md).

Quando si crea un nuovo progetto, per impostazione predefinita viene salvato in *%USERPROFILE%\source\repos*. È possibile modificare questo percorso tramite l'impostazione **Percorso progetti** in **Strumenti** > **Opzioni** > **Progetti e soluzioni** > **Percorsi**. Per altre informazioni, vedere [Pagina Progetti e soluzioni, finestra di dialogo Opzioni](../ide/reference/projects-and-solutions-options-dialog-box.md).

## <a name="solution-explorer"></a>Esplora soluzioni

Dopo aver creato un nuovo progetto, è possibile usare **Esplora soluzioni** per visualizzare e gestire il progetto e la soluzione, nonché gli elementi associati. La figura seguente illustra **Esplora soluzioni** con una soluzione C# contenente due progetti:

![Esplora soluzioni](../ide/media/vs2015_solution_explorer.png)

Sono disponibili molti comandi di menu dal menu di scelta rapida per vari elementi in **Esplora soluzioni**. Questi comandi includono la compilazione di un progetto, la gestione dei pacchetti NuGet, l'aggiunta di un riferimento, la ridenominazione di un file e l'esecuzione di test, solo per citarne alcuni. La barra degli strumenti nella parte superiore di **Esplora soluzioni** include pulsanti per passare dalla visualizzazione della soluzione alla visualizzazione delle cartelle, visualizzare i file nascosti, comprimere tutti i nodi e altro ancora.

Per i progetti ASP.NET Core, è possibile personalizzare la modalità di annidamento dei file in **Esplora soluzioni**. Per altre informazioni, vedere [Personalizzare l'annidamento file in Esplora soluzioni](file-nesting-solution-explorer.md).

## <a name="see-also"></a>Vedere anche

- [IDE di Visual Studio](../get-started/visual-studio-ide.md)
- [Progetti e soluzioni (Visual Studio per Mac)](/visualstudio/mac/projects-and-solutions)
- [Aggiungere e rimuovere elementi del progetto (Visual Studio per Mac)](/visualstudio/mac/add-and-remove-project-items)
