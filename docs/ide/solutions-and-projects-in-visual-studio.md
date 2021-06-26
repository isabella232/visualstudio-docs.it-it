---
title: Che cosa sono Visual Studio soluzioni & progetti?
description: Informazioni su Visual Studio progetti e soluzioni, su come creare nuovi progetti da un modello e su come visualizzare & gestire i progetti in Esplora soluzioni.
ms.custom: SEO-VS-2020, contperf-fy21q2
ms.date: 12/31/2020
ms.topic: conceptual
f1_keywords:
- vs.openproject
- vs.addexistingitem
- vs.addexistingsolutionitem
- vs.environment.projects
- vs.environment.solutions
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0a186c63cf695184b74780eeb6ab16b85c8aef5e
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112924968"
---
# <a name="what-are-solutions-and-projects-in-visual-studio"></a>Che cosa sono le soluzioni e i progetti Visual Studio?

In questo articolo si apprenderà *che* cos'è un progetto e *una* soluzione in Visual Studio. Illustra anche brevemente la finestra Esplora soluzioni strumenti e come creare un nuovo progetto.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Progetti e soluzioni in Visual Studio per Mac](/visualstudio/mac/projects-and-solutions).

## <a name="projects"></a>Progetti

Quando si crea un'app o un sito Web in Visual Studio, si inizia con un *progetto*. In senso logico, un progetto contiene tutti i file compilati in un file eseguibile, una libreria o un sito Web. Tali file possono includere codice sorgente, icone, immagini, file di dati e così via. Un progetto contiene anche le impostazioni del compilatore e altri file di configurazione che potrebbero essere necessari per i vari servizi o componenti con cui il programma comunica.

### <a name="project-file"></a>File di progetto

Visual Studio usa [MSBuild per](../msbuild/msbuild.md) compilare ogni progetto in una soluzione e ogni progetto contiene un file di progetto MSBuild. L'estensione di file riflette il tipo di progetto, ad esempio un progetto C# (con estensione csproj), un progetto Visual Basic (con estensione vbproj) o un progetto di database (con estensione dbproj). Il file di progetto è un documento XML che contiene tutte le informazioni e le istruzioni necessarie a MSBuild per compilare il progetto, inclusi il contenuto, i requisiti della piattaforma, le informazioni sul controllo delle versioni, le impostazioni del server Web o del server di database e le attività da eseguire.

I file di progetto sono basati sullo [schema XML di MSBuild.](../msbuild/msbuild-project-file-schema-reference.md) Per esaminare il contenuto dei file di progetto di tipo [sdk](../msbuild/how-to-use-project-sdk.md) più recente in Visual Studio, fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e **scegliere Modifica. \<projectname\>** Per esaminare il contenuto di .NET Framework e di altri progetti di tale stile, scaricare prima di tutto il progetto (fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e selezionare Scarica **progetto**). Fare quindi clic con il pulsante destro del mouse sul progetto e scegliere **Modifica. \<projectname\>**

