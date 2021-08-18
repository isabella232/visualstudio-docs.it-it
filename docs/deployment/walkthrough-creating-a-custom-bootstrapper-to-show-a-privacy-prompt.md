---
title: Creare un programma di avvio automatico personalizzato con un prompt di privacy
description: Informazioni su come configurare le ClickOnce per l'aggiornamento automatico quando gli assembly con versioni di file e versioni di assembly più recenti diventano disponibili.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 5f0c34a56b610ee65f2f9d8d4ac506224950c302
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133614"
---
# <a name="walkthrough-create-a-custom-bootstrapper-with-a-privacy-prompt"></a>Procedura dettagliata: Creare un programma di avvio automatico personalizzato con un prompt di privacy
È possibile configurare le ClickOnce per l'aggiornamento automatico quando gli assembly con versioni di file e versioni di assembly più recenti diventano disponibili. Per assicurarsi che i clienti acconsentino a questo comportamento, è possibile visualizzare una richiesta di privacy. Possono quindi scegliere se concedere l'autorizzazione all'applicazione per l'aggiornamento automatico. Se l'applicazione non è autorizzata ad aggiornare automaticamente, non viene installata.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Visual Studio 2010.

## <a name="create-an-update-consent-dialog-box"></a>Finestra di dialogo Crea consenso per l'aggiornamento
 Per visualizzare una richiesta di privacy, creare un'applicazione che chiede al lettore di acconsentire agli aggiornamenti automatici per l'applicazione.

#### <a name="to-create-a-consent-dialog-box"></a>Per creare una finestra di dialogo di consenso

1. Scegliere **Nuovo** dal menu **File** e quindi fare clic su **Progetto**.

2. Nella finestra **di dialogo Nuovo Project** fare clic su **Windows** e quindi su **WindowsFormsApplication**.

3. Per **Nome** digitare **ConsentDialog** e quindi fare clic su **OK.**

4. Nella finestra di progettazione fare clic sul form.

5. Nella finestra **Proprietà** modificare la proprietà **Text** in **Update Consent Dialog**.

6. Nella casella **degli** strumenti espandere **Tutti Windows Form** e trascinare un controllo **Etichetta** nel form.

7. Nella finestra di progettazione fare clic sul controllo etichetta.

8. Nella finestra **Proprietà** modificare la **proprietà Text** in **Aspetto** nel modo seguente:

    L'applicazione che si sta per installare controlla la disponibilità degli aggiornamenti più recenti sul Web. Facendo clic su "Accetto", si autorizza l'applicazione a cercare e installare automaticamente gli aggiornamenti da Internet.

9. Nella casella **degli strumenti** trascinare un **controllo Casella** di controllo al centro del form.

10. Nella finestra **Proprietà** modificare la **proprietà Text** in **Layout** in **Accetto**.

11. Nella casella **degli strumenti** trascinare un **controllo Pulsante** in basso a sinistra nel form.

12. Nella finestra **Proprietà** modificare la **proprietà Text** in **Layout** in **Proceed**.

13. Nella finestra **Proprietà** modificare la proprietà **(Nome)** in **Progettazione** in **ProceedButton**.

14. Nella casella **degli strumenti** trascinare un **controllo Pulsante** in basso a destra nel form.

15. Nella finestra **Proprietà** modificare la **proprietà Text** in **Layout** in **Cancel**.

16. Nella finestra **Proprietà** modificare la proprietà **(Nome)** in **Progettazione** in **CancelButton**.

17. Nella finestra di progettazione fare doppio clic sulla casella **di controllo Accetto** per generare il gestore dell'evento CheckedChanged.

18. Nel file di codice Form1 aggiungere il codice seguente per il gestore eventi CheckedChanged.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb" id="Snippet1":::

19. Aggiornare il costruttore della classe per disabilitare il **pulsante** Continua per impostazione predefinita.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb" id="Snippet6":::

20. Nel file di codice Form1 aggiungere il codice seguente per una variabile booleana da rilevare se l'utente finale ha acconsentito agli aggiornamenti online.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb" id="Snippet3":::

21. Nella finestra di progettazione fare doppio clic sul **pulsante Continua** per generare il gestore dell'evento Click.

22. Nel file di codice Form1 aggiungere il codice seguente al gestore dell'evento Click per il **pulsante Proceed.**

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb" id="Snippet2":::


23. Nella finestra di progettazione fare doppio clic sul **pulsante Annulla** per generare il gestore dell'evento Click.

24. Nel file di codice Form1 aggiungere il codice seguente per il gestore dell'evento Click per il **pulsante** Annulla.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb" id="Snippet4":::

