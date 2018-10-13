---
title: 'Procedura dettagliata: Creazione di una semplice applicazione Shell isolata | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, walkthroughs
- Shell [Visual Studio], walkthroughs
- walkthroughs [Visual Studio], isolated shell-based application
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 55
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f7158dcbd55229998e49e2d2891ae46d88c7fbc9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49199537"
---
# <a name="walkthrough-creating-a-basic-isolated-shell-application"></a>Procedura dettagliata: Creazione di un'applicazione Shell isolata di base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa procedura dettagliata illustra come creare una soluzione di shell isolata, personalizzare la finestra degli strumenti informazioni su e creare un programma di installazione che viene installata la shell isolata.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Per la distribuzione della shell isolata, è necessario utilizzare anche il pacchetto ridistribuibile di Visual Studio Shell (Isolated).  
  
## <a name="creating-an-isolated-shell-solution"></a>Creazione di una soluzione di Shell isolata  
 Questa sezione illustra come usare il modello di progetto di Visual Studio Shell isolata per creare una soluzione di shell isolata. La soluzione contiene progetti seguenti:  
  
-   Il *SolutionName*. Progetto AboutBoxPackage, che consente di personalizzare l'aspetto delle informazioni della Guida/finestra informazioni su.  
  
-   Il progetto ShellExtensionsVSIX, che contiene il file vsixmanifest che definisce i diversi componenti dell'applicazione shell isolata.  
  
-   Il *SolutionName* progetto, che produce il file eseguibile che richiama l'applicazione shell isolata. Questo progetto contiene la cartella delle personalizzazioni di Shell, che consente di personalizzare l'aspetto e comportamento dell'applicazione shell isolata.  
  
-   Il *SolutionName* progetto dell'interfaccia utente, che produce un assembly satellite che definisce i comandi di menu active e stringhe localizzabili.  
  
#### <a name="to-create-a-basic-isolated-shell-solution"></a>Per creare una soluzione di shell isolata di base  
  
1.  Aprire Visual Studio e creare un nuovo progetto.  
  
2.  Nel **nuovo progetto** finestra, espandere **altri tipi di progetto** e quindi **estendibilità**. Selezionare il **Visual Studio Shell isolata** modello di progetto.  
  
3.  Denominare il progetto `MyVSShellStub` e specificare un percorso. Verificare che l'opzione **Crea directory per soluzione** sia selezionata e quindi fare clic su **OK**.  
  
     La nuova soluzione viene visualizzato nella **Esplora soluzioni**.  
  
4.  Compilare la soluzione e avviare il debug dell'applicazione shell isolata.  
  
     Verrà visualizzata la shell isolata di Visual Studio. La barra del titolo legge **MyVSShellStub**. L'icona della barra del titolo viene generata da \MyVSShellStub\Resource Files\ApplicationIcon.ico.  
  
## <a name="customizing-the-application-name-and-icon"></a>Personalizzazione di un'icona e il nome dell'applicazione  
 È possibile personalizzare l'applicazione utilizzando il nome della società e il logo nella barra del titolo. La procedura seguente illustra come modificare il nome e l'icona che vengono visualizzati nella barra del titolo personalizzato dell'applicazione modificando il file di definizione del pacchetto, MyVSShellStub.Application.pkgdef.  
  
#### <a name="to-customize-the-application-name-and-icon"></a>Per personalizzare il nome dell'applicazione e l'icona  
  
1.  Nel progetto MyVSShellStub, aprire \Shell Customization\MyVSShellStub.Application.pkgdef.  
  
2.  Modifica il `AppName` valore dell'elemento a **"AppName" = "Editor di musica Fabrikam"**  
  
3.  Per modificare l'icona dell'applicazione, copiare un'icona diversa nella directory \MyVSShellStub\MyVSShellStub\MyVSShellStub\. Rinominare il file ApplicationIcon.ico esistente in ApplicationIcon1.ico. Rinominare il nuovo file in ApplicationIcon.ico.  
  
4.  Compilare la soluzione e avviare il debug. Verrà visualizzato l'IDE della shell isolata. La barra del titolo è la nuova icona accanto alle parole **Fabrikam musica Editor**.  
  