> [!NOTE]
> Non è necessario usare soluzioni o progetti in Visual Studio modificare, compilare ed eseguire il debug del codice. È sufficiente aprire la cartella che contiene i file di origine in Visual Studio e iniziare ad apportare le modifiche. Per altre informazioni, vedere [Sviluppare codice in Visual Studio senza progetti o soluzioni](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

### <a name="create-new-projects"></a>Crea nuovi progetti

Il modo più semplice per creare un nuovo progetto è usare un modello di progetto per il tipo di progetto desiderato. Un modello di progetto include un set di base di file di codice, file di configurazione, asset e impostazioni pre-generati. Usare **File**  >  **New**  >  **Project (Nuovo progetto)** per selezionare un modello di progetto. Per altre informazioni, vedere [Creare un nuovo progetto.](create-new-project.md)

È anche possibile creare un modello di progetto personalizzato da usare per creare nuovi progetti. Per altre informazioni, vedere [Creare modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md).

Quando si crea un nuovo progetto, Visual Studio lo salva nel percorso *predefinito% USERPROFILE%\source\repos*. Per modificare questo percorso, passare **a** Strumenti  >  **Opzioni Progetti**  >  **e percorsi**  >  **soluzioni**. Per altre informazioni, vedere [Finestra di dialogo Opzioni: Progetti e soluzioni > percorsi](./reference/projects-solutions-locations-options.md).

## <a name="solutions"></a>Soluzioni

Un progetto è contenuto all'interno di una *soluzione*. Nonostante il nome, una soluzione non è una "risposta". È semplicemente un contenitore che include uno o più progetti correlati, insieme a informazioni di compilazione, impostazioni della finestra di Visual Studio e a vari file non associati a un progetto particolare.

### <a name="solution-file"></a>File di soluzione

Per archiviare le impostazioni delle soluzioni, Visual Studio usa due tipi di file, uno con estensione *sln* e uno con estensione *suo*.

|Estensione|Nome|Descrizione|
|---------------|----------|-----------------|
|sln|Soluzione Visual Studio|Organizza progetti, elementi del progetto ed elementi della soluzione nella soluzione.|
|suo|Solution User Options|Archivia le impostazioni a livello di utente e le personalizzazioni, ad esempio i punti di interruzione.|

> [!IMPORTANT]
> Una soluzione è descritta da un file di testo (con estensione *sln*) con un formato univoco specifico, per il quale non è prevista la modifica manuale. Al contrario, il file *suo* è un file nascosto che non viene visualizzato nelle impostazioni predefinite Esplora file predefinite. Per visualizzare i file nascosti, nel menu **Visualizza** di Esplora file selezionare la casella di controllo **Elementi nascosti**.

### <a name="solution-folder"></a>Cartella della soluzione

Una "cartella della soluzione" è una cartella virtuale che si trova solo in **Esplora soluzioni**, in cui è possibile usarla per raggruppare i progetti in una soluzione. Se si vuole individuare un file di soluzione in un computer, passare a Strumenti  >  **Opzioni**  >  **Progetti e percorsi**  >  **soluzioni**. Per altre informazioni, vedere [Finestra di dialogo Opzioni: Progetti e soluzioni > percorsi](./reference/projects-solutions-locations-options.md).

> [!TIP]
> Per un esempio di un progetto e di una soluzione creati da zero, completi di istruzioni dettagliate e codice di esempio, vedere Introduzione a [progetti e soluzioni.](../get-started/tutorial-projects-solutions.md)

## <a name="solution-explorer"></a>Esplora soluzioni

Dopo aver creato un nuovo progetto, è possibile usare **Esplora soluzioni** per visualizzare e gestire il progetto e la soluzione, nonché gli elementi associati. La figura seguente illustra **Esplora soluzioni** con una soluzione C# contenente due progetti:

::: moniker range="vs-2017"

![Screenshot della Esplora soluzioni con due progetti.](../ide/media/vs2015_solution_explorer.png)

La barra degli strumenti nella parte superiore di **Esplora soluzioni** include pulsanti per passare dalla visualizzazione della soluzione alla visualizzazione delle cartelle, visualizzare i file nascosti, comprimere tutti i nodi e altro ancora.

::: moniker-end

::: moniker range=">=vs-2019"

![Screenshot della Esplora soluzioni con due progetti Visual Studio.](../ide/media/solution-explorer.png)

La barra degli strumenti nella parte superiore di **Esplora soluzioni** include pulsanti per passare da una visualizzazione della soluzione [](managing-project-and-solution-properties.md) a una visualizzazione cartella, filtrare le modifiche in sospeso, visualizzare tutti i file, comprimere tutti i nodi, visualizzare le pagine delle proprietà, visualizzare il codice in anteprima [nell'editor](writing-code-in-the-code-and-text-editor.md)di codice e altro ancora.

::: moniker-end

Molti comandi di menu sono disponibili dal menu di scelta rapida visualizzato con il pulsante destro del mouse su varie voci **Esplora soluzioni**. Questi comandi includono la compilazione di un progetto, la gestione dei pacchetti NuGet, l'aggiunta di un riferimento, la ridenominazione di un file e l'esecuzione di test, solo per citarne alcuni.

Per i progetti ASP.NET Core, è possibile personalizzare la modalità di annidamento dei file in **Esplora soluzioni**. Per altre informazioni, vedere [Personalizzare l'annidamento file in Esplora soluzioni](file-nesting-solution-explorer.md).

> [!TIP]
> Se è stato chiuso Esplora soluzioni e si vuole aprirlo di nuovo, scegliere Visualizza Esplora soluzioni dalla barra dei menu o  >   premere **CTRL** + **ALT** + **L**. Se sono state chiuse le schede laterali e si vuole ripristinarne le posizioni predefinite, scegliere Window  >  **Reset Window Layout (Reimposta** layout finestra) dalla barra dei menu.

> [!NOTE]
> Per visualizzare le immagini e le icone dell'applicazione visualizzate in Visual Studio, scaricare la [**raccolta Visual Studio immagini.**](https://www.microsoft.com/download/details.aspx?id=35825)

## <a name="see-also"></a>Vedere anche

- [Introduzione a progetti e soluzioni](../get-started/tutorial-projects-solutions.md)
- [Gestire le proprietà di progetti e soluzioni](managing-project-and-solution-properties.md)
- [Soluzioni filtrate in Visual Studio](filtered-solutions.md)
- [Portabilità, migrazione e aggiornamento dei progetti](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Risorse per la risoluzione dei Visual Studio ide](./reference/resources-for-troubleshooting-integrated-development-environment-errors.md)
- [Progetti e soluzioni (Visual Studio per Mac)](/visualstudio/mac/projects-and-solutions)
