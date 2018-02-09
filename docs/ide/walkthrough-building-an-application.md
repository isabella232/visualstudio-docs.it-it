---
title: 'Procedura dettagliata: compilazione di un''applicazione | Microsoft Docs'
ms.custom: 
ms.date: 09/25/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4842955d-8959-4e4e-98b8-2358360179b3
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d24a8b0cfa54b56808e8d283534e03e607fca0c9
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="walkthrough-building-an-application"></a>Procedura dettagliata: compilazione di un'applicazione

Completando questa procedura dettagliata è possibile acquisire familiarità con numerose opzioni che possono essere configurate quando si compilano applicazioni con Visual Studio. Verrà illustrato come creare una configurazione della build personalizzata, nascondere alcuni messaggi di avviso e aumentare le informazioni di output di compilazione per un'applicazione di esempio.

## <a name="install-the-sample-application"></a>Installare l'applicazione di esempio

Scaricare l'esempio di [introduzione alla creazione di applicazioni WPF](https://code.msdn.microsoft.com/Introduction-to-Building-b8d16419). Scegliere C# o Visual Basic. Dopo aver scaricato il file con estensione zip, estrarlo e aprire il file **ExpenseItIntro.sln** usando Visual Studio.

## <a name="create-a-custom-build-configuration"></a>Creare una configurazione della build personalizzata

Quando si crea una soluzione, le configurazioni della build di versione e di debug e le relative destinazioni della piattaforma predefinite sono definite automaticamente per la soluzione. È quindi possibile personalizzare queste configurazioni o crearne di proprie. Le configurazioni della build specificano il tipo di compilazione. Le piattaforme di compilazione specificano il sistema operativo a cui è rivolta un'applicazione per la configurazione. Per altre informazioni, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md), [Informazioni sulle piattaforme di compilazione](../ide/understanding-build-platforms.md) e [Procedura: Impostare le configurazioni di debug e di versione](../debugger/how-to-set-debug-and-release-configurations.md).

È possibile modificare o creare configurazioni e impostazioni piattaforma usando la finestra di dialogo **Gestione configurazione**. In questa procedura si creerà una configurazione della build per il test.

### <a name="to-create-a-build-configuration"></a>Per creare una configurazione della build
  
1. Aprire la finestra di dialogo **Gestione configurazione**.
  
     ![Build menu, Configuration Manager command](../ide/media/buildwalk_configurationmanagerdialogbox.png "BuildWalk_ConfigurationManagerDialogBox")  
  
2. Nell'elenco **Configurazione soluzione attiva** scegliere **\<Nuova\>**.
  
3. Nella finestra di dialogo **Nuova configurazione soluzione** assegnare il nome `Test` alla nuova configurazione, copiare le impostazioni dalla configurazione per il debug esistente e quindi scegliere il pulsante **OK**.
  
     ![New Solution Configuration Dialog Box](../ide/media/buildwalk_newsolutionconfigdlgbox.png "BuildWalk_NewSolutionConfigDlgBox")  
  
4. Nell'elenco **Piattaforma soluzione attiva** scegliere **\<Nuova\>**.
  
5. Nella finestra di dialogo **Nuova piattaforma soluzione** scegliere **x64** e non copiare le impostazioni dalla piattaforma x86.
  
     ![New Solution Platform Dialog Box](../ide/media/buildwalk_newsolutionplatform.png "BuildWalk_NewSolutionPlatform")  
  
6. Scegliere il pulsante **OK**.
  
 La configurazione della soluzione attiva è stata modificata su Test con la piattaforma della soluzione attiva impostata su x64.
  
 ![Gestione configurazione con configurazione di test](../ide/media/buildwalk_configmanagertestconfig.png "BuildWalk_ConfigManagerTestconfig")  
  
7. Scegliere **Chiudi**.

È possibile verificare o modificare rapidamente la configurazione della soluzione attiva tramite l'elenco **Configurazioni soluzione** nella barra degli strumenti **Standard**.
  
![Opzione Configurazioni soluzione barra degli strumenti standard](../ide/media/buildwalk_standardtoolbarsolutioncongfig.png "BuildWalk_StandardToolbarSolutionCongfig")  
  
## <a name="build-the-application"></a>Compilare l'applicazione

Successivamente verrà creata la soluzione con la configurazione della build personalizzata.
  
### <a name="to-build-the-solution"></a>Per compilare la soluzione
  
-   Nella barra dei menu scegliere **Compilazione**, **Compila soluzione**.
  
    Nella finestra **Output** vengono visualizzati i risultati della compilazione. La compilazione è stata completata.
  