## <a name="customizing-the-default-web-browser-home-page"></a>Personalizzazione della pagina Home del Browser Web predefinito  
 In questa sezione illustra come modificare la home page predefinita del **Web Browser** finestra modificando il file di definizione del pacchetto.  
  
#### <a name="to-customize-the-default-web-browser-home-page"></a>Per personalizzare la home page del Browser Web predefinito  
  
1.  Nel file MyVSShellStub.Application.pkgdef, modificare il `DefaultHomePage` valore dell'elemento per "http://www.microsoft.com".  
  
2.  Ricompilare il progetto MyVSShellStub.  
  
3.  Compilare la soluzione e avviare il debug.  
  
4.  Nelle **Vista / Windows altri**, fare clic su **Browser Web**. Il **Web Browser** finestra consente di visualizzare la home page di Microsoft Corporation.  
  
## <a name="removing-the-print-command"></a>Rimozione del comando Print  
 Il file con estensione vsct in un progetto di interfaccia utente della shell isolata è costituito da un set di dichiarazioni del form `<Define name=No_` *elemento*`>`, dove *elemento* è uno dei menu di Visual Studio standard e comandi.  
  
 Se una dichiarazione verrà rimossi, tale menu o un comando è escluso dalla shell isolata. Viceversa, se viene impostata come commento una dichiarazione, il comando o il menu di scelta è incluso nella shell isolata.  
  
 Nei passaggi seguenti, si rimuove il commento comando di stampa nel file con estensione vsct.  
  
#### <a name="to-remove-the-print-command"></a>Per rimuovere il comando di stampa  
  
1.  Verificare che il **Print** comando compare nel **File** menu nell'applicazione shell isolata.  
  
2.  Nel progetto MyVSShellStubUI, aprire \Resource Files\MyVSShellStubUI.vsct per la modifica.  
  
3.  Rimuovere il commento di questa riga:  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4.  Questa operazione rimuove il comando di stampa.  
  
5.  Avviare il debug dell'applicazione shell isolata. Verificare che il **File / stampa** comando non è più presente.  
  
## <a name="removing-features-from-the-isolated-shell"></a>Rimozione delle funzionalità dalla Shell isolata  
 È possibile rimuovere alcuni dei pacchetti che vengono caricati con Visual Studio modificando il file con estensione pkgundef se non si desidera queste funzionalità nell'applicazione shell isolata personalizzato. Specificare il pacchetto in una delle sottochiavi della chiave del Registro di sistema \Packages $ $RootKey.  
  
