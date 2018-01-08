---
title: 'Procedura dettagliata: Creazione di base di applicazione Shell isolata | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, walkthroughs
- Shell [Visual Studio], walkthroughs
- walkthroughs [Visual Studio], isolated shell-based application
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: "54"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e798eb66601d253c180a72b730bb3531e21c11c2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-basic-isolated-shell-application"></a>Procedura dettagliata: Creazione di un'applicazione Shell isolata di base
Questa procedura dettagliata viene illustrato come creare una soluzione shell isolata, personalizzare la finestra dello strumento informazioni e creare un programma di installazione che consente di installare la shell isolata.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../visual-studio-sdk.md). Per distribuire la shell isolata, è necessario utilizzare anche il pacchetto ridistribuibile di Visual Studio Shell (Isolated).  
  
## <a name="creating-an-isolated-shell-solution"></a>Creazione di una soluzione di Isolated Shell  
 In questa sezione viene illustrato come utilizzare il modello di progetto Visual Studio Shell isolata per creare una soluzione shell isolata. La soluzione contiene progetti seguenti:  
  
-   Il *SolutionName*. Progetto AboutBoxPackage, che consente di personalizzare l'aspetto della Guida/informazioni su casella.  
  
-   Il progetto ShellExtensionsVSIX che contiene il file vsixmanifest che definisce i diversi componenti dell'applicazione shell isolata.  
  
-   Il *SolutionName* progetto, che genera il file eseguibile che richiama l'applicazione shell isolata. Questo progetto contiene la cartella Shell Customization, che consente di personalizzare l'aspetto e il comportamento dell'applicazione shell isolata.  
  
-   Il *SolutionName* progetto dell'interfaccia utente, che genera un assembly satellite che definisce i comandi di menu attiva e stringhe localizzabili.  
  
#### <a name="to-create-a-basic-isolated-shell-solution"></a>Per creare una soluzione di base shell isolata  
  
1.  Aprire Visual Studio e creare un nuovo progetto.  
  
2.  Nel **nuovo progetto** finestra, espandere **altri tipi di progetto** e quindi **estendibilità**. Selezionare il **Visual Studio Shell Isolated** modello di progetto.  
  
3.  Denominare il progetto `MyVSShellStub` e specificare un percorso. Assicurarsi che **Crea directory per soluzione** è selezionata e quindi fare clic su **OK**.  
  
     Verrà visualizzata la nuova soluzione **Esplora**.  
  
4.  Compilare la soluzione e avviare il debug dell'applicazione shell isolata.  
  
     Visual Studio shell isolata viene visualizzata. Legge la barra del titolo **MyVSShellStub**. L'icona della barra del titolo viene generato da \MyVSShellStub\Resource Files\ApplicationIcon.ico.  
  
## <a name="customizing-the-application-name-and-icon"></a>Personalizzazione di un'icona e il nome dell'applicazione  
 Si consiglia di personalizzare l'applicazione utilizzando il nome dell'azienda e del logo nella barra del titolo. I passaggi seguenti mostrano come cambiare il nome e l'icona che vengono visualizzati nella barra del titolo dell'applicazione personalizzata modificando il file di definizione del pacchetto, MyVSShellStub.Application.pkgdef.  
  
#### <a name="to-customize-the-application-name-and-icon"></a>Per personalizzare il nome dell'applicazione e l'icona  
  
1.  Nel progetto MyVSShellStub aprire \Shell Customization\MyVSShellStub.Application.pkgdef.  
  
2.  Modifica il `AppName` valore dell'elemento a **"AppName" = "Fabrikam musica Editor"**  
  
3.  Per modificare l'icona dell'applicazione, copiare la directory \MyVSShellStub\MyVSShellStub\MyVSShellStub\ un'icona diversa. Rinominare il file ApplicationIcon.ico esistente ApplicationIcon1.ico. Rinominare il nuovo file ApplicationIcon.ico.  
  
4.  Compilare la soluzione e avviare il debug. Shell isolata IDE viene visualizzato. La barra del titolo è la nuova icona accanto alle parole **Fabrikam musica Editor**.  
  
## <a name="customizing-the-default-web-browser-home-page"></a>Personalizzazione della pagina Home del Browser Web predefinito  
 In questa sezione viene illustrato come modificare la home page predefinita del **Web Browser** finestra modificando il file di definizione del pacchetto.  
  
