---
title: 'Procedura dettagliata: creazione di un programma di avvio automatico personalizzato per visualizzare un prompt di privacy | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839608"
---
# <a name="walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt"></a>Procedura dettagliata: creazione di un programma di avvio automatico per visualizzare un prompt di privacy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile configurare le applicazioni ClickOnce per l'aggiornamento automatico quando diventano disponibili assembly con versioni di file e versioni di assembly più recenti. Per assicurarsi che i clienti accettino questo comportamento, è possibile visualizzare un messaggio di richiesta di privacy. Quindi, possono scegliere se concedere l'autorizzazione all'applicazione per l'aggiornamento automatico. Se l'applicazione non è consentita per l'aggiornamento automatico, non viene installata.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
- Visual Studio 2010.  
  
## <a name="creating-an-update-consent-dialog-box"></a>Creazione di una finestra di dialogo di consenso dell'aggiornamento  
 Per visualizzare una richiesta di privacy, creare un'applicazione che chieda al lettore di concedere il consenso agli aggiornamenti automatici per l'applicazione.  
  
#### <a name="to-create-a-consent-dialog-box"></a>Per creare una finestra di dialogo di consenso  
  
1. Scegliere **Nuovo** dal menu **File**e quindi fare clic su **Progetto**.  
  
2. Nella finestra di dialogo **nuovo progetto** fare clic su **Windows**e quindi su **WindowsFormsApplication**.  
  
3. Per il **nome**digitare **ConsentDialog**e quindi fare clic su **OK**.  
  
4. Nella finestra di progettazione fare clic sul form.  
  
5. Nella finestra **Proprietà** modificare la proprietà **Text** in **Aggiorna finestra di dialogo di consenso**.  
  
6. Nella **casella degli strumenti**espandere **tutti i Windows Forms**e trascinare un controllo **etichetta** nel form.  
  
7. Nella finestra di progettazione fare clic sul controllo etichetta.  
  
8. Nella finestra **Proprietà** modificare la proprietà **Text** in **aspetto** nel modo seguente:  
  
    L'applicazione che si sta per installare controlla gli aggiornamenti più recenti sul Web. Se si fa clic su "Accetto", si autorizza l'applicazione a verificare e installare automaticamente gli aggiornamenti da Internet.  
  
9. Nella **casella degli strumenti**trascinare un controllo **CheckBox** al centro del form.  
  
10. Nella finestra **Proprietà** modificare la proprietà **Text** in **layout** **su Accetto**.  
  
11. Nella **casella degli strumenti**trascinare un controllo **Button** in basso a sinistra nel form.  
  
12. Nella finestra **Proprietà** modificare la proprietà **Text** in **layout** per **continuare**.  
  
13. Nella finestra **Proprietà** modificare la proprietà **(Name)** in **progettazione** in **ProceedButton**.  
  
14. Nella **casella degli strumenti**trascinare un controllo **Button** nella parte inferiore destra del form.  
  
15. Nella finestra **Proprietà** modificare la proprietà **Text** in **layout** in **Annulla**.  
  
16. Nella finestra **Proprietà** modificare la proprietà **(Name)** in **progettazione** in **CancelButton**.  
  
17. Nella finestra di progettazione fare doppio clic sulla casella di controllo **Accetto** per generare il gestore dell'evento CheckedChanged.  
  
