---
title: "Procedura dettagliata: Creazione di un programma di avvio automatico per visualizzare l'informativa sulla Privacy dei messaggi di richiesta | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- dependencies [.NET Framework], custom bootstrapper package
- deploying applications [Visual Studio], custom prerequisites
- Windows Installer deployment, prerequisites
- prerequisites [.NET Framework], custom bootstrapper package
ms.assetid: 2f3edd6a-84d1-4864-a1ae-6a13c5732aae
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6d93d9f771da9387661603f3eb71301e9d9aead7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63427138"
---
# <a name="walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt"></a>Procedura dettagliata: Creazione di un programma di avvio automatico per visualizzare un Prompt di Privacy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile configurare le applicazioni ClickOnce per l'aggiornamento automatico quando gli assembly con le versioni più recenti di file e delle versioni degli assembly saranno disponibili. Per assicurarsi che i clienti di consenso a questo comportamento, è possibile visualizzare un prompt di privacy a essi. Quindi, è possibile scegliere se concedere l'autorizzazione per l'applicazione per aggiornare automaticamente. Se l'applicazione non è consentita l'aggiornamento automatico, non viene installato.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
- Visual Studio 2010.  
  
## <a name="creating-an-update-consent-dialog-box"></a>Creazione di una finestra di dialogo di consenso di aggiornamento  
 Per visualizzare un prompt di privacy, creare un'applicazione che richiede il lettore a fornire il consenso agli aggiornamenti automatici per l'applicazione.  
  
#### <a name="to-create-a-consent-dialog-box"></a>Per creare una finestra di dialogo di consenso  
  
1. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
2. Nel **nuovo progetto** della finestra di dialogo fare clic su **Windows**, quindi fare clic su **WindowsFormsApplication**.  
  
3. Per il **Name**, digitare **ConsentDialog**, quindi fare clic su **OK**.  
  
4. Nella finestra di progettazione, fare clic sul form.  
  
5. Nel **delle proprietà** finestra Modifica il **testo** proprietà **della finestra di consenso di aggiornamento**.  
  
6. Nel **casella degli strumenti**, espandere **tutti i Windows Form**e trascinare un' **etichetta** controllo al form.  
  
7. Nella finestra di progettazione, fare clic sul controllo etichetta.  
  
8. Nel **delle proprietà** finestra Modifica il **testo** proprietà sotto **aspetto** al seguente:  
  
    L'applicazione che sta tentando di installare i controlli per gli aggiornamenti più recenti sul Web. Facendo clic su "Accetto", si autorizza l'applicazione per cercare e installare automaticamente gli aggiornamenti da Internet.  
  
9. Nel **casella degli strumenti**, trascinare un **casella di controllo** controllo al centro del form.  
  
10. Nel **delle proprietà** finestra Modifica il **testo** proprietà sotto **Layout** a **accetto**.  
  
11. Nel **casella degli strumenti**, trascinare un **pulsante** controllo in basso a sinistra del modulo.  
  
12. Nel **le proprietà** finestra Modifica il **testo** proprietà sotto **Layout** a **procedi**.  
  
13. Nel **delle proprietà** finestra Modifica il **(nome)** proprietà sotto **progettazione** a **ProceedButton**.  
  
14. Nel **casella degli strumenti**, trascinare un **pulsante** controllo nella parte inferiore destra del modulo.  
  
15. Nel **delle proprietà** finestra Modifica il **testo** proprietà sotto **Layout** per **Annulla**.  
  
16. Nel **delle proprietà** finestra Modifica il **(nome)** proprietà sotto **progettazione** a **CancelButton**.  
  
17. Nella finestra di progettazione, fare doppio clic il **accetto** casella di controllo per generare il gestore dell'evento CheckedChanged.  
  