## <a name="hide-compiler-warnings"></a>Nascondere gli avvisi del compilatore

A questo punto viene presentata la parte del codice che determina un avviso generato dal compilatore.

1. Nel progetto C# aprire il file **ExpenseReportPage.xaml.cs**. Nel metodo **ExpenseReportPage** aggiungere il codice seguente: `int i;`.

    OR

    Nel progetto Visual Basic aprire il file **ExpenseReportPage.xaml.vb**. Nel costruttore personalizzato **Public Sub New...**  aggiungere il codice seguente: `Dim i`.

2. Compilare la soluzione.

Nella finestra **Output** vengono visualizzati i risultati della compilazione. La compilazione è stata completata, ma sono stati generati avvisi:  

 Figura 1: Avvisi di Visual Basic  
  
 ![Finestra Output di Visual Basic ](../ide/media/buildwalk_vbbuildoutputwnd.png "BuildWalk_VBBuildOutputWnd")  
  
 Figura 2: Avvisi di C#  
  
 ![Finestra Output di Visual C&#35;](../ide/media/buildwalk_csharpbuildoutputwnd.png "BuildWalk_CsharpBuildOutputWnd")  
  
È possibile nascondere temporaneamente determinati messaggi di avviso durante una compilazione anziché lasciare che ingombrino l'output di compilazione.

### <a name="to-hide-a-specific-c-warning"></a>Per nascondere un avviso specifico di C#
  
1. Scegliere il nodo di progetto di primo livello in **Esplora soluzioni**.
  
2. Sulla barra dei menu scegliere **Visualizza**, **Pagine delle proprietà**.
  
     The **Project Designer** opens.
  
3. Scegliere la pagina **Compilazione** e specificare il numero di avviso **0168** nella casella **Non visualizzare avvisi**.
  
     ![Build page, Project Designer](../ide/media/buildwalk_csharpsupresswarnings.png "BuildWalk_CsharpSupressWarnings")  
  
     For more information, see [Build Page, Project Designer (C#)](../ide/reference/build-page-project-designer-csharp.md).
  
4. Compilare la soluzione.
  
     The **Output** window displays only summary information for the build.
  
     ![Output Window, Visual C&#35; Build Warnings](../ide/media/buildwalk_visualcsharpbuildwarnings.png "BuildWalk_VisualCsharpBuildWarnings")  
  
### <a name="to-suppress-all-visual-basic-build-warnings"></a>Per eliminare tutti gli avvisi durante la compilazione di Visual Basic
  
1. Scegliere il nodo di progetto di primo livello in **Esplora soluzioni**.
  
2. Sulla barra dei menu scegliere **Visualizza**, **Pagine delle proprietà**.
  
     The **Project Designer** opens.
  
3. Nella pagina **Compilazione** selezionare la casella di controllo **Disabilita tutti gli avvisi**.
  
     ![Compile page, Project Designer](../ide/media/buildwalk_vbsupresswarnings.png "BuildWalk_VBSupressWarnings")  
  
     For more information, see [Configuring Warnings in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).
  
4. Compilare la soluzione.
  
 Nella finestra **Output** vengono visualizzate solo le informazioni di riepilogo per la compilazione.
  
 ![Finestra Output, avvisi durante la compilazione di Visual Basic ](../ide/media/buildwalk_visualbasicbuildwarnings.png "BuildWalk_VisualBasicBuildWarnings")  
  
 Per altre informazioni, vedere [Procedura: Non visualizzare avvisi del compilatore](../ide/how-to-suppress-compiler-warnings.md).
  
## <a name="display-additional-build-details-in-the-output-window"></a>Visualizzare dettagli di compilazione aggiuntivi nella finestra di output

È possibile modificare la quantità di informazioni sul processo di compilazione visualizzate nella finestra **Output**. Il livello di dettaglio di compilazione è in genere impostato su minimo, cioè nella finestra **Output** viene visualizzato solo un riepilogo del processo di compilazione insieme a eventuali errori o avvisi di priorità alta. È possibile visualizzare altre informazioni sulla compilazione tramite la [finestra di dialogo Opzioni, Progetti e soluzioni, Compila ed esegui](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md).
  
> [!IMPORTANT]
>  Se si visualizzano maggiori informazioni, il completamento della compilazione richiederà più tempo.
  
### <a name="to-change-the-amount-of-information-in-the-output-window"></a>Per modificare la quantità di informazioni nella finestra Output
  
1. Aprire la finestra di dialogo **Opzioni**.
  
     ![Options command on the Tools menu](../ide/media/exploreide-toolsoptionsmenu.png "ExploreIDE-ToolsOptionsmenu")  
  
2. Scegliere la categoria **Progetti e soluzioni** e quindi scegliere la pagina **Compila ed esegui**.
  
3. Nell'elenco **Livello di dettaglio output in compilazione progetto MSBuild** scegliere **Normale** e quindi **OK**.
  
4. Nella barra dei menu scegliere **Compilazione**, **Pulisci soluzione**.
  
5. Compilare la soluzione e quindi esaminare le informazioni nella finestra **Output**.
  
     The build information includes the time that the build started (located at the beginning) and the order in which files were processed. This information also includes the actual compiler syntax that Visual Studio runs during the build.
  
     For example, in the C# build, the [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) option lists the warning code, 1762, that you specified earlier in this topic, along with three other warnings.
  
     In the Visual Basic build, [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) doesn't include specific warnings to exclude, so no warnings appear.
  
    > [!TIP]
    >  You can search the contents of the **Output** window if you display the **Find** dialog box by choosing the Ctrl+F keys.
  
Per altre informazioni, vedere [Procedura: Visualizzare, salvare e configurare file di log di compilazione](../ide/how-to-view-save-and-configure-build-log-files.md).
  
## <a name="create-a-release-build"></a>Creare una build di versione

È possibile compilare una versione dell'applicazione di esempio ottimizzata per la spedizione. Per la build di versione, si specificherà che il file eseguibile venga copiato in una condivisione di rete prima dell'avvio della compilazione.

Per altre informazioni, vedere [Procedura: Modificare la directory dell'output compilato](../ide/how-to-change-the-build-output-directory.md) e [Compilazione e pulizia di progetti e soluzioni in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md).

### <a name="to-specify-a-release-build-for-visual-basic"></a>Per specificare una build di versione per Visual Basic
  
1. Aprire **Creazione progetti**.
  
     ![View menu, Property Pages command](../ide/media/buildwalk_viewpropertypages.png "BuildWalk_ViewPropertyPages")  
  
2. Scegliere la pagina **Compilazione**.
  
3. Nell'elenco **Configurazione** scegliere **Versione**.
  
4. Nell'elenco **Piattaforma** scegliere **x86**.
  
5. Specificare un percorso di compilazione nella casella **Percorso dell'output di compilazione**.
  
     For example, you can specify \\\myserver\builds.
  
    > [!IMPORTANT]
    >  A message box might appear, warning you that the network share that you've specified might not be a trusted location. If you trust the location that you've specified, choose the **OK** button in the message box.
  
6. Compilare l'applicazione.
  
     ![Build Solution command on the Build menu](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")  
  
### <a name="to-specify-a-release-build-for-c"></a>Per specificare una build di versione per Visual C# #
  
1. Aprire **Creazione progetti**.
  
     ![View menu, Property Pages command](../ide/media/buildwalk_viewpropertypages.png "BuildWalk_ViewPropertyPages")  
  
2. Scegliere la scheda **Compila**.
  
3. Nell'elenco **Configurazione** scegliere **Versione**.
  
4. Nell'elenco **Piattaforma** scegliere **x86**.
  
5. Specificare un percorso di rete nella casella **Percorso output**.
  
     For example, you could specify \\\myserver\builds.
  
    > [!IMPORTANT]
    >  A message box might appear, warning you that the network share that you've specified might not be a trusted location. If you trust the location that you've specified, choose the **OK** button in the message box.
  
6. Nella **barra degli strumenti Standard** impostare le opzioni Configurazioni soluzione su **Versione** e Piattaforme soluzione su **x86**.

7. Compilare l'applicazione.
  
     ![Build Solution command on the Build menu](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")  
  
 Il file eseguibile viene copiato nel percorso di rete specificato. Il percorso sarà \\\mioserver\compilazioni\\*Nomefile*.exe.
  
Congratulazioni: questa procedura dettagliata è stata completata correttamente.
  
## <a name="see-also"></a>Vedere anche

[Procedura dettagliata: compilazione di un progetto (C++)](/cpp/ide/walkthrough-building-a-project-cpp)  
[Panoramica della precompilazione del progetto di applicazione Web ASP.NET](http://msdn.microsoft.com/b940abbd-178d-4570-b441-52914fa7b887)  
[Procedura dettagliata: uso di MSBuild](../msbuild/walkthrough-using-msbuild.md)
