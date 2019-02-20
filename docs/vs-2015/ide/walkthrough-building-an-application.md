---
title: "Procedura dettagliata: Compilazione di un'applicazione | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 4842955d-8959-4e4e-98b8-2358360179b3
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7f4103502b3ebd6371f0b1c0ac27c6da7c8904c6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54799155"
---
# <a name="walkthrough-building-an-application"></a>Procedura dettagliata: compilazione di un'applicazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Completando questa procedura dettagliata è possibile acquisire familiarità con numerose opzioni che possono essere configurate quando si compilano applicazioni con Visual Studio. Tra le altre attività, verrà illustrato come creare una configurazione della build personalizzata, nascondere alcuni messaggi di avviso e aumentare le informazioni di output di compilazione per un'applicazione di esempio.  
  
 Di seguito sono elencate le diverse sezioni di questo argomento:  
  
 [Installare l'applicazione di esempio](../ide/walkthrough-building-an-application.md#BKMK_installapp)  
  
 [Creare una configurazione della build personalizzata](../ide/walkthrough-building-an-application.md#BKMK_CreateBuildConfig)  
  
 [Compilare l'applicazione](../ide/walkthrough-building-an-application.md#BKMK_building)  
  
 [Nascondere gli avvisi del compilatore](../ide/walkthrough-building-an-application.md#BKMK_hidewarning)  
  
 [Visualizzare dettagli di compilazione aggiuntivi nella finestra di output](../ide/walkthrough-building-an-application.md#BKMK_outputdetails)  
  
 [Creare una build di versione](../ide/walkthrough-building-an-application.md#BKMK_releasebuild)  
  
##  <a name="BKMK_installapp"></a> Installare l'applicazione di esempio  
 Usare la finestra di dialogo **Estensioni e aggiornamenti** per trovare e installare l'esempio [Introduzione alla creazione di applicazioni WPF](http://code.msdn.microsoft.com/Introduction-to-Building-b8d16419?SRC=VSIDE) nella raccolta esempi del sito Web Microsoft. La raccolta esempi offre un'ampia gamma di progetti e codice di esempio che è possibile scaricare ed esaminare durante la pianificazione e lo sviluppo delle applicazioni.  
  
#### <a name="to-install-the-sample-application"></a>Per installare l'applicazione di esempio  
  
1. Nella barra dei menu scegliere **Strumenti**, **Estensioni e aggiornamenti**.  
  
2. Scegliere la categoria **Online** e quindi la categoria **Raccolta esempi**.  
  
3. Specificare `Introduction` nella casella di ricerca per trovare l'esempio.  
  
    ![Finestra di dialogo Estensioni e aggiornamenti](../ide/media/buildwalk-extensionsdialogsampledownload.png "BuildWalk_ExtensionsDialogSampleDownload")  
  
4. Nell'elenco dei risultati scegliere **Introduzione alla creazione di applicazioni WPF (Visual c#)** o **Introduzione alla creazione di applicazioni WPF (Visual Basic)**.  
  
5. Scegliere il pulsante **Scarica** e quindi fare clic sul pulsante **Chiudi**.  
  
   L'esempio Introduzione alla creazione di applicazioni WPF viene visualizzato nella finestra di dialogo **Nuovo progetto**.  
  
#### <a name="to-create-a-solution-for-the-sample-application"></a>Per creare una soluzione per l'applicazione di esempio  
  
1.  Aprire la finestra di dialogo **Nuovo progetto**.  
  
     ![Nella barra dei menu scegliere File, Nuovo, Progetto](../ide/media/exploreide-filenewproject.png "ExploreIDE-FileNewProject")  
  
2.  Nella categoria **Installati** scegliere la categoria **Esempi** per visualizzare l'esempio Introduzione alla creazione di applicazioni WPF.  
  
3.  Denominare la soluzione `IntroWPFcsharp` per Visual C#.  
  
     ![Finestra di dialogo Nuovo progetto, esempi installati](../ide/media/buildwalk-newprojectdlgintrotowpfsample.png "BuildWalk_NewProjectdlgIntrotoWPFsample")  
  
     OR  
  
     Denominare la soluzione `IntroWPFvb` per Visual Basic.  
  
     ![Finestra di dialogo Nuovo progetto, esempio di Visual Basic](../ide/media/buildwalk-newprojectdlgintrotowpfsamplevb.png "BuildWalk_NewProjectdlgIntrotoWPFsampleVB")  
  
4.  Fare clic sul pulsante **OK** .  
  
##  <a name="BKMK_CreateBuildConfig"></a> Creare una configurazione della build personalizzata  
 Quando si crea una soluzione, le configurazioni della build di versione e di debug e le relative destinazioni della piattaforma predefinite sono definite automaticamente per la soluzione. È quindi possibile personalizzare queste configurazioni o crearne di proprie. Le configurazioni della build specificano il tipo di compilazione. Le piattaforme di compilazione specificano il sistema operativo a cui è rivolta un'applicazione per la configurazione. Per altre informazioni, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md), [Informazioni sulle piattaforme di compilazione](../ide/understanding-build-platforms.md) ed [Eseguire il debug e il rilascio delle configurazioni del progetto](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).  
  
 È possibile modificare o creare configurazioni e impostazioni piattaforma usando la finestra di dialogo **Gestione configurazione**. In questa procedura si creerà una configurazione della build per il test.  
  
#### <a name="to-create-a-build-configuration"></a>Per creare una configurazione della build  
  
1. Aprire la finestra di dialogo **Gestione configurazione**.  
  
    ![Menu Compila, comando Gestione configurazione](../ide/media/buildwalk-configurationmanagerdialogbox.png "BuildWalk_ConfigurationManagerDialogBox")  
  
2. Nell'elenco **Configurazione soluzione attiva** scegliere **Nuova**.  
  
3. Nella finestra di dialogo **Nuova configurazione soluzione** assegnare un nome alla nuova configurazione `Test`, copiare le impostazioni dalla configurazione per il debug esistente e quindi scegliere il pulsante **OK**.  
  
    ![Finestra di dialogo Nuova configurazione soluzione](../ide/media/buildwalk-newsolutionconfigdlgbox.png "BuildWalk_NewSolutionConfigDlgBox")  
  
4. Nell'elenco **Piattaforma soluzione attiva** scegliere **Nuova**.  
  
5. Nella finestra di dialogo **Nuova piattaforma soluzione** scegliere **x64** e non copiare le impostazioni dalla piattaforma x86.  
  
    ![Finestra di dialogo Nuova piattaforma soluzione](../ide/media/buildwalk-newsolutionplatform.png "BuildWalk_NewSolutionPlatform")  
  
6. Fare clic sul pulsante **OK** .  
  
   La configurazione della soluzione attiva è stata modificata su Test con la piattaforma della soluzione attiva impostata su x64.  
  
   ![Gestione configurazione con configurazione di test](../ide/media/buildwalk-configmanagertestconfig.png "BuildWalk_ConfigManagerTestconfig")  
  
   È possibile verificare o modificare rapidamente la configurazione della soluzione attiva tramite l'elenco **Configurazioni soluzione** nella barra degli strumenti **Standard**.  
  
   ![Opzione Configurazioni soluzione barra degli strumenti standard](../ide/media/buildwalk-standardtoolbarsolutioncongfig.png "BuildWalk_StandardToolbarSolutionCongfig")  
  
##  <a name="BKMK_building"></a> Compilare l'applicazione  
 Successivamente verrà creata la soluzione con la configurazione della build personalizzata.  
  
#### <a name="to-build-the-solution"></a>Per compilare la soluzione  
  
- Nella barra dei menu scegliere **Compilazione**, **Compila soluzione**.  
  
  Nella finestra **Output** vengono visualizzati i risultati della compilazione. La compilazione ha avuto esito positivo, ma sono stati generati alcuni messaggi di avviso.  
  
  Figura 1: Avvisi di Visual Basic  
  
  ![Finestra Output di Visual Basic ](../ide/media/buildwalk-vbbuildoutputwnd.png "BuildWalk_VBBuildOutputWnd")  
  
  Figura 2: Visual C# avvisi  
  
  ![Finestra Output di Visual C&#35;](../ide/media/buildwalk-csharpbuildoutputwnd.png "BuildWalk_CsharpBuildOutputWnd")  
  
##  <a name="BKMK_hidewarning"></a> Nascondere gli avvisi del compilatore  
 È possibile nascondere temporaneamente determinati messaggi di avviso durante una compilazione anziché lasciare che ingombrino l'output di compilazione.  
  
#### <a name="to-hide-a-specific-visual-c-warning"></a>Per nascondere un avviso specifico di Visual C#  
  
1.  Scegliere il nodo di progetto di primo livello in **Esplora soluzioni**.  
  
2.  Sulla barra dei menu, scegliere **Visualizza**, **Pagine delle proprietà**.  
  
     Si apre la finestra **Creazione progetti**.  
  
3.  Scegliere la pagina **Compilazione** e specificare il numero dell'avviso nella casella **Non visualizzare avvisi**`1762`.  
  
     ![Pagina compilazione, creazione progetti](../ide/media/buildwalk-csharpsuppresswarnings.png "BuildWalk_CsharpSuppressWarnings")  
  
     Per altre informazioni, vedere [Pagina Compilazione, Creazione progetti (C#)](../ide/reference/build-page-project-designer-csharp.md).  
  
4.  Compilare la soluzione.  
  
     Nella finestra **Output** vengono visualizzate solo le informazioni di riepilogo per la compilazione.  
  
     ![Finestra Output, avvisi durante la compilazione di Visual C&#35;](../ide/media/buildwalk-visualcsharpbuildwarnings.png "BuildWalk_VisualCsharpBuildWarnings")  
  
#### <a name="to-suppress-all-visual-basic-build-warnings"></a>Per eliminare tutti gli avvisi durante la compilazione di Visual Basic  
  
1. Scegliere il nodo di progetto di primo livello in **Esplora soluzioni**.  
  
2. Sulla barra dei menu, scegliere **Visualizza**, **Pagine delle proprietà**.  
  
    Si apre la finestra **Creazione progetti**.  
  
3. Nella pagina **Compilazione** selezionare la casella di controllo **Disabilita tutti gli avvisi**.  
  
    ![Pagina compilazione, creazione progetti](../ide/media/buildwalk-vbsuppresswarnings.png "BuildWalk_VBSuppressWarnings")  
  
    Per altre informazioni, vedere [Configuring Warnings in Visual Basic](../ide/configuring-warnings-in-visual-basic.md) (Configurazione degli avvisi in Visual Basic).  
  
4. Compilare la soluzione.  
  
   Nella finestra **Output** vengono visualizzate solo le informazioni di riepilogo per la compilazione.  
  
   ![Finestra Output, avvisi durante la compilazione di Visual Basic ](../ide/media/buildwalk-visualbasicbuildwarnings.png "BuildWalk_VisualBasicBuildWarnings")  
  
   Per altre informazioni, vedere [Procedura: Non visualizzare avvisi del compilatore](../ide/how-to-suppress-compiler-warnings.md).  
  
##  <a name="BKMK_outputdetails"></a> Visualizzare dettagli di compilazione aggiuntivi nella finestra di output  
 È possibile modificare la quantità di informazioni sul processo di compilazione visualizzate nella finestra **Output**. Il livello di dettaglio di compilazione è in genere impostato su minimo, cioè nella finestra **Output** viene visualizzato solo un riepilogo del processo di compilazione insieme a eventuali errori o avvisi di priorità alta. È possibile visualizzare altre informazioni sulla compilazione tramite la [finestra di dialogo Opzioni, Progetti e soluzioni, Compila ed esegui](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md).  
  
> [!IMPORTANT]
>  Se si visualizzano maggiori informazioni, il completamento della compilazione richiederà più tempo.  
  
#### <a name="to-change-the-amount-of-information-in-the-output-window"></a>Per modificare la quantità di informazioni nella finestra Output  
  
1. Aprire la finestra di dialogo **Opzioni**.  
  
    ![Comando Opzioni nel menu Strumenti](../ide/media/exploreide-toolsoptionsmenu.png "ExploreIDE-ToolsOptionsmenu")  
  
2. Scegliere la categoria **Progetti e soluzioni** e quindi scegliere la pagina **Compila ed esegui**.  
  
3. Nell'elenco **Livello di dettaglio output in compilazione progetto MSBuild** scegliere **Normale** e quindi **OK**.  
  
4. Nella barra dei menu scegliere **Compilazione**, **Pulisci soluzione**.  
  
5. Compilare la soluzione e quindi esaminare le informazioni nella finestra **Output**.  
  
    Le informazioni sulla compilazione includono l'ora di inizio della compilazione (indicata all'inizio), l'ordine in cui i file sono stati elaborati e la quantità di tempo impiegato per completare il processo (indicata alla fine). Queste informazioni includono anche la sintassi del compilatore effettiva che Visual Studio esegue durante la compilazione.  
  
    Ad esempio, nella compilazione di Visual C#, l'opzione [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) elenca il codice di avviso, 1762, specificato in precedenza in questo argomento, insieme ad altri tre avvisi.  
  
    Nella compilazione di Visual Basic [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) non include avvisi specifici da escludere, pertanto non viene visualizzato alcun avviso.  
  
   > [!TIP]
   >  È possibile cercare il contenuto della finestra **Output** se si visualizza la finestra di dialogo **Trova** scegliendo i tasti CTRL+F.  
  
   Per altre informazioni, vedere [Procedura: Visualizzare, salvare e configurare file di log di compilazione](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
##  <a name="BKMK_releasebuild"></a> Creare una build di versione  
 È possibile compilare una versione dell'applicazione di esempio ottimizzata per la spedizione. Per la build di versione, si specificherà che il file eseguibile venga copiato in una condivisione di rete prima dell'avvio della compilazione.  
  
 Per altre informazioni, vedere [Procedura: Modificare la Directory di Output di compilazione](../ide/how-to-change-the-build-output-directory.md) e [compilazione e pulizia di progetti e soluzioni in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md).  
  
#### <a name="to-specify-a-release-build-for-visual-basic"></a>Per specificare una build di versione per Visual Basic  
  
1.  Aprire **Creazione progetti**.  
  
     ![Menu Visualizza, comando pagine delle proprietà](../ide/media/buildwalk-viewpropertypages.png "BuildWalk_ViewPropertyPages")  
  
2.  Scegliere la pagina **Compilazione**.  
  
3.  Nell'elenco **Configurazione** scegliere **Versione**.  
  
4.  Nell'elenco **Piattaforma** scegliere **x86**.  
  
5.  Specificare un percorso di compilazione nella casella **Percorso dell'output di compilazione**.  
  
     Ad esempio, è possibile specificare \\\mioserver\compilazioni.  
  
    > [!IMPORTANT]
    >  Potrebbe essere visualizzata una finestra di messaggio che informa che la condivisione di rete specificata potrebbe non essere una posizione attendibile. Se si considera attendibile il percorso specificato, scegliere il pulsante **OK** nella finestra di messaggio.  
  
6.  Compilare l'applicazione.  
  
     ![Comando Compila soluzione dal menu Compila](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")  
  
#### <a name="to-specify-a-release-build-for-visual-c"></a>Per specificare una build di rilascio per Visual C#  
  
1. Aprire **Creazione progetti**.  
  
    ![Menu Visualizza, comando pagine delle proprietà](../ide/media/buildwalk-viewpropertypages.png "BuildWalk_ViewPropertyPages")  
  
2. Scegliere la scheda **Compila**.  
  
3. Nell'elenco **Configurazione** scegliere **Versione**.  
  
4. Nell'elenco **Piattaforma** scegliere **x86**.  
  
5. Specificare un percorso di rete nella casella **Percorso output**.  
  
    Ad esempio, è possibile specificare \\\mioserver\compilazioni.  
  
   > [!IMPORTANT]
   >  Potrebbe essere visualizzata una finestra di messaggio che informa che la condivisione di rete specificata potrebbe non essere una posizione attendibile. Se si considera attendibile il percorso specificato, scegliere il pulsante **OK** nella finestra di messaggio.  
  
6. Compilare l'applicazione.  
  
    ![Comando Compila soluzione dal menu Compila](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")  
  
   Il file eseguibile viene copiato nel percorso di rete specificato. Il percorso sarà \\\mioserver\compilazioni\\*Nomefile*.exe.  
  
   Congratulazioni: questa procedura dettagliata è stata completata correttamente.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Compilazione di un progetto (C++)](http://msdn.microsoft.com/library/d459bc03-88ef-48d0-9f9a-82d17f0b6a4d)   
 [Cenni preliminari sulla precompilazione del progetto di applicazione Web ASP.NET](http://msdn.microsoft.com/b940abbd-178d-4570-b441-52914fa7b887)   
 [Procedura dettagliata: uso di MSBuild](../msbuild/walkthrough-using-msbuild.md)