18. Nel file di codice Form1, aggiungere il codice seguente per il gestore dell'evento CheckedChanged.  
  
     [!code-csharp[ConsentDialog#1](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#1)]
     [!code-vb[ConsentDialog#1](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#1)]  
  
19. Aggiornare il costruttore della classe per disabilitare il **procedi** pulsante per impostazione predefinita.  
  
     [!code-csharp[ConsentDialog#6](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#6)]
     [!code-vb[ConsentDialog#6](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#6)]  
  
20. Nel file di codice Form1, aggiungere il codice seguente per una variabile booleana rilevare se l'utente finale abbia dato il consenso agli aggiornamenti online.  
  
     [!code-csharp[ConsentDialog#3](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#3)]
     [!code-vb[ConsentDialog#3](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#3)]  
  
21. Nella finestra di progettazione, fare doppio clic il **procedi** pulsante per generare il gestore dell'evento Click.  
  
22. Nel file di codice Form1, aggiungere il codice seguente al gestore dell'evento Click per il **procedi** pulsante.  
  
     [!code-csharp[ConsentDialog#2](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#2)]
     [!code-vb[ConsentDialog#2](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#2)]  
  
23. Nella finestra di progettazione, fare doppio clic il **annullare** pulsante per generare il gestore dell'evento Click.  
  
24. Nel file di codice Form1, aggiungere il codice seguente per il gestore eventi Click per il **annullare** pulsante.  
  
     [!code-csharp[ConsentDialog#4](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#4)]
     [!code-vb[ConsentDialog#4](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#4)]  
  
25. Aggiornamento dell'applicazione per restituire un errore se l'utente finale non fornire il consenso agli aggiornamenti online.  
  
     Visual Basic solo per sviluppatori:  
  
    1. Nelle **Esplora soluzioni**, fare clic su **ConsentDialog**.  
  
    2. Nel **Project** menu, fare clic su **Aggiungi modulo**e quindi fare clic su **Add**.  
  
    3. Nel file di codice Module1.vb, aggiungere il codice seguente.  
  
        [!code-vb[ConsentDialog#7](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/module1.vb#7)]  
  
    4. Nel **progetto** menu, fare clic su **proprietà ConsentDialog**e quindi fare clic sul **applicazione** scheda.  
  
    5. Deselezionare l'opzione **Abilita framework applicazione**.  
  
    6. Nel **oggetto di avvio** elenco a discesa dal menu **Module1**.  
  
       > [!NOTE]
       > La disabilitazione di framework applicazione disattiva le funzionalità, ad esempio stili di Windows XP, gli eventi dell'applicazione, la schermata iniziale, un'applicazione a istanza singola e altro ancora. Per altre informazioni, vedere [Pagina Applicazione, Creazione progetti (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
       Per Visual c# solo per gli sviluppatori:  
  
       Aprire il file di codice Program.cs e aggiungere il codice seguente.  
  
       [!code-csharp[ConsentDialog#5](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/program.cs#5)]  
  
26. Nel **compilare** menu, fare clic su **BuildSolution**.  
  
## <a name="creating-the-custom-bootstrapper-package"></a>Creazione del pacchetto del programma di avvio automatico personalizzato  
 Per visualizzare il prompt di privacy per gli utenti finali, è possibile creare un pacchetto di programma di avvio automatico per l'applicazione della finestra di consenso di aggiornamento e includerlo come prerequisito in tutte le applicazioni ClickOnce.  
  
 Questa procedura viene illustrato come creare un pacchetto di programma di avvio automatico personalizzato creando i documenti seguenti:  
  
- Un Product manifest file per descrivere il contenuto del programma di avvio automatico.  
  
- Un file manifesto di package. XML per elencare gli aspetti specifici della localizzazione del pacchetto, ad esempio stringhe e le condizioni di licenza software.  
  
- Un documento per le condizioni di licenza software.  
  
#### <a name="step-1-to-create-the-bootstrapper-directory"></a>Passaggio 1: Per creare la directory di avvio automatico  
  
1. Creare una directory denominata **UpdateConsentDialog** in %PROGRAMFILES%\Microsoft Sdks\windows\v7.0A\Bootstrapper\Packages.  
  
    > [!NOTE]
    > Potrebbe essere necessario privilegi di amministratore per creare questa cartella.  
  
2. Nella directory UpdateConsentDialog, creare una sottodirectory denominata en.  
  
    > [!NOTE]
    > Creare una nuova directory per ciascuna lingua. Ad esempio, è possibile aggiungere le sottodirectory per le impostazioni locali de e fr. Queste directory conterrebbe il francese e tedesco stringhe e i language pack, se necessario.  
  
#### <a name="step-2-to-create-the-productxml-manifest-file"></a>Passaggio 2: Per creare il file manifesto di Product. Xml  
  
1. Creare un file di testo denominato `product.xml`.  
  
2. Nel file di Product. XML, aggiungere il codice XML seguente. Assicurarsi che non sovrascrivere il codice XML esistente.  
  
    ```  
    <Product  
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      ProductCode="Microsoft.Sample.EULA">  
      <!-- Defines the list of files to be copied on build. -->  
      <PackageFiles CopyAllPackageFiles="false">  
        <PackageFile Name="ConsentDialog.exe"/>  
      </PackageFiles>  
  
      <!-- Defines how to run the Setup package.-->  
      <Commands >  
        <Command PackageFile = "ConsentDialog.exe" Arguments=''>  
          <ExitCodes>  
            <ExitCode Value="0" Result="Success" />  
            <ExitCode Value="-1" Result="Fail" String="AU_Unaccepted" />  
            <DefaultExitCode Result="Fail"   
              FormatMessageFromSystem="true" String="GeneralFailure" />  
          </ExitCodes>  
        </Command>  
      </Commands>  
  
    </Product>  
    ```  
  
3. Salvare il file alla directory bootstrapper UpdateConsentDialog.  
  
#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>Passaggio 3: Per creare il file manifesto di package. XML e le condizioni di licenza software  
  
1. Creare un file di testo denominato `package.xml`.  
  
2. Nel file package. XML, aggiungere il codice XML seguente per definire le impostazioni locali e includere le condizioni di licenza software. Assicurarsi che non sovrascrivere il codice XML esistente.  
  
    ```  
    <Package   
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      Name="DisplayName"  
      Culture="Culture"  
      LicenseAgreement="eula.rtf">  
      <PackageFiles>  
        <PackageFile Name="eula.rtf"/>  
      </PackageFiles>  
  
      <!-- Defines a localizable string table for error messages. -->  
      <Strings>  
        <String Name="DisplayName">Update Consent Dialog</String>  
        <String Name="Culture">en</String>  
        <String Name="AU_Unaccepted">The automatic update agreement is not accepted.</String>  
        <String Name="GeneralFailure">A failure occurred attempting to launch the setup.</String>  
      </Strings>  
    </Package>  
    ```  
  
3. Salvare il file nella directory del programma di bootstrap UpdateConsentDialog nella sottodirectory en.  
  
4. Creare un documento denominato EULA. RTF per le condizioni di licenza software.  
  
    > [!NOTE]
    > Le condizioni di licenza software devono includere informazioni sulle licenze, garanzia, responsabilità e le leggi locali. Questi file devono essere specifiche delle impostazioni locali, assicurarsi che il file viene salvato in un formato che supporta i caratteri MBCS o UNICODE. Consultare l'ufficio legale sul contenuto delle condizioni di licenza software.  
  
5. Salvare il documento nella directory del programma di bootstrap UpdateConsentDialog nella sottodirectory en.  
  
6. Se necessario, creare un nuovo file manifesto di package. XML e un nuovo documento EULA. RTF per le condizioni di licenza software per ognuna delle impostazioni locali. Ad esempio, se è stata creata una sottodirectory per le impostazioni locali de e fr, creare condizioni di licenza software e i file manifesto separato package. XML e salvarli in sottodirectory fr e de.  
  
## <a name="setting-the-update-consent-application-as-a-prerequisite"></a>Impostare il consenso dell'utente di aggiornare un'applicazione come prerequisito  
 In Visual Studio, è possibile impostare l'applicazione di fornire il consenso di aggiornamento come prerequisito.  
  
#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>Per impostare l'applicazione di fornire il consenso di aggiornamento come prerequisito  
  
1. Nelle **Esplora soluzioni**, fare clic sul nome dell'applicazione che si desidera distribuire.  
  
2. Scegliere **Proprietà** *Nome progetto* dal menu **Progetto**.  
  
3. Scegliere il **Publish** pagina e quindi fare clic su **prerequisiti**.  
  
4. Selezionare **aggiornare consenso nell'apposita finestra**.  
  
    > [!NOTE]
    > Potrebbe essere necessario chiudere e riaprire Visual Studio per visualizzare la finestra di dialogo di consenso Update nella finestra di dialogo Prerequisiti.  
  
5. Fare clic su **OK**.  
  
## <a name="creating-and-testing-the-setup-program"></a>Creare e testare il programma di installazione  
 Dopo aver impostato l'applicazione di fornire il consenso di aggiornamento come prerequisito, è possibile generare il programma di installazione e il programma di avvio automatico per l'applicazione.  
  
#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>Per creare e testare il programma di installazione, non fare clic su accetto  
  
1. Nelle **Esplora soluzioni**, fare clic sul nome dell'applicazione che si desidera distribuire.  
  
2. Scegliere **Proprietà** *Nome progetto* dal menu **Progetto**.  
  
3. Fare clic sui **Publish** pagina e quindi fare clic su **pubblica**.  
  
4. Se l'output di pubblicazione non viene aperto automaticamente, passare all'output della pubblicazione.  
  
5. Eseguire il programma Setup.exe.  
  
     Il programma di installazione viene illustrato il contratto di licenza della finestra di consenso di aggiornamento software.  
  
6. Leggere il contratto di licenza software e quindi fare clic su **Accept**.  
  
     L'applicazione di aggiornamento finestra di dialogo di consenso viene visualizzata e Mostra il testo seguente: L'applicazione che sta tentando di installare i controlli per gli aggiornamenti più recenti sul Web. Facendo clic su accetto, si autorizza l'applicazione per cercare gli aggiornamenti automaticamente su Internet.  
  
7. Chiudere l'applicazione o fare clic su Annulla.  
  
     L'applicazione viene visualizzato un errore: Si è verificato un errore durante l'installazione dei componenti di sistema per *ApplicationName*. Impossibile continuare fino a quando tutti i componenti di sistema sono stati installati correttamente.  
  
8. Fare clic su Dettagli per visualizzare il messaggio di errore seguente: Finestra di dialogo aggiornamento fornire il consenso del componente non è riuscita per l'installazione con il messaggio di errore seguente: "Il contratto per l'aggiornamento automatico non è accettato". Impossibile installare i componenti seguenti:-finestra di dialogo di consenso Update  
  
9. Fare clic su **Chiudi**.  
  
#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>Per creare e testare il programma di installazione, fare clic su accetto  
  
1. Nelle **Esplora soluzioni**, fare clic sul nome dell'applicazione che si desidera distribuire.  
  
2. Scegliere **Proprietà** *Nome progetto* dal menu **Progetto**.  
  
3. Fare clic sui **Publish** pagina e quindi fare clic su **pubblica**.  
  
4. Se l'output di pubblicazione non viene aperto automaticamente, passare all'output della pubblicazione.  
  
5. Eseguire il programma Setup.exe.  
  
     Il programma di installazione viene illustrato il contratto di licenza della finestra di consenso di aggiornamento software.  
  
6. Leggere il contratto di licenza software e quindi fare clic su **Accept**.  
  
     L'applicazione di aggiornamento finestra di dialogo di consenso viene visualizzata e Mostra il testo seguente: L'applicazione che sta tentando di installare i controlli per gli aggiornamenti più recenti sul Web. Facendo clic su accetto, si autorizza l'applicazione per cercare gli aggiornamenti automaticamente su Internet.  
  
7. Fare clic su **accetto**, quindi fare clic su **procedi**.  
  
     Avvio dell'applicazione per l'installazione.  
  
8. Se viene visualizzata la finestra di dialogo Installazione applicazioni, fare clic su **installare**.  
  
## <a name="see-also"></a>Vedere anche  
 [Prerequisiti per la distribuzione dell'applicazione](../deployment/application-deployment-prerequisites.md)   
 [Creazione di pacchetti del programma di avvio automatico](../deployment/creating-bootstrapper-packages.md)   
 [Procedura: Creare un manifesto del prodotto](../deployment/how-to-create-a-product-manifest.md)   
 [Procedura: Creare un manifesto di pacchetto](../deployment/how-to-create-a-package-manifest.md)   
 [Riferimenti dello schema di prodotti e package](../deployment/product-and-package-schema-reference.md)