25. Aggiornare l'applicazione per restituire un errore se l'utente finale non acconsente agli aggiornamenti online.

     Solo per Visual Basic sviluppatori:

    1. In **Esplora soluzioni** fare clic **su ConsentDialog**.

    2. Scegliere **Aggiungi modulo dal** menu Project e quindi fare clic su **Aggiungi**.

    3. Nel file *di codice Module1.vb* aggiungere il codice seguente.

       :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/module1.vb" id="Snippet7":::

    4. Scegliere Proprietà **consentDialog** **dal** menu Project e quindi fare clic **sulla scheda** Applicazione.

    5. Deselezionare **Abilita framework applicazione**.

    6. Nel menu **a discesa Oggetto** di avvio selezionare **Module1.**

       > [!NOTE]
       > La disabilitazione del framework dell'applicazione Windows gli stili di visualizzazione di XP, gli eventi dell'applicazione, la schermata iniziale, l'applicazione a istanza singola e altro ancora. Per altre informazioni, vedere [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).

       Solo per gli sviluppatori Visual C#:

       Aprire il file *di codice Program.cs* e aggiungere il codice seguente.

       :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/program.cs" id="Snippet5":::

26. Scegliere **CompilaSoluzione** dal menu **Compila**.

## <a name="create-the-custom-bootstrapper-package"></a>Creare il pacchetto del programma di avvio automatico personalizzato
 Per visualizzare la richiesta di privacy agli utenti finali, è possibile creare un pacchetto del programma di avvio automatico personalizzato per l'applicazione Finestra di dialogo di consenso all'aggiornamento e includerlo come prerequisito in tutte le applicazioni ClickOnce client.

 Questa procedura illustra come creare un pacchetto del programma di avvio automatico personalizzato creando i documenti seguenti:

- Un *product.xml* file manifesto per descrivere il contenuto del programma di avvio automatico.

- Un *package.xml* file manifesto per elencare gli aspetti specifici della localizzazione del pacchetto, ad esempio le stringhe e le condizioni di licenza software.

- Documento per le condizioni di licenza software.

#### <a name="step-1-to-create-the-bootstrapper-directory"></a>Passaggio 1: Per creare la directory del programma di avvio automatico

1. Creare una directory denominata **UpdateConsentDialog** in *%PROGRAMFILES%\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages*.

    > [!NOTE]
    > Potrebbe essere necessario disporre di privilegi amministrativi per creare questa cartella.

2. Nella directory *UpdateConsentDialog* creare una sottodirectory denominata *en*.

    > [!NOTE]
    > Creare una nuova directory per ogni impostazione locale. Ad esempio, è possibile aggiungere sottodirectory per le impostazioni locali fr e de. Queste directory conterranno le stringhe e i Language Pack in francese e tedesco, se necessario.

#### <a name="step-2-to-create-the-productxml-manifest-file"></a>Passaggio 2: Per creare il product.xml manifesto

1. Creare un file di testo denominato *product.xml*.

2. Nel file *product.xml* aggiungere il codice XML seguente. Assicurarsi di non sovrascrivere il codice XML esistente.

    ```xml
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

3. Salvare il file nella directory del programma di avvio automatico UpdateConsentDialog.

#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>Passaggio 3: Creare il file manifesto package.xml e le condizioni di licenza software

1. Creare un file di testo denominato *package.xml*.

2. Nel file *package.xml* aggiungere il codice XML seguente per definire le impostazioni locali e includere le condizioni di licenza software. Assicurarsi di non sovrascrivere il codice XML esistente.

    ```xml
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

3. Salvare il file nella sottodirectory en nella directory del programma di avvio automatico UpdateConsentDialog.

4. Creare un documento denominato *eula.rtf per* le condizioni di licenza software.

    > [!NOTE]
    > Le condizioni di licenza software devono includere informazioni su licenze, garanzie, responsabilità e leggi locali. Questi file devono essere specifici delle impostazioni locali, quindi assicurarsi che il file sia salvato in un formato che supporti i caratteri MBCS o UNICODE. Consultare il reparto legale per informazioni sul contenuto delle condizioni di licenza software.

5. Salvare il documento nella sottodirectory en nella directory del programma di avvio automatico *UpdateConsentDialog.*

6. Se necessario, creare un nuovo file *package.xml* manifesto e un nuovo *documento eula.rtf* per le condizioni di licenza software per ogni impostazione locale. Ad esempio, se sono state create sottodirectory per le impostazioni locali fr e de, creare file manifesto package.xml separati e condizioni di licenza software e salvarli nelle sottodirectory fr e de.

