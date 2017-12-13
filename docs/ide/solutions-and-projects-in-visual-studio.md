---
title: Soluzioni e progetti in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 10/5/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
- solution items, folder in Solution Explorer
- solution items, shared
- solutions [Visual Studio]
- project items [Visual Studio], about project items
- solutions [Visual Studio], designing
- projects [Visual Studio]
- solutions [Visual Studio], projects and
- projects [Visual Studio], setting up
ms.assetid: aeaf56cb-c2dd-47f6-b012-23b84b7a7254
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ca3094b3bfe35381236798164fa18e58304bae3f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="solutions-and-projects-in-visual-studio"></a>Soluzioni e progetti in Visual Studio
Quando si crea un’app, un sito Web, un plug-in e così via in Visual Studio, si comincia con un *progetto*. In senso logico, un progetto contiene di tutti i file di codice sorgente, le icone, le immagini, i file di dati e qualsiasi altro elemento che verrà compilato in un programma eseguibile o in un sito Web in caso contrario, o necessario per eseguire la compilazione. Un progetto contiene anche tutte le impostazioni del compilatore e altri file di configurazione che potrebbero essere necessari per i vari servizi o componenti con cui il programma comunicherà.  

> [!NOTE]
>  Non è necessario usare progetti e soluzioni. È possibile semplicemente aprire i file in Visual Studio e iniziare a modificare il codice. Per altre informazioni, vedere [Sviluppare codice in Visual Studio senza progetti o soluzioni](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).  

Un file di progetto (con estensione vbproj, csproj, vcxproj) è un file XML che definisce una gerarchia di cartelle virtuali insieme ai percorsi di tutti gli elementi del progetto. Contiene anche le impostazioni di compilazione. Per visualizzare il contenuto di un file di progetto, è possibile selezionare il nome del progetto in Esplora soluzioni e quindi scegliere **Scarica progetto** dal menu di scelta rapida. Aprire di nuovo il menu di scelta rapida e scegliere **Modifica \<nomeprogetto\>**.  

In Visual Studio, il file di progetto viene utilizzato da Esplora soluzioni per visualizzare il contenuto e le impostazioni del progetto. Quando si compila il progetto, il motore MSBuild utilizza il file di progetto per creare il file eseguibile. È anche possibile personalizzare i progetti per produrre altri tipi di output.  

Un progetto è contenuto, in senso logico e all’interno di un file system, in una *soluzione* che può contenere uno o più progetti correlati, insieme alle informazioni di compilazione, alle impostazioni di finestra di Visual Studio ed eventuali file vari che non sono associati ad alcun progetto particolare. Una soluzione è un file di testo (con estensione sln) con un formato univoco specifico. In genere, non è destinato a essere modificato manualmente.  

Una soluzione ha un file con estensione *suo* associato che archivia le impostazioni, le preferenze e le informazioni di configurazione per ogni utente che ha lavorato al progetto.  

 Nel diagramma seguente viene illustrata la relazione tra progetti e soluzioni e gli elementi in essi contenuti dal punto di vista logico.  

 ![Progetti e soluzioni di Visual Studio](../ide/media/vside-project-diagram.png)  

## <a name="creating-new-projects"></a>Creazione di nuovi progetti  
 Il modo più semplice per creare un nuovo progetto consiste nell'iniziare con un modello di progetto costituito da un set di file di codice generati in precedenza, file di configurazione, risorse e impostazioni che consentono di iniziare la creazione di un particolare tipo di applicazione o sito Web in un determinato linguaggio di programmazione. Questi modelli sono quelli visualizzati nella finestra di dialogo **Nuovo progetto** o **Nuovo sito Web** quando si sceglie **File**, **Nuovo**, **Progetto** o **File**, **Nuovo**, **Sito Web**. Per altre informazioni, vedere [Creazione di soluzioni e progetti](../ide/creating-solutions-and-projects.md).  

È inoltre possibile creare modelli di progetto e modelli di elemento personalizzati. Per altre informazioni, vedere [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md).  

## <a name="managing-projects-in-solution-explorer"></a>Gestione di progetti in Esplora soluzioni  
 Dopo aver creato un nuovo progetto, viene utilizzato **Esplora soluzioni** per visualizzare e gestire progetti e soluzioni e i relativi articoli associati. La figura seguente illustra Esplora soluzioni con una soluzione C# contenente due progetti.  

 ![Esplora soluzioni](../ide/media/vs2015_solution_explorer.png "vs2015_solution_explorer")  

## <a name="in-this-section"></a>Contenuto della sezione  

-   [Creazione di soluzioni e progetti](../ide/creating-solutions-and-projects.md)  

-   [Aggiunta e rimozione di elementi di progetto](../ide/adding-and-removing-project-items.md)  

-   [Gestione delle proprietà di progetti e soluzioni](../ide/managing-project-and-solution-properties.md)  

-   [Gestione dei riferimenti in un progetto](../ide/managing-references-in-a-project.md)  

-   [Proprietà dell'applicazione](../ide/application-properties.md)  

-   [Gestione delle firme di assembly e manifesti](../ide/managing-assembly-and-manifest-signing.md)  

-   [Procedura: Specificare l'icona di un'applicazione (Visual Basic, C#)](../ide/how-to-specify-an-application-icon-visual-basic-csharp.md)  

-   [Sviluppo per una versione specifica di .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)  

-   [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)  

## <a name="see-also"></a>Vedere anche  
 [IDE di Visual Studio](../ide/visual-studio-ide.md)
