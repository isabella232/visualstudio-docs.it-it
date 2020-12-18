---
title: Informazioni su soluzioni e progetti
description: Informazioni sui progetti e le soluzioni di Visual Studio, su come creare nuovi progetti da un modello e su come visualizzare & gestire i progetti in Esplora soluzioni.
ms.custom: SEO-VS-2020, contperf-fy21q2
ms.date: 12/17/2020
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51a2f9683dd2285cc71dfff67020687f0c48afa4
ms.sourcegitcommit: c558d8a0f02ed2c932c8d6f70756d8d2cedb10b3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/18/2020
ms.locfileid: "97683918"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Soluzioni e progetti in Visual Studio

Questa pagina descrive il concetto di *progetto* e una *soluzione* in Visual Studio. Vengono inoltre illustrati brevemente la finestra degli strumenti Esplora soluzioni e la modalità di creazione di un nuovo progetto.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Progetti e soluzioni in Visual Studio per Mac](/visualstudio/mac/projects-and-solutions).

## <a name="projects"></a>Progetti

Quando si crea un'app o un sito Web in Visual Studio, si inizia con un *progetto*. In senso logico, un progetto contiene tutti i file compilati in un file eseguibile, in una libreria o in un sito Web. Tali file possono includere codice sorgente, icone, immagini, file di dati e così via. Un progetto contiene anche le impostazioni del compilatore e altri file di configurazione che potrebbero essere necessari per i vari servizi o componenti con cui il programma comunica.

### <a name="project-file"></a>File di progetto

Visual Studio USA [MSBuild](../msbuild/msbuild.md) per compilare ogni progetto in una soluzione e ogni progetto contiene un file di progetto MSBuild. L'estensione di file riflette il tipo di progetto, ad esempio un progetto C# (con estensione csproj), un progetto di Visual Basic (vbproj) o un progetto di database (. dbproj). Il file di progetto è un documento XML contenente tutte le informazioni e le istruzioni necessarie a MSBuild per compilare il progetto, inclusi il contenuto, i requisiti della piattaforma, le informazioni sul controllo delle versioni, le impostazioni del server Web o del server di database e le attività da eseguire.

I file di progetto sono basati sulla [XML schema MSBuild](../msbuild/msbuild-project-file-schema-reference.md). Per esaminare il contenuto dei [file di progetto in stile SDK](../msbuild/how-to-use-project-sdk.md) più recenti in Visual Studio, fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **modifica \<projectname\>**. Per esaminare il contenuto di .NET Framework e di altri progetti dello stile, scaricare prima il progetto (fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e selezionare **Scarica progetto**). Quindi, fare clic con il pulsante destro del mouse sul progetto e scegliere **modifica \<projectname\>**.