## <a name="set-the-update-consent-application-as-a-prerequisite"></a>Impostare l'applicazione di consenso per l'aggiornamento come prerequisito
 In Visual Studio è possibile impostare l'applicazione Update Consent come prerequisito.

#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>Per impostare Update Consent Application come prerequisito

1. In **Esplora soluzioni** fare clic sul nome dell'applicazione che si vuole distribuire.

2. Scegliere Proprietà **NomeProgetto** dal menu Project  **progetto**.

3. Fare clic **sulla pagina** Pubblica e quindi su **Prerequisiti**.

4. Selezionare **Aggiorna finestra di dialogo consenso**.

    > [!NOTE]
    > Potrebbe essere necessario chiudere e riaprire Visual Studio finestra di dialogo aggiorna consenso nella finestra di dialogo Prerequisiti.

5. Fare clic su **OK**.

## <a name="create-and-test-the-setup-program"></a>Creare e testare il programma di installazione
 Dopo aver impostato l'applicazione Update Consent come prerequisito, è possibile generare il programma di installazione e il programma di avvio automatico per l'applicazione.

#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>Per creare e testare il programma di installazione senza fare clic su Accetto

1. In **Esplora soluzioni** fare clic sul nome dell'applicazione che si vuole distribuire.

2. Scegliere Proprietà **NomeProgetto** dal menu Project  **progetto**.

3. Fare clic **sulla pagina** Pubblica e quindi su **Pubblica adesso**.

4. Se l'output di pubblicazione non si apre automaticamente, passare all'output di pubblicazione.

5. Eseguire il *Setup.exe* programma.

     Nel programma di installazione viene visualizzato il contratto di licenza software update consent dialog.

6. Leggere il contratto di licenza software e quindi fare clic su **Accetta**.

     Viene visualizzata l'applicazione Finestra di dialogo di consenso all'aggiornamento con il testo seguente: L'applicazione che si sta per installare controlla la disponibilità degli aggiornamenti più recenti sul Web. Facendo clic su Accetto, si autorizza l'applicazione a verificare automaticamente la disponibilità di aggiornamenti su Internet.

7. Chiudere l'applicazione o fare clic su Annulla.

     L'applicazione visualizza un errore: Si è verificato un errore durante l'installazione dei componenti di sistema per *ApplicationName*. Il programma di installazione non può continuare fino a quando tutti i componenti di sistema non sono stati installati correttamente.

8. Fare clic su Dettagli per visualizzare il messaggio di errore seguente: Impossibile installare la finestra di dialogo di consenso per l'aggiornamento dei componenti con il messaggio di errore seguente: "Il contratto di aggiornamento automatico non è accettato". Impossibile installare i componenti seguenti: - Finestra di dialogo di consenso per l'aggiornamento

9. Fare clic su **Chiudi**.

#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>Per creare e testare il programma di installazione facendo clic su Accetto

1. In **Esplora soluzioni** fare clic sul nome dell'applicazione che si vuole distribuire.

2. Nel menu **Project** scegliere *Proprietà NomeProgetto* .

3. Fare clic **sulla pagina** Pubblica e quindi su **Pubblica adesso**.

4. Se l'output di pubblicazione non si apre automaticamente, passare all'output di pubblicazione.

5. Eseguire il *Setup.exe* programma.

     Il programma di installazione mostra il Contratto di licenza software di Dialogo di consenso aggiornamento.

6. Leggere il contratto di licenza software e quindi fare clic su **Accetta**.

     Viene visualizzata l'applicazione Finestra di dialogo di consenso all'aggiornamento con il testo seguente: L'applicazione che si sta per installare controlla la disponibilità degli aggiornamenti più recenti sul Web. Facendo clic su Accetto, si autorizza l'applicazione a verificare automaticamente la disponibilità di aggiornamenti su Internet.

7. Fare **clic su Accetto** e quindi su **Continua.**

     Viene avviata l'installazione dell'applicazione.

8. Se viene visualizzata la finestra di dialogo Installazione applicazione , fare clic **su Installa**.

## <a name="see-also"></a>Vedi anche
- [Prerequisiti per la distribuzione dell'applicazione](../deployment/application-deployment-prerequisites.md)
- [Creare pacchetti del programma di avvio automatico personalizzati](../deployment/creating-bootstrapper-packages.md)
- [Procedura: Creare il manifesto di un prodotto](../deployment/how-to-create-a-product-manifest.md)
- [Procedura: Creare un manifesto del pacchetto](../deployment/how-to-create-a-package-manifest.md)
- [Informazioni di riferimento sullo schema di prodotti e pacchetti](../deployment/product-and-package-schema-reference.md)