> [!NOTE]
>  Per trovare le funzionalità di GUID di Visual Studio, vedere [pacchetto i GUID di funzionalità di Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
 La procedura seguente illustra come rimuovere il codice XML come editor da shell isolata.  
  
#### <a name="to-remove-the-xml-editor"></a>Per rimuovere l'editor XML  
  
1.  Aprire il file MyVSShellStub.pkgundef nella cartella del progetto MyVSShellStub personalizzazione della Shell.  
  
2.  Rimuovere il commento la riga seguente:  
  
     [$RootKey$ \Packages\\{87569308-4813-40a0-9cd0-d7a30838ca3f}]  
  
3.  Ricompilare la soluzione e avviare il debug della shell isolata. Aprire un file XML, ad esempio, \MyVSShellStub\MyVSShellStub\MyVSShellStubUI\MyVSShellStubUI.vsct. Verificare che le parole chiave XML nel file non sono colorate e tale digitando "<" su una riga non visualizzare le descrizioni comandi XML.  
  
## <a name="customizing-the-helpabout-box"></a>La Guida di personalizzazione/finestra informazioni su  
 È possibile personalizzare la Guida/sulla finestra di cui viene creato come parte del modello di progetto shell isolata.  
  
#### <a name="to-customize-the-company-name"></a>Per personalizzare il nome della società  
  
1.  Il nome della società, le informazioni sul copyright, versione del prodotto e descrizione del prodotto si trovano nel progetto MyVSShellStub.AboutBoxPackage, nel file \Properties\AssemblyInfo.cs. Aprire il file.  
  
2.  Modifica il `AssemblyCompany` valore per **Fabrikam**, il `AssemblyProduct` e `AssemblyTitle` valori **Fabrikam musica Editor**e il `AssemblyCopyright` valore **Copyright © Fabrikam 2015**:  
  
    ```  
    [assembly: AssemblyTitle("Fabrikam Music Editor")]  
    [assembly: AssemblyDescription("")]  
    [assembly: AssemblyConfiguration("")]  
    [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")] [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor ")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015”)]  
    ```  
  
3.  Per aggiungere una descrizione del prodotto, modificare il `AssemblyDescription` valore per **la descrizione dell'editor di file musicali Fabrikam.**:  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.”)]  
    ```  
  
4.  Avviare il debug e nell'applicazione shell isolata, aprire il **utili informazioni su** casella. Si noterà che le stringhe modificate. Il titolo degli argomenti della Guida/finestra informazioni su è lo stesso come il `AssemblyTitle` valore nel file AssemblyInfo.cs.  
  
5.  Le proprietà del **informazioni su** finestra stessa si trovano nel file MyVSShellStub.AboutBoxPackage\AboutBox.xaml. Per modificare la larghezza delle informazioni della Guida/finestra informazioni su, passare al `AboutDialogStyle` bloccare e impostare il `Width` proprietà a 200:  
  
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
  
6.  Ricompilare la soluzione e avviare il debug della shell isolata. La Guida in linea o della finestra informazioni su deve essere circa quadrati.  
  
## <a name="before-you-deploy-the-isolated-shell-application"></a>Prima di distribuire l'applicazione Shell isolata  
 L'applicazione shell isolata può essere installato in qualsiasi computer dotato di Visual Studio Shell (Isolated) Redistributable Package. Per altre informazioni sul pacchetto ridistribuibile, vedere la [download di Visual Studio Extensibility](http://go.microsoft.com/fwlink/?LinkID=119298) sito Web.  
  
## <a name="deploying-the-isolated-shell-application"></a>Distribuzione dell'applicazione Shell isolata  
 Si distribuisce l'applicazione shell isolata in un computer di destinazione mediante la creazione di un progetto di installazione. È necessario specificare quanto segue:  
  
-   Il layout delle cartelle e file nel computer di destinazione.  
  
-   Le condizioni di avvio che garantiscono che il Framework .NET e Visual Studio shell runtime vengono installate nel computer di destinazione.  
  
 Nella procedura seguente è necessario per l'installazione di InstallShield Limited Edition nel computer.  
  
#### <a name="to-create-the-setup-project"></a>Per creare il progetto di installazione  
  
1.  Nelle **Esplora soluzioni**, fare doppio clic sul nodo della soluzione e quindi fare clic su **Aggiungi nuovo progetto**.  
  
2.  Nel **nuovo progetto** finestra di dialogo espandere **altri tipi di progetto** e quindi selezionare **installazione e distribuzione**. Selezionare il modello di InstallShield. Denominare il nuovo progetto `MySetup` e quindi fare clic su **OK**.  
  
3.  Se è già installato InstallShield Limited Edition, continuare al passaggio successivo.  
  
     Se InstallShield Limited Edition non è già installato, verrà visualizzata la pagina di download di InstallShield. Seguire le istruzioni per scaricare e installare il prodotto, scegliendo la versione di InstallShield compatibile con la versione di Visual Studio. È necessario decidere se si desidera registrare l'installazione di InstallShield o usarlo come versione di valutazione. È necessario riavviare Visual Studio dopo aver completato l'installazione.  
  
    > [!IMPORTANT]
    >  Prima di creare un progetto InstallShield, è necessario avviare Visual Studio come amministratore. Se non si esegue questa operazione, si otterrà un errore quando si compila il progetto.  
  
 I passaggi successivi illustrano come configurare il progetto di installazione.  
  
> [!IMPORTANT]
>  Assicurarsi di avere compilato la configurazione di rilascio del progetto shell isolata di almeno una volta prima di configurare il progetto di installazione.  
  
#### <a name="to-configure-the-setup-project"></a>Per configurare il progetto di installazione  
  
1.  Nel **Esplora soluzioni**, sotto il **MySetup** del progetto, scegliere **Project Assistant**. Nella riga inferiore del **Project Assistant** finestra, scegliere **le informazioni sull'applicazione**. Immettere **Fabrikam** come nome della società e **Fabrikam musica Editor** come il nome dell'applicazione. Scegliere la freccia avanti nella parte inferiore destra della **Project Assistant**.  
  
2.  Selezionare **Yes** sotto **richiede l'applicazione software da installare nella macchina?** e quindi selezionare **pacchetto completo di Microsoft .NET Framework 4.5**.  
  
3.  Scegliere il **i file dell'applicazione** pulsante nella parte inferiore della finestra e assicurarsi che le **Fabrikam musica Editor** viene selezionata la cartella.  
  
4.  Scegliere il **Add Files** pulsante. Nel **Add Files** finestra di dialogo, aggiungere i seguenti file dalle **MyVSShellStub\Release** cartella:  
  
    1.  MyVSShellStub.exe.config  
  
    2.  Debuggerproxy  
  
    3.  Debuggerproxy  
  
    4.  MyVSShellStub.pkgdef  
  
    5.  MyVSShellStub.pkgundef  
  
    6.  MyVSShellStub.winprf  
  
    7.  Splash.bmp  
  
5.  Scegliere il **Aggiungi output progetto** pulsante e aggiungere **Output MyVSShellStub/primario**. Fare clic su **OK**.  
  
6.  Nel riquadro sinistro, sotto **Computer di destinazione**, fare doppio clic il **Fabrikam musica Editor [INSTALLDIR]** nodo e aggiungere un **nuova cartella** denominato **estensioni** .  
  
7.  Fare doppio clic il **Extensions** nodo nel riquadro sinistro e aggiungere una nuova cartella denominata **applicazione**.  
  
8.  Selezionare il **Application** cartella, scegliere il **Aggiungi output progetto** pulsante e quindi selezionare l'output primario dal progetto MyVSShellStub.AboutBoxPackage.  
  
9. Scegliere il **Add Files** pulsante e aggiungere i file seguenti dalla cartella \MyVSShellStub\Release\Extensions\Application\:  
  
    -   MyVSShellStub.AboutBoxPackage.pkgdef  
  
    -   MyVSShellStub.Application.pkgdef  
  
10. Fare doppio clic il **Fabrikam musica Editor [INSTALLDIR]** nodo nel riquadro sinistro e aggiungere una nuova cartella denominata **1033**.  
  
11. Selezionare la cartella 1033, quindi scegliere il **Aggiungi output progetto** e selezionare l'output primario dal progetto MyVSShellStubUI.  
  
12. Spostare il **i collegamenti alle applicazioni** finestra.  
  
13. Fare clic su **New** per creare un collegamento e selezionare **\Fabrikam\Fabrikam Music Editor\MyVSShellStub.Primary Output [ProgramFilesFolder]**.  
  
14. Spostare il **domanda per l'installazione** riquadro.  
  
15. Impostare tutti gli elementi **No**.  
  
16. Nelle **Esplora soluzioni**, nel progetto MySetup, aprire **definiscono i requisiti di installazione e le azioni \ requisiti**. Il **requisiti** verrà visualizzata la finestra.  
  
17. Fare clic destro **requisiti Software di sistema** e selezionare **Crea nuova condizione di avvio**. Il **sistema ricerca guidata** viene visualizzata.  
  
18. Nel **ciò che si desidera trovare?** riquadro, scegliere **voce del Registro di sistema** nell'elenco a discesa e fare clic su **Next**.  
  
19. Nel **modo in cui si desidera cercare l'elemento?** riquadro, selezionare **HKEY_LOCAL_MACHINE** come radice del Registro di sistema. Immettere **SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** per i sistemi a 64 bit o **SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** per sistemi a 32 bit, quindi immettere  **Installare** come valore del Registro di sistema. Scegliere **Avanti**.  
  
20. Nel **ciò che si desidera eseguire con il valore?** riquadro, immettere **questo prodotto è necessario il 2015 isolato Shell ridistribuibile di Visual Studio da installare.** il testo visualizzato e fare clic su **fine**.  
  
21. Ricompilare la soluzione di shell isolata per creare il progetto di installazione.  
  
     È possibile trovare il file setup.exe nella cartella seguente:  
  
     \MyVSShellStub\MySetup\MySetup\Express\SingleImage\DiskImages\DISK1  
  
## <a name="testing-the-installation-program"></a>Test del programma di installazione  
 Per testare il programma di installazione, copiare il file setup.exe in un computer diverso ed eseguire l'eseguibile di programma di installazione. È necessario essere in grado di eseguire l'applicazione shell isolata.