18. Nel file di codice Form1 aggiungere il codice seguente per il gestore dell'evento CheckedChanged.  
  
     [!code-csharp[ConsentDialog#1](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#1)]
     [!code-vb[ConsentDialog#1](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#1)]  
  
19. Aggiornare il costruttore della classe per disabilitare il pulsante **continua** per impostazione predefinita.  
  
     [!code-csharp[ConsentDialog#6](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#6)]
     [!code-vb[ConsentDialog#6](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#6)]  
  
20. Nel file di codice Form1 aggiungere il codice seguente per una variabile booleana per rilevare se l'utente finale ha acconsentito agli aggiornamenti online.  
  
     [!code-csharp[ConsentDialog#3](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#3)]
     [!code-vb[ConsentDialog#3](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#3)]  
  
21. Nella finestra di progettazione fare doppio clic sul pulsante **continua** per generare il gestore dell'evento click.  
  
22. Nel file di codice Form1 aggiungere il codice seguente al gestore dell'evento click per il pulsante **continua** .  
  
     [!code-csharp[ConsentDialog#2](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#2)]
     [!code-vb[ConsentDialog#2](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#2)]  
  
23. Nella finestra di progettazione fare doppio clic sul pulsante **Annulla** per generare il gestore dell'evento click.  
  
24. Nel file di codice Form1 aggiungere il codice seguente per il gestore dell'evento click per il pulsante **Annulla** .  
  
     [!code-csharp[ConsentDialog#4](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#4)]
     [!code-vb[ConsentDialog#4](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#4)]  
  
25. Aggiornare l'applicazione per restituire un errore se l'utente finale non acconsente agli aggiornamenti online.  
  
     Solo per gli sviluppatori Visual Basic:  
  
    1. In **Esplora soluzioni**fare clic su **ConsentDialog**.  
  
    2. Scegliere **Aggiungi modulo**dal menu **progetto** , quindi fare clic su **Aggiungi**.  
  
    3. Nel file di codice Module1. vb aggiungere il codice seguente.  
  
        [!code-vb[ConsentDialog#7](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/module1.vb#7)]  
  
    4. Scegliere **Proprietà ConsentDialog**dal menu **progetto** e quindi fare clic sulla scheda **applicazione** .  
  
    5. Deselezionare **Abilita framework applicazione**.  
  
    6. Nel menu a discesa **oggetto di avvio** selezionare **Module1**.  
  
       > [!NOTE]
       > La disabilitazione del Framework applicazione disattiva funzionalità come gli stili di visualizzazione di Windows XP, gli eventi dell'applicazione, la schermata iniziale, l'applicazione a istanza singola e altro ancora. Per altre informazioni, vedere [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
       Solo per gli sviluppatori di Visual C#:  
  
       Aprire il file di codice Program.cs e aggiungere il codice seguente.  
  
       [!code-csharp[ConsentDialog#5](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/program.cs#5)]  
  
26. Scegliere **BuildSolution**dal menu **Compila** .  
  
## <a name="creating-the-custom-bootstrapper-package"></a>Creazione del pacchetto del programma di avvio automatico personalizzato  
 Per visualizzare la richiesta di privacy per gli utenti finali, è possibile creare un pacchetto del programma di avvio automatico personalizzato per l'applicazione della finestra di dialogo di consenso dell'aggiornamento e includerlo come prerequisito in tutte le applicazioni ClickOnce.  
  
 Questa procedura illustra come creare un pacchetto del programma di avvio automatico personalizzato creando i documenti seguenti:  
  
- Un product.xml file manifesto per descrivere il contenuto del programma di avvio automatico.  
  
- Un package.xml file manifesto per elencare gli aspetti specifici della localizzazione del pacchetto, ad esempio le stringhe e le condizioni di licenza software.  
  
- Documento per le condizioni di licenza software.  
  
#### <a name="step-1-to-create-the-bootstrapper-directory"></a>Passaggio 1: creare la directory del programma di avvio automatico  
  
1. Creare una directory denominata **UpdateConsentDialog** nel percorso%ProgramFiles%\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages.  
  
    > [!NOTE]
    > Per creare questa cartella, potrebbero essere necessari privilegi amministrativi.  
  
2. Nella directory UpdateConsentDialog creare una sottodirectory denominata en.  
  
    > [!NOTE]
    > Creare una nuova directory per ogni impostazione locale. Ad esempio, è possibile aggiungere sottodirectory per le impostazioni locali FR e de. Se necessario, queste directory contengono le stringhe e i Language Pack in francese e tedesco.  
  
#### <a name="step-2-to-create-the-productxml-manifest-file"></a>Passaggio 2: creare il file manifesto product.xml  
  
1. Creare un file di testo denominato `product.xml` .  
  
2. Nel file product.xml aggiungere il codice XML seguente. Assicurarsi di non sovrascrivere il codice XML esistente.  
  
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
  
3. Salvare il file nella directory UpdateConsentDialog del programma di avvio automatico.  
  
#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>Passaggio 3: creare il file manifesto package.xml e le condizioni di licenza software  
  
1. Creare un file di testo denominato `package.xml` .  
  
2. Nel file package.xml aggiungere il seguente codice XML per definire le impostazioni locali e includere le condizioni di licenza software. Assicurarsi di non sovrascrivere il codice XML esistente.  
  
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
  
3. Salvare il file nella sottodirectory en nella directory UpdateConsentDialog del programma di avvio automatico.  
  
4. Creare un documento denominato EULA. RTF per le condizioni di licenza software.  
  
    > [!NOTE]
    > Le condizioni di licenza software devono includere informazioni su licenze, garanzie, passività e leggi locali. Questi file devono essere specifici delle impostazioni locali, quindi assicurarsi che il file venga salvato in un formato che supporti i caratteri MBCS o UNICODE. Consultare il reparto legale sul contenuto delle condizioni di licenza software.  
  
5. Salvare il documento nella sottodirectory en nella directory UpdateConsentDialog del programma di avvio automatico.  
  
6. Se necessario, creare un nuovo file manifesto package.xml e un nuovo documento EULA. RTF per le condizioni di licenza software per ciascuna impostazione locale. Se, ad esempio, sono state create sottodirectory per le impostazioni locali FR e de, creare file manifesto package.xml e condizioni di licenza software distinti e salvarli nelle sottodirectory fr e de.  
  
## <a name="setting-the-update-consent-application-as-a-prerequisite"></a>Impostazione dell'applicazione di consenso dell'aggiornamento come prerequisito  
 In Visual Studio è possibile impostare l'applicazione di consenso dell'aggiornamento come prerequisito.  
  
#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>Per impostare l'applicazione di consenso dell'aggiornamento come prerequisito  
  
1. In **Esplora soluzioni**fare clic sul nome dell'applicazione che si desidera distribuire.  
  
2. Scegliere **Proprietà***Nome progetto dal menu * **Progetto**.  
  
3. Fare clic sulla pagina **pubblica** , quindi fare clic su **prerequisiti**.  
  
4. Selezionare la **finestra di dialogo di consenso dell'aggiornamento**.  
  
    > [!NOTE]
    > Potrebbe essere necessario chiudere e riaprire Visual Studio per visualizzare la finestra di dialogo di consenso dell'aggiornamento nella finestra di dialogo Prerequisiti.  
  
5. Fare clic su **OK**.  
  
## <a name="creating-and-testing-the-setup-program"></a>Creazione e test del programma di installazione  
 Dopo aver impostato l'applicazione di consenso dell'aggiornamento come prerequisito, è possibile generare il programma di installazione e il programma di avvio automatico per l'applicazione.  
  
#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>Per creare e testare il programma di installazione facendo clic su Accetto  
  
1. In **Esplora soluzioni**fare clic sul nome dell'applicazione che si desidera distribuire.  
  
2. Scegliere **Proprietà***Nome progetto dal menu * **Progetto**.  
  
3. Fare clic sulla pagina **pubblica** , quindi fare clic su **pubblica ora**.  
  
4. Se l'output di pubblicazione non viene aperto automaticamente, passare all'output di pubblicazione.  
  
5. Eseguire il programma Setup.exe.  
  
     Il programma di installazione Visualizza il contratto di licenza software per la finestra di dialogo di autorizzazione aggiornamenti.  
  
6. Leggere il contratto di licenza software, quindi fare clic su **Accetto**.  
  
     Viene visualizzata l'applicazione finestra di dialogo consenso aggiornamento con il testo seguente: l'applicazione da installare controlla gli aggiornamenti più recenti sul Web. Facendo clic su Accetto, si autorizza l'applicazione a verificare la disponibilità di aggiornamenti automaticamente in Internet.  
  
7. Chiudere l'applicazione o fare clic su Annulla.  
  
     Nell'applicazione viene visualizzato un errore: si è verificato un errore durante l'installazione dei componenti di sistema per *ApplicationName*. Impossibile continuare l'installazione fino a quando tutti i componenti di sistema non sono stati installati correttamente.  
  
8. Fare clic su dettagli per visualizzare il messaggio di errore seguente: Impossibile installare la finestra di dialogo di consenso aggiornamento componenti con il seguente messaggio di errore: "il contratto di aggiornamento automatico non è accettato". Impossibile installare i componenti seguenti: finestra di dialogo di consenso per l'aggiornamento  
  
9. Fare clic su **Close**.  
  
#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>Per creare e testare il programma di installazione facendo clic su Accetto  
  
1. In **Esplora soluzioni**fare clic sul nome dell'applicazione che si desidera distribuire.  
  
2. Scegliere **Proprietà***Nome progetto dal menu * **Progetto**.  
  
3. Fare clic sulla pagina **pubblica** , quindi fare clic su **pubblica ora**.  
  
4. Se l'output di pubblicazione non viene aperto automaticamente, passare all'output di pubblicazione.  
  
5. Eseguire il programma Setup.exe.  
  
     Il programma di installazione Visualizza il contratto di licenza software per la finestra di dialogo di autorizzazione aggiornamenti.  
  
6. Leggere il contratto di licenza software, quindi fare clic su **Accetto**.  
  
     Viene visualizzata l'applicazione finestra di dialogo consenso aggiornamento con il testo seguente: l'applicazione da installare controlla gli aggiornamenti più recenti sul Web. Facendo clic su Accetto, si autorizza l'applicazione a verificare la disponibilità di aggiornamenti automaticamente in Internet.  
  
7. Fare clic su **Accetto**e quindi su **continua**.  
  
     Viene avviata l'installazione dell'applicazione.  
  
8. Se viene visualizzata la finestra di dialogo installazione applicazione, fare clic su **Installa**.  
  
## <a name="see-also"></a>Vedere anche  
 [Prerequisiti per la distribuzione dell'applicazione](../deployment/application-deployment-prerequisites.md)   
 [Creazione di pacchetti del programma di avvio automatico](../deployment/creating-bootstrapper-packages.md)   
 [Procedura: creare un manifesto del prodotto](../deployment/how-to-create-a-product-manifest.md)   
 [Procedura: creare un manifesto del pacchetto](../deployment/how-to-create-a-package-manifest.md)   
 [Riferimenti dello schema di prodotti e package](../deployment/product-and-package-schema-reference.md)