#### <a name="to-customize-the-default-web-browser-home-page"></a>Per personalizzare la home page del Browser Web predefinito  
  
1.  Nel file MyVSShellStub.Application.pkgdef, modificare il `DefaultHomePage` valore dell'elemento a "http://www.microsoft.com".  
  
2.  Ricompilare il progetto MyVSShellStub.  
  
3.  Compilare la soluzione e avviare il debug.  
  
4.  In **Vista > altre finestre**, fare clic su **Browser Web**. Il **Web Browser** finestra consente di visualizzare la home page di Microsoft Corporation.  
  
## <a name="removing-the-print-command"></a>Rimuovere il comando di stampa  
 Il file vsct in un progetto di interfaccia utente della shell isolata è costituito da un insieme di dichiarazioni del modulo di `<Define name=No_` *elemento*`>`, dove *elemento* è uno dei comandi e menu standard di Visual Studio.  
  
 Se una dichiarazione di blocco, il menu o un comando è escluso dalla shell isolata. Viceversa, se è impostata come commento una dichiarazione, il menu o un comando è incluso nella shell di tipo isolata.  
  
 Nei passaggi seguenti, si rimuove il commento comando stampato del file con estensione vsct.  
  
#### <a name="to-remove-the-print-command"></a>Per rimuovere il comando di stampa  
  
1.  Verificare che il **stampa** comando viene visualizzata sul **File** menu nell'applicazione shell isolata.  
  
2.  Nel progetto MyVSShellStubUI aprire \Resource Files\MyVSShellStubUI.vsct per la modifica.  
  
3.  Rimuovere questa riga:  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4.  Consente di rimuovere il comando di stampa.  
  
5.  Avviare il debug dell'applicazione shell isolata. Verificare che il **File > Stampa** comando non viene più visualizzato.  
  
## <a name="removing-features-from-the-isolated-shell"></a>Rimozione di funzionalità da Shell isolata  
 È possibile rimuovere alcuni dei pacchetti che vengono caricati con Visual Studio, modificando il file .pkgundef se non si desidera tali funzionalità nell'applicazione shell isolata personalizzato. Specificare il pacchetto in una delle sottochiavi della chiave del Registro di sistema \Packages $RootKey$.  
  
> [!NOTE]
>  Per trovare le funzionalità di GUID di Visual Studio, vedere [pacchetto GUID di funzionalità di Visual Studio](package-guids-of-visual-studio-features.md).  
  
 La procedura seguente viene illustrato come rimuovere il codice XML editor dalla shell isolata.  
  
#### <a name="to-remove-the-xml-editor"></a>Per rimuovere l'editor XML  
  
1.  Aprire il file MyVSShellStub.pkgundef nella cartella Shell Customization del progetto MyVSShellStub.  
  
2.  Rimuovere il commento la riga seguente:  
  
     [$RootKey$ \Packages\\{87569308-4813-40a0-9cd0-d7a30838ca3f}]  
  
3.  Ricompilare la soluzione e avviare il debug di shell isolata. Aprire un file XML, ad esempio, \MyVSShellStub\MyVSShellStub\MyVSShellStubUI\MyVSShellStubUI.vsct. Verificare che le parole chiave XML nel file sono colorate non e tale digitare "<" in una riga non viene visualizzata la descrizione comandi XML.  
  
## <a name="customizing-the-helpabout-box"></a>La Guida di personalizzazione/finestra informazioni su  
 È possibile personalizzare la Guida/sulla casella che viene creato come parte del modello di progetto shell isolata.  
  
#### <a name="to-customize-the-company-name"></a>Per personalizzare il nome della società  
  
1.  Il nome della società, le informazioni sul copyright, versione del prodotto e descrizione del prodotto si trovano nel progetto MyVSShellStub.AboutBoxPackage, nel file \Properties\AssemblyInfo.cs. Aprire il file.  
  
2.  Modifica il `AssemblyCompany` valore **Fabrikam**, `AssemblyProduct` e `AssemblyTitle` valori **Fabrikam musica Editor**e `AssemblyCopyright` valore **2015 Copyright © Fabrikam**:  
  
    ```  
    [assembly: AssemblyTitle("Fabrikam Music Editor")]  
    [assembly: AssemblyDescription("")]  
    [assembly: AssemblyConfiguration("")]  
    [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")] [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor ")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")]  
    ```  
  
