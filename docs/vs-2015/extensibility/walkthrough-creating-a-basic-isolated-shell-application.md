---
title: "Procedura dettagliata: creazione di un'applicazione shell isolata di base | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, walkthroughs
- Shell [Visual Studio], walkthroughs
- walkthroughs [Visual Studio], isolated shell-based application
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 55
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6192eb5583e7d0bc37518e995aacccad643cc9ec
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850342"
---
# <a name="walkthrough-creating-a-basic-isolated-shell-application"></a>Procedura dettagliata: creazione di un'applicazione shell isolata di base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa procedura dettagliata viene illustrato come creare una soluzione Shell isolata, personalizzare la finestra degli strumenti e creare un programma di installazione che consente di installare la shell isolata.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Per distribuire la shell isolata, è necessario utilizzare anche il pacchetto ridistribuibile di Visual Studio Shell (isolated).  
  
## <a name="creating-an-isolated-shell-solution"></a>Creazione di una soluzione Shell isolata  
 Questa sezione illustra come usare il modello di progetto Visual Studio Shell isolated per creare una soluzione Shell isolata. La soluzione contiene i progetti seguenti:  
  
- *SolutionName*. Progetto AboutBoxPackage, che consente di personalizzare l'aspetto della casella Guida/informazioni su.  
  
- Il progetto ShellExtensionsVSIX, che contiene il file source. Extension. vsixmanifest che definisce i diversi componenti dell'applicazione shell isolata.  
  
- Il progetto *SolutionName* , che produce il file eseguibile che richiama l'applicazione shell isolata. Questo progetto contiene la cartella di personalizzazione della shell, che consente di personalizzare l'aspetto e il comportamento dell'applicazione shell isolata.  
  
- Il progetto dell'interfaccia utente *SolutionName* , che produce un assembly satellite che definisce i comandi di menu attivi e le stringhe localizzabili.  
  
#### <a name="to-create-a-basic-isolated-shell-solution"></a>Per creare una soluzione Shell isolata di base  
  
1. Aprire Visual Studio e creare un nuovo progetto.  
  
2. Nella finestra **nuovo progetto** espandere **altri tipi di progetto** , quindi **estendibilità**. Selezionare il modello di progetto **Visual Studio Shell isolated** .  
  
3. Denominare il progetto `MyVSShellStub` e specificare un percorso. Verificare che l'opzione **Crea directory per soluzione** sia selezionata, quindi fare clic su **OK**.  
  
     La nuova soluzione verrà visualizzata in **Esplora soluzioni**.  
  
4. Compilare la soluzione e avviare il debug dell'applicazione shell isolata.  
  
     Viene visualizzata la shell isolata di Visual Studio. La barra del titolo legge **MyVSShellStub**. L'icona della barra del titolo viene generata da \MyVSShellStub\Resource Files\ApplicationIcon.ico.  
  
## <a name="customizing-the-application-name-and-icon"></a>Personalizzazione del nome e dell'icona dell'applicazione  
 Per personalizzare l'applicazione, è possibile usare il nome della società e il logo sulla barra del titolo. Nei passaggi seguenti viene illustrato come modificare il nome e l'icona visualizzati nella barra del titolo dell'applicazione personalizzata modificando il file di definizione del pacchetto, MyVSShellStub. Application. pkgdef.  
  
#### <a name="to-customize-the-application-name-and-icon"></a>Per personalizzare il nome e l'icona dell'applicazione  
  
1. Nel progetto MyVSShellStub aprire \Shell contiene Customization\MyVSShellStub.Application.pkgdef.  
  
2. Modificare il valore dell'elemento `AppName` in **"appname" = "Fabrikam Music Editor"**  
  
3. Per modificare l'icona dell'applicazione, copiare un'icona diversa nella directory \MyVSShellStub\MyVSShellStub\MyVSShellStub\ Rinominare il file ApplicationIcon. ico esistente in ApplicationIcon1. ico. Rinominare il nuovo file in ApplicationIcon. ico.  
  
4. Compilare la soluzione e avviare il debug. Viene visualizzato l'IDE della shell isolata. La barra del titolo ha la nuova icona accanto alla parola **editor di Fabrikam Music**.  
  