> [!NOTE]
> Non è necessario usare soluzioni o progetti in Visual Studio per modificare, compilare ed eseguire il debug del codice. È sufficiente aprire la cartella che contiene i file di origine in Visual Studio e iniziare ad apportare le modifiche. Per altre informazioni, vedere [Sviluppare codice in Visual Studio senza progetti o soluzioni](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions"></a>Soluzioni

Un progetto è contenuto all'interno di una *soluzione*. Nonostante il nome, una soluzione non è una "risposta". È semplicemente un contenitore che include uno o più progetti correlati, insieme a informazioni di compilazione, impostazioni della finestra di Visual Studio e a vari file non associati a un progetto particolare.

### <a name="solution-file"></a>File di soluzione

Per archiviare le impostazioni delle soluzioni, Visual Studio usa due tipi di file, uno con estensione *sln* e uno con estensione *suo*.

|Estensione|Nome|Descrizione|
|---------------|----------|-----------------|
|sln|Soluzione Visual Studio|Organizza progetti, elementi del progetto ed elementi della soluzione nella soluzione.|
|suo|Solution User Options|Archivia le impostazioni a livello di utente e le personalizzazioni, ad esempio i punti di interruzione.|

> [!IMPORTANT]
> Una soluzione è descritta da un file di testo (con estensione *sln*) con un formato univoco specifico, per il quale non è prevista la modifica manuale. Viceversa, il file con estensione *suo* è un file nascosto che non viene visualizzato nelle impostazioni predefinite di Esplora file. Per visualizzare i file nascosti, nel menu **Visualizza** di Esplora file selezionare la casella di controllo **Elementi nascosti**.

### <a name="solution-folder"></a>Cartella soluzione

Una "cartella della soluzione" è una cartella virtuale che è solo in **Esplora soluzioni**, in cui è possibile usarla per raggruppare i progetti in una soluzione. Se si desidera individuare un file di soluzione in un computer, passare a **strumenti**  >  **Opzioni**  >  **progetti e soluzioni**  >  **percorsi**. Per altre informazioni, vedere finestra di [dialogo Opzioni: progetti e soluzioni > percorsi](./reference/projects-solutions-locations-options.md).

## <a name="create-new-projects"></a>Crea nuovi progetti

Il modo più semplice per creare un nuovo progetto consiste nell'usare un modello di progetto per il tipo di progetto desiderato. Un modello di progetto include un set di base di file di codice, file di configurazione, asset e impostazioni generati in precedenza. Usare **file**  >  **nuovo**  >  **progetto** per selezionare un modello di progetto. Per ulteriori informazioni, vedere la pagina relativa alla [creazione di un nuovo progetto](create-new-project.md).

È inoltre possibile creare un modello di progetto personalizzato che è possibile utilizzare per creare nuovi progetti da. Per altre informazioni, vedere [Creare modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md).

Quando si crea un nuovo progetto, Visual Studio lo salva nel percorso predefinito, *%USERPROFILE%\source\repos*. Per modificare questo percorso, passare a **strumenti**  >  **Opzioni**  >  **progetti e soluzioni**  >  **percorsi**. Per altre informazioni, vedere finestra di [dialogo Opzioni: progetti e soluzioni > percorsi](./reference/projects-solutions-locations-options.md).

> [!TIP]
> Per un esempio di progetto e di soluzione creato da zero, completate con istruzioni dettagliate e codice di esempio, vedere [Introduzione a progetti e soluzioni](../get-started/tutorial-projects-solutions.md).

## <a name="solution-explorer"></a>Esplora soluzioni

Dopo aver creato un nuovo progetto, è possibile usare **Esplora soluzioni** per visualizzare e gestire il progetto e la soluzione, nonché gli elementi associati. La figura seguente illustra **Esplora soluzioni** con una soluzione C# contenente due progetti:

![Screenshot del Esplora soluzioni.](../ide/media/vs2015_solution_explorer.png)

Sono disponibili molti comandi di menu dal menu di scelta rapida per vari elementi in **Esplora soluzioni**. Questi comandi includono la compilazione di un progetto, la gestione dei pacchetti NuGet, l'aggiunta di un riferimento, la ridenominazione di un file e l'esecuzione di test, solo per citarne alcuni. La barra degli strumenti nella parte superiore di **Esplora soluzioni** include pulsanti per passare dalla visualizzazione della soluzione alla visualizzazione delle cartelle, visualizzare i file nascosti, comprimere tutti i nodi e altro ancora.

> [!TIP]
> Se è stato chiuso Esplora soluzioni e si desidera aprirlo nuovamente, scegliere **finestra**  >  **Reimposta layout finestra** dalla barra dei menu.

Per i progetti ASP.NET Core, è possibile personalizzare la modalità di annidamento dei file in **Esplora soluzioni**. Per altre informazioni, vedere [Personalizzare l'annidamento file in Esplora soluzioni](file-nesting-solution-explorer.md).

Per visualizzare un elenco di alcune delle icone visualizzate in Esplora soluzioni, vedere [Visualizzazione classi e Visualizzatore oggetti icone](class-view-and-object-browser-icons.md).

## <a name="see-also"></a>Vedere anche

- [IDE di Visual Studio](../get-started/visual-studio-ide.md)
- [Portabilità, migrazione e aggiornamento dei progetti](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Progetti e soluzioni (Visual Studio per Mac)](/visualstudio/mac/projects-and-solutions)