3.  Per aggiungere una descrizione del prodotto, è possibile modificare il `AssemblyDescription` valore **la descrizione dell'editor di Fabrikam musica.**:  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.")]  
    ```  
  
4.  Avviare il debug e nell'applicazione shell isolata, aprire il **Guida > su** casella. Si noterà che le stringhe modificate. Il titolo degli argomenti della Guida/informazioni su casella è lo stesso come il `AssemblyTitle` valore nel file AssemblyInfo.cs.  
  
5.  Le proprietà del **Guida/informazioni su** casella stessa si trovano nel file MyVSShellStub.AboutBoxPackage\AboutBox.xaml. Per modificare la larghezza della Guida/informazioni su casella, passare al `AboutDialogStyle` blocco e impostare il `Width` proprietà 200:  
  
    ```  
    <Style x:Key="AboutDialogStyle" TargetType="Window">  
        <Setter Property="Height" Value="Auto" />  
        <Setter Property="Width" Value="200" />  
        <Setter Property="ShowInTaskbar" Value="False" />  
        <Setter Property="ResizeMode" Value="NoResize" />  
        <Setter Property="WindowStyle" Value="SingleBorderWindow" />  
        <Setter Property="SizeToContent" Value="Height" />  
    </Style>  
    ```  
  
6.  Ricompilare la soluzione e avviare il debug di shell isolata. La Guida sulla casella deve essere circa quadrato.  
  
## <a name="before-you-deploy-the-isolated-shell-application"></a>Prima di distribuire l'applicazione Shell isolata  
 L'applicazione shell isolata può essere installato in qualsiasi computer dotato di Visual Studio Shell (Isolated) Redistributable Package. Per ulteriori informazioni sul pacchetto ridistribuibile, vedere il [download di Visual Studio Extensibility](http://go.microsoft.com/fwlink/?LinkID=119298) sito Web.  
  
## <a name="deploying-the-isolated-shell-application"></a>Distribuzione dell'applicazione Shell isolata  
 Distribuire l'applicazione shell isolata in un computer di destinazione mediante la creazione di un progetto di installazione. È necessario specificare quanto segue:  
  
-   Il layout delle cartelle e file nel computer di destinazione.  
  
-   Le condizioni di avvio che garantiscono che .NET Framework e Visual Studio shell runtime vengono installate nel computer di destinazione.  
  
 Nella procedura seguente è necessario installare InstallShield Limited Edition nel computer.  
  
#### <a name="to-create-the-setup-project"></a>Per creare il progetto di installazione  
  
1.  In **Esplora**, fare doppio clic sul nodo della soluzione e quindi fare clic su **Aggiungi nuovo progetto**.  
  
2.  Nel **nuovo progetto** finestra di dialogo espandere **altri tipi di progetto** e quindi selezionare **installazione e distribuzione**. Selezionare il modello di InstallShield. Denominare il nuovo progetto `MySetup` e quindi fare clic su **OK**.  
  
3.  Se è già installato InstallShield Limited Edition, continuare al passaggio successivo.  
  
     Se InstallShield Limited Edition non è già installato, verrà visualizzata la pagina di download di InstallShield. Seguire le istruzioni per scaricare e installare il prodotto, scegliere la versione di InstallShield compatibile con la versione di Visual Studio. È necessario decidere se registrare l'installazione di InstallShield o utilizzarlo come versione di valutazione. Dopo aver completato l'installazione, è necessario riavviare Visual Studio.  
  
    > [!IMPORTANT]
    >  Prima di creare un progetto InstallShield, è necessario avviare Visual Studio come amministratore. Se non si esegue in modo, si verificherà un errore quando si compila il progetto.  
  
 I passaggi successivi viene illustrato come configurare il progetto di installazione.  
  
> [!IMPORTANT]
>  Assicurarsi di aver compilato la configurazione di rilascio del progetto shell isolata almeno una volta prima di configurare il progetto di installazione.  
  
#### <a name="to-configure-the-setup-project"></a>Per configurare il progetto di installazione  
  
1.  Nel **Esplora**, sotto il **MySetup** del progetto, scegliere **Project Assistant**. Nella riga inferiore del **Project Assistant** finestra, scegliere **informazioni sull'applicazione**. Immettere **Fabrikam** come nome della società e **Fabrikam musica Editor** come il nome dell'applicazione. Scegliere la freccia avanti nella parte inferiore destra del **Project Assistant**.  
  
2.  Selezionare **Sì** in **requisiti dell'applicazione software da installare nel computer?** e quindi selezionare **pacchetto completo di Microsoft .NET Framework 4.5**.  
  
3.  Scegliere il **file dell'applicazione** pulsante nella parte inferiore della finestra e verificare che il **Fabrikam musica Editor** viene selezionata la cartella.  
  
4.  Scegliere il **Aggiungi file** pulsante. Nel **Aggiungi file** finestra di dialogo, aggiungere i file seguenti dal **MyVSShellStub\Release** cartella:  
  
    1.  MyVSShellStub.exe.config  
  
    2.  DebuggerProxy.dll  
  
    3.  Debuggerproxy.dll  
  
    4.  MyVSShellStub.pkgdef  
  
    5.  MyVSShellStub.pkgundef  
  
    6.  MyVSShellStub.winprf  
  
    7.  Splash.bmp  
  
5.  Fare clic su di **Aggiungi output progetto** pulsante e aggiungere **MyVSShellStub/primario Output**. Fare clic su **OK**.  
  
6.  Nel riquadro a sinistra, sotto **Computer di destinazione**, fare doppio clic su di **Fabrikam musica Editor [INSTALLDIR]** nodo e aggiungere un **nuova cartella** denominato **estensioni**.  
  
7.  Fare doppio clic su di **estensioni** nodo nel riquadro a sinistra e aggiungere una nuova cartella denominata **applicazione**.  
  
8.  Selezionare il **applicazione** cartella, scegliere il **Aggiungi output progetto** pulsante, quindi selezionare l'output primario dal progetto MyVSShellStub.AboutBoxPackage.  
  
9. Fare clic su di **Aggiungi file** pulsante e dalla cartella \MyVSShellStub\Release\Extensions\Application\ aggiungere i file seguenti:  
  
    -   MyVSShellStub.AboutBoxPackage.pkgdef  
  
    -   MyVSShellStub.Application.pkgdef  
  
10. Fare doppio clic su di **Fabrikam musica Editor [INSTALLDIR]** nodo nel riquadro a sinistra e aggiungere una nuova cartella denominata **1033**.  
  
11. Selezionare la cartella 1033 e quindi fare clic su di **Aggiungi output progetto** e selezionare l'output primario dal progetto MyVSShellStubUI.  
  
12. Spostare il **collegamenti ad applicazioni** finestra.  
  
13. Fare clic su **New** per creare un collegamento e selezionare **\Fabrikam\Fabrikam Music Editor\MyVSShellStub.Primary Output [ProgramFilesFolder]**.  
  
14. Spostare il **domanda per l'installazione** riquadro.  
  
15. Impostare tutti gli elementi **n**.  
  
16. In **Esplora**, nel progetto MySetup, aprire **definiscono i requisiti di installazione e le azioni \ requisiti**. Il **requisiti** verrà visualizzata la finestra.  
  
17. Fare clic destro **requisiti Software di sistema** e selezionare **Crea nuova condizione di avvio**. Il **System ricerca guidata** viene visualizzato.  
  
18. Nel **ciò che si desidera trovare?** riquadro scegliere **voce del Registro di sistema** nell'elenco a discesa e fare clic su **Avanti**.  
  
19. Nel **come si desidera cercare l'elemento?** riquadro, selezionare **HKEY_LOCAL_MACHINE** come radice del Registro di sistema. Immettere **SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** per sistemi a 64 bit o **SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** per sistemi a 32 bit e immettere **installare** come valore del Registro di sistema. Scegliere **Avanti**.  
  
20. Nel **ciò che si desidera eseguire con il valore?** riquadro immettere **questo prodotto richiede il 2015 isolato Shell ridistribuibile di Visual Studio sia installato.** come il testo visualizzato e fare clic su **fine**.  
  
21. Ricompilare la soluzione shell isolata per creare il progetto di installazione.  
  
     È possibile trovare il file setup.exe nella cartella seguente:  
  
     \MyVSShellStub\MySetup\MySetup\Express\SingleImage\DiskImages\DISK1  
  
## <a name="testing-the-installation-program"></a>Il programma di installazione di test  
 Per testare il programma di installazione, copiare il file setup.exe in un computer diverso ed eseguire l'eseguibile del programma di installazione. È necessario essere in grado di eseguire l'applicazione shell isolata.