## <a name="customizing-the-default-web-browser-home-page"></a>Personalizzazione della Home page del Web browser predefinito  
 In questa sezione viene illustrato come modificare il home page predefinito della finestra del **browser Web** modificando il file di definizione del pacchetto.  
  
#### <a name="to-customize-the-default-web-browser-home-page"></a>Per personalizzare il Web browser predefinito home page  
  
1. Nel file MyVSShellStub. Application. pkgdef modificare il valore dell'elemento `DefaultHomePage` in "<https://www.microsoft.com>".  
  
2. Ricompilare il progetto MyVSShellStub.  
  
3. Compilare la soluzione e avviare il debug.  
  
4. In **Visualizza/altre finestre**fare clic su **Web browser**. Nella finestra del **Web browser** viene visualizzata la Home page Microsoft Corporation.  
  
## <a name="removing-the-print-command"></a>Rimozione del comando Print  
 Il file con estensione vsct in un progetto dell'interfaccia utente della shell isolata è costituito da un set di dichiarazioni nel formato `<Define name=No_`*elemento*`>`, dove *elemento* è uno dei menu e dei comandi standard di Visual Studio.  
  
 Se una dichiarazione viene annullata come commento, tale menu o comando viene escluso dalla shell isolata. Viceversa, se una dichiarazione è impostata come commento, il menu o il comando viene incluso nella shell isolata.  
  
 Nei passaggi seguenti è possibile rimuovere il commento dalla stampa del comando nel file con estensione vsct.  
  
#### <a name="to-remove-the-print-command"></a>Per rimuovere il comando stampa  
  
1. Verificare che il comando **stampa** sia visualizzato nel menu **file** dell'applicazione shell isolata.  
  
2. Nel progetto MyVSShellStubUI aprire \Resource Files\MyVSShellStubUI.vsct per la modifica.  
  
3. Rimuovere il commento da questa riga:  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4. Viene rimosso il comando stampa.  
  
5. Avviare il debug dell'applicazione shell isolata. Verificare che il comando **file/stampa** sia scomparso.  
  
## <a name="removing-features-from-the-isolated-shell"></a>Rimozione di funzionalità dalla shell isolata  
 È possibile rimuovere alcuni pacchetti caricati con Visual Studio modificando il file con estensione pkgundef se non si desidera che tali funzionalità siano presenti nell'applicazione shell isolata personalizzata. Il pacchetto viene specificato in una delle sottochiavi della chiave del registro di sistema $RootKey $ \Packages.  
  
> [!NOTE]
> Per trovare i GUID delle funzionalità di Visual Studio, vedere [GUID di pacchetti delle funzionalità di Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
 Nella procedura seguente viene illustrato come rimuovere l'editor XML dalla shell isolata.  
  
#### <a name="to-remove-the-xml-editor"></a>Per rimuovere l'editor XML  
  
1. Aprire il file MyVSShellStub. pkgundef nella cartella di personalizzazione della shell del progetto MyVSShellStub.  
  
2. Rimuovere il commento dalla riga seguente:  
  
     [$RootKey$\Packages\\{87569308-4813-40a0-9cd0-d7a30838ca3f}]  
  
3. Ricompilare la soluzione e avviare il debug della shell isolata. Aprire un file XML, ad esempio \MyVSShellStub\MyVSShellStub\MyVSShellStubUI\MyVSShellStubUI.vsct. Verificare che le parole chiave XML nel file non siano colorate e che digitando "<" in una riga non vengano visualizzate le descrizioni comandi XML.  
  
## <a name="customizing-the-helpabout-box"></a>Personalizzazione della casella Guida/informazioni  
 È possibile personalizzare la casella Guida/informazioni, creata come parte del modello di progetto della shell isolata.  
  
#### <a name="to-customize-the-company-name"></a>Per personalizzare il nome della società  
  
1. Il nome della società, le informazioni sul copyright, la versione del prodotto e la descrizione del prodotto si trovano nel progetto MyVSShellStub. AboutBoxPackage nel file \Properties\AssemblyInfo.cs. Aprire il file.  
  
2. Modificare il valore di `AssemblyCompany` in **Fabrikam**, i valori `AssemblyProduct` e `AssemblyTitle` in **Fabrikam Music Editor**e il valore di `AssemblyCopyright` su **Copyright © Fabrikam 2015**:  
  
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
  
3. Per aggiungere una descrizione del prodotto, modificare il valore di `AssemblyDescription` con **la descrizione di Fabrikam Music Editor.** :  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.”)]  
    ```  
  
4. Avviare il debug e nell'applicazione shell isolata aprire la casella **Guida/informazioni** . Verranno visualizzate le stringhe modificate. Il titolo della casella Guida/informazioni è uguale al valore di `AssemblyTitle` in AssemblyInfo.cs.  
  
5. Le proprietà della casella **Guida/informazioni** si trovano nel file MyVSShellStub. AboutBoxPackage\AboutBox.XAML. Per modificare la larghezza della casella Guida/informazioni, passare al blocco `AboutDialogStyle` e impostare la proprietà `Width` su 200:  
  
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
  
6. Ricompilare la soluzione e avviare il debug della shell isolata. La casella Guida/informazioni deve essere approssimativamente quadrata.  
  
## <a name="before-you-deploy-the-isolated-shell-application"></a>Prima di distribuire l'applicazione shell isolata  
 L'applicazione shell isolata può essere installata in qualsiasi computer in cui è presente il pacchetto ridistribuibile di Visual Studio Shell (isolated). Per ulteriori informazioni sul pacchetto ridistribuibile, vedere il sito Web relativo ai [download di estendibilità di Visual Studio](https://msdn.microsoft.com/vstudio/bb984878.aspx) .  
  
## <a name="deploying-the-isolated-shell-application"></a>Distribuzione dell'applicazione shell isolata  
 Per distribuire l'applicazione shell isolata in un computer di destinazione, è necessario creare un progetto di installazione. È necessario specificare gli elementi seguenti:  
  
- Il layout delle cartelle e dei file nel computer di destinazione.  
  
- Condizioni di avvio che garantiscono che il .NET Framework e il runtime della shell di Visual Studio siano installati nel computer di destinazione.  
  
  Nella procedura seguente sarà necessario installare InstallShield Limited Edition nel computer.  
  
#### <a name="to-create-the-setup-project"></a>Per creare il progetto di installazione  
  
1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo della soluzione, quindi scegliere **Aggiungi nuovo progetto**.  
  
2. Nella finestra di dialogo **nuovo progetto** espandere **altri tipi di progetto** , quindi selezionare **installazione e distribuzione**. Selezionare il modello InstallShield. Denominare il nuovo progetto `MySetup` e quindi fare clic su **OK**.  
  
3. Se InstallShield Limited Edition è già installato, continuare con il passaggio successivo.  
  
    Se InstallShield Limited Edition non è ancora installato, viene visualizzata la pagina di download di InstallShield. Seguire le istruzioni per scaricare e installare il prodotto, scegliendo la versione di InstallShield compatibile con la versione di Visual Studio. È necessario decidere se registrare l'installazione di InstallShield o usarla come valutazione. Dopo aver completato l'installazione, è necessario riavviare Visual Studio.  
  
   > [!IMPORTANT]
   > È necessario avviare Visual Studio come amministratore prima di creare un progetto InstallShield. In caso contrario, verrà generato un errore quando si compila il progetto.  
  
   Nei passaggi successivi viene illustrato come configurare il progetto di installazione.  
  
> [!IMPORTANT]
> Prima di configurare il progetto di installazione, verificare di aver compilato la configurazione di rilascio del progetto shell isolata almeno una volta.  
  
#### <a name="to-configure-the-setup-project"></a>Per configurare il progetto di installazione  
  
1. Nel **Esplora soluzioni**, nel progetto di **installazione** , scegliere **Assistente progetto**. Nella riga inferiore della finestra **Project Assistant** scegliere **informazioni sull'applicazione**. Immettere **Fabrikam** come nome della società e **Fabrikam Music Editor** come nome dell'applicazione. Scegliere la freccia in giù nella parte inferiore destra di **Project Assistant**.  
  
2. Selezionare **Sì** in **l'applicazione richiede che il software sia installato nel computer** e quindi selezionare **Microsoft .NET pacchetto completo di .NET Framework 4,5**.  
  
3. Scegliere il pulsante **file applicazione** nella parte inferiore della finestra e assicurarsi che la cartella **Fabrikam Music Editor** sia selezionata.  
  
4. Scegliere il pulsante **Aggiungi file** . Nella finestra di dialogo **Aggiungi file** aggiungere i file seguenti dalla cartella **MyVSShellStub\Release** :  
  
    1. MyVSShellStub.exe.config  
  
    2. DebuggerProxy.dll  
  
    3. DebuggerProxy.dll.manifest  
  
    4. MyVSShellStub.pkgdef  
  
    5. MyVSShellStub.pkgundef  
  
    6. MyVSShellStub.winprf  
  
    7. Splash. bmp  
  
5. Fare clic sul pulsante **Aggiungi output progetto** e aggiungere **MyVSShellStub/output primario**. Fare clic su **OK**.  
  
6. Nel riquadro sinistro, in **computer di destinazione**, fare clic con il pulsante destro del mouse sul nodo **Fabrikam Music Editor [INSTALLDIR]** e aggiungere una **nuova cartella** denominata **Extensions**.  
  
7. Fare clic con il pulsante destro del mouse sul nodo **estensioni** nel riquadro sinistro e aggiungere una nuova cartella denominata **Application**.  
  
8. Selezionare la cartella **dell'applicazione** e fare clic sul pulsante **Aggiungi output progetto** , quindi selezionare l'output primario dal progetto MyVSShellStub. AboutBoxPackage.  
  
9. Fare clic sul pulsante **Aggiungi file** e dalla cartella \MyVSShellStub\Release\Extensions\Application\ aggiungere i file seguenti:  
  
    - MyVSShellStub.AboutBoxPackage.pkgdef  
  
    - MyVSShellStub.Application.pkgdef  
  
10. Fare clic con il pulsante destro del mouse sul nodo di **Fabrikam Music Editor [INSTALLDIR]** nel riquadro sinistro e aggiungere una nuova cartella denominata **1033**.  
  
11. Selezionare la cartella 1033, quindi fare clic sul pulsante **Aggiungi output progetto** e selezionare l'output primario dal progetto MyVSShellStubUI.  
  
12. Passare alla finestra dei **collegamenti dell'applicazione** .  
  
13. Fare clic su **nuovo** per creare un collegamento e selezionare **[ProgramFilesFolder] \Fabrikam\Fabrikam musica Editor\MyVSShellStub.Primary output**.  
  
14. Passare al riquadro **intervista di installazione** .  
  
15. Impostare tutti gli elementi su **No**.  
  
16. In **Esplora soluzioni**, nel progetto di installazione, aprire define requirements **and actions \ requirements**. Verrà visualizzata la finestra **requisiti** .  
  
17. Fare clic con il pulsante destro del mouse su **requisiti software** e selezionare **Crea nuova condizione di avvio**. Viene visualizzata la **procedura guidata di ricerca del sistema** .  
  
18. Nel riquadro **che si desidera trovare?** scegliere **voce del registro di sistema** nell'elenco a discesa e fare clic su **Avanti**.  
  
19. Nel riquadro **come si desidera cercarlo** selezionare **HKEY_LOCAL_MACHINE** come radice del registro di sistema. Immettere **SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** per i sistemi a 64 bit o **SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** per i sistemi a 32 bit, quindi immettere **Install** come valore del registro di sistema. Scegliere **Avanti**.  
  
20. Nel riquadro **che cosa si vuole fare con il valore?** immettere **questo prodotto richiede l'installazione di Visual Studio 2015 isolated shell Redistributable.** come testo visualizzato e fare clic su **fine**.  
  
21. Ricompilare la soluzione Shell isolata per creare il progetto di installazione.  
  
     È possibile trovare il file Setup. exe nella cartella seguente:  
  
     \MyVSShellStub\MySetup\MySetup\Express\SingleImage\DiskImages\DISK1  
  
## <a name="testing-the-installation-program"></a>Test del programma di installazione  
 Per testare l'installazione, copiare il file Setup. exe in un computer diverso ed eseguire il file eseguibile di installazione. Dovrebbe essere possibile eseguire l'applicazione shell isolata.
