---
title: "Procedura dettagliata: Distribuzione manuale di un'applicazione ClickOnce | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Mage.exe, manual ClickOnce deployments
- MageUI.exe, manual ClickOnce deployments
- deploying applications [ClickOnce], manual ClickOnce deployments
- ClickOnce deployment, manually
- ClickOnce deployment, SDK tools
- manual ClickOnce deployments
- manifests [ClickOnce]
ms.assetid: ccee6551-a1b9-4ca2-8845-9c1cf4ac2560
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 60173bd8a48b067757bbccfad42a2feaf5633082
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63405785"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application"></a>Procedura dettagliata: Distribuire manualmente un'applicazione ClickOnce
Se non è possibile utilizzare Visual Studio per distribuire il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione oppure è necessario usare le funzionalità avanzate di distribuzione, ad esempio la distribuzione di applicazioni attendibili, è consigliabile usare il *Mage.exe* lo strumento da riga di comando per creare la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesti. Questa procedura dettagliata viene descritto come creare un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione con la versione della riga di comando (*Mage.exe*) o la versione con interfaccia grafica (*MageUI.exe*) della generazione del manifesto e Strumento di modifica.

## <a name="prerequisites"></a>Prerequisiti
 Questa procedura dettagliata presenta alcuni prerequisiti e le opzioni che è necessario scegliere prima di creare una distribuzione.

- Installare *Mage.exe* e *MageUI.exe*.

   *Mage.exe* e *MageUI.exe* fanno parte di [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. È necessario avere il [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] installato o la versione del [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] inclusi in Visual Studio. Per altre informazioni, vedere [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=158044) su MSDN.

- Fornire un'applicazione da distribuire.

   Questa procedura dettagliata si presuppone che si dispone di un'applicazione Windows che si è pronti per la distribuzione. Questa applicazione verrà considerata AppToDeploy.

- Determinare come verrà distribuita la distribuzione.

   Le opzioni di distribuzione includono: Web, condivisione file o CD. Per altre informazioni, vedere [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md).

- Determinare se l'applicazione richiede un livello di attendibilità elevato.

   Se l'applicazione richiede attendibilità completa, ad esempio, accesso completo al sistema dell'utente, è possibile usare la `-TrustLevel` opzione di *Mage.exe* impostare questo valore. Se si vuole definire un'autorizzazione personalizzata impostata per l'applicazione, è possibile copiare la sezione autorizzazioni Internet o intranet dal manifesto di un'altra, modificarlo in base alle esigenze e aggiungerlo al manifesto dell'applicazione usando un editor di testo o  *MageUI.exe*. Per altre informazioni, vedere [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md).

- Ottenere un certificato Authenticode.

   È necessario firmare la distribuzione con un certificato Authenticode. È possibile generare un certificato di test con Visual Studio, *MageUI.exe*, o *MakeCert.exe* e *Pvk2Pfx.exe* strumenti, oppure è possibile ottenere un certificato da un certificato Autorità (CA). Se si sceglie di usare la distribuzione di applicazioni attendibili, è anche necessario eseguire un'unica installazione del certificato in tutti i computer client. Per altre informazioni, vedere [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).

  > [!NOTE]
  > È anche possibile firmare la distribuzione con un certificato CNG che è possibile ottenere da un'autorità di certificazione.

- Assicurarsi che l'applicazione non dispone di un manifesto con le informazioni di controllo dell'account utente.

   È necessario determinare se l'applicazione contiene un manifesto con informazioni di controllo Account utente (UAC), ad esempio un `<dependentAssembly>` elemento. Per esaminare un manifesto dell'applicazione, è possibile utilizzare il Windows Sysinternals [Sigcheck](http://go.microsoft.com/fwlink/?LinkId=158035) utilità.

   Se l'applicazione contiene un manifesto con dettagli controllo dell'account utente, è necessario ricompilarla senza le informazioni di controllo dell'account utente. Per un progetto c# in Visual Studio, aprire le proprietà del progetto e selezionare la scheda dell'applicazione. Nel **Manifest** elenco a discesa, seleziona **Crea applicazione senza manifesto**. Per un progetto di Visual Basic in Visual Studio, aprire le proprietà del progetto, selezionare la scheda applicazione e fare clic su **impostazioni di controllo dell'account utente visualizzazione**. Nel file manifesto aperto, rimuovere tutti gli elementi all'interno di singolo `<asmv1:assembly>` elemento.

- Determinare se l'applicazione richiede i prerequisiti nei computer client.

   [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] le applicazioni distribuite da Visual Studio possono includere un programma di bootstrap di installazione dei prerequisiti (*setup.exe*) con la distribuzione. Questa procedura dettagliata crea due manifesti necessari per un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione. È possibile creare un programma di avvio automatico di prerequisiti usando il [attività GenerateBootstrapper](../msbuild/generatebootstrapper-task.md).

### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>Distribuire un'applicazione con lo strumento da riga di comando Mage.exe

1. Creare una directory in cui verranno archiviati i [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] i file di distribuzione.

2. Nella directory di distribuzione che appena creata, creare una sottodirectory della versione. Se questa è la prima volta che si sta distribuendo l'applicazione, assegnare un nome nella sottodirectory della versione **1.0.0.0**.

   > [!NOTE]
   > La versione della distribuzione può essere distinta da quella dell'applicazione.

3. Copiare tutti i file dell'applicazione nella sottodirectory della versione, inclusi file eseguibili, gli assembly, le risorse e i file di dati. Se necessario, è possibile creare ulteriori sottodirectory che contengono i file aggiuntivi.

4. Aprire il [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] o comandi di Visual Studio prompt e passare alla sottodirectory della versione.

5. Creare il manifesto dell'applicazione con una chiamata a *Mage.exe*. L'istruzione seguente crea un manifesto dell'applicazione per il codice compilato per l'esecuzione nel processore Intel x86.

   ```cmd
   mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .
   ```

   > [!NOTE]
   > Assicurarsi di includere il punto (.) dopo il `-FromDirectory` opzione, che indica la directory corrente. Se non si include il punto, è necessario specificare il percorso ai file dell'applicazione.

6. Firmare il manifesto dell'applicazione con il certificato Authenticode. Sostituire *mycert. pfx* con il percorso al file del certificato. Sostituire *passwd* con la password per il file del certificato.

   ```cmd
   mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd
   ```

   il SDK di .NET Framework 4.6.2, che viene distribuito con Visual Studio e con il SDK di Windows, a partire *mage.exe* firma i manifesti con CNG e con i certificati Authenticode. Usare gli stessi parametri della riga di comando come con i certificati Authenticode.

7. Passare alla radice della directory di distribuzione.

8. Generare il manifesto di distribuzione con una chiamata a *Mage.exe*. Per impostazione predefinita *Mage.exe* contrassegnerà il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione come un'applicazione installata, in modo che non può essere eseguito sia online e offline. Per rendere l'applicazione disponibile solo quando l'utente è online, usare il `-Install` con un valore di opzione `false`. Se si usa l'impostazione predefinita, e gli utenti installeranno l'applicazione da un sito Web o una condivisione di file, assicurarsi che il valore della `-ProviderUrl` opzione punti al percorso dell'applicazione manifesto nel server Web o nella condivisione.

   ```cmd
   mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application
   ```

9. Firmare il manifesto di distribuzione con il certificato Authenticode o CNG.

    ```cmd
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd
    ```

10. Copiare tutti i file nella directory di distribuzione per il supporto o nella destinazione di distribuzione. Può trattarsi di un file della cartella in un sito Web o FTP del sito, una condivisione file o un CD-ROM.

11. Fornire agli utenti con l'URL, UNC o supporti fisici necessari per installare l'applicazione. Se si specifica un URL o un percorso UNC, è necessario indicare agli utenti il percorso completo del manifesto di distribuzione. Ad esempio, se viene distribuito AppToDeploy http://webserver01/ nella directory AppToDeploy, il percorso URL completo dovrebbe essere http://webserver01/AppToDeploy/AppToDeploy.application.

### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>Distribuire un'applicazione con lo strumento con interfaccia grafica MageUI.exe

1. Creare una directory in cui verranno archiviati i [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] i file di distribuzione.

2. Nella directory di distribuzione che appena creata, creare una sottodirectory della versione. Se questa è la prima volta che si sta distribuendo l'applicazione, assegnare un nome nella sottodirectory della versione **1.0.0.0**.

   > [!NOTE]
   > La versione della distribuzione è probabilmente diverso dalla versione dell'applicazione.

3. Copiare tutti i file dell'applicazione nella sottodirectory della versione, inclusi file eseguibili, gli assembly, le risorse e i file di dati. Se necessario, è possibile creare ulteriori sottodirectory che contengono i file aggiuntivi.

4. Avviare il *MageUI.exe* strumento con interfaccia grafico.

   ```cmd
   MageUI.exe
   ```

5. Creare un nuovo manifesto dell'applicazione selezionando **File**, **New**, **Application Manifest** dal menu di scelta.

6. Nel valore predefinito **nome** scheda, digitare il nome e numero di versione di questa distribuzione. Specificare anche il **processore** che l'applicazione viene compilata, ad esempio x86.

7. Selezionare il **file** scheda e fare clic sui puntini di sospensione (**...** ) accanto al pulsante il **directory dell'applicazione** casella di testo. Oggetto **Sfoglia per cartelle** verrà visualizzata la finestra di dialogo.

8. Selezionare la sottodirectory della versione che contiene i file dell'applicazione e quindi fare clic su **OK**.

9. Se si intende distribuire da Internet Information Services (IIS), selezionare la **quando la compilazione aggiunge l'estensione. deploy a tutti i file che non è presente** casella di controllo.

10. Scegliere il **Popola** pulsante per aggiungere tutti i file dell'applicazione per l'elenco dei file. Se l'applicazione contiene più di un file eseguibile, contrassegnare il file eseguibile principale per la distribuzione dell'applicazione di avvio selezionando **punto di ingresso** dalle **tipo di File** elenco a discesa. (Se l'applicazione contiene un solo file eseguibile *MageUI.exe* verrà contrassegnato per l'utente.)

11. Selezionare il **autorizzazioni necessarie** scheda e selezionare il livello di attendibilità che è necessario che l'applicazione per l'asserzione. Il valore predefinito è **FullTrust**, che sarà idoneo per la maggior parte delle applicazioni.

12. Selezionare **File**, **Salva con nome** dal menu di scelta. Una finestra di dialogo Opzioni di firma verrà visualizzata la richiesta di firmare il manifesto dell'applicazione.

13. Se si dispone di un certificato archiviato come file nel file system, usare il **firma con file di certificato** opzione e selezionare il certificato dal file system con i puntini di sospensione (**...** ) pulsante. Quindi digitare la password del certificato.

     -oppure-

     Se il certificato si trova in un archivio di certificati accessibile dal computer, selezionare la **firma con certificato archiviato** opzione e selezionare il certificato dall'elenco fornito.

14. Fare clic su **OK** per firmare il manifesto dell'applicazione. Il **Salva con nome** verrà visualizzata la finestra di dialogo.

15. Nel **Salva con nome** finestra di dialogo, specificare la directory della versione e quindi fare clic su **salvare**.

16. Selezionare **File**, **New**, **manifesto della distribuzione** dal menu per creare il manifesto della distribuzione.

17. Nel **Name** , specificare un nome e numero di versione per questa distribuzione (**1.0.0.0** in questo esempio). Specificare anche il **processore** che l'applicazione viene compilata, ad esempio x86.

18. Selezionare il **Description** scheda e specificare i valori per **server di pubblicazione** e **prodotto**. (**Prodotto** è il nome assegnato all'applicazione nel menu Start di Windows quando l'applicazione viene installata in un computer client per l'uso offline.)

19. Selezionare il **opzioni di distribuzione** scheda e nella **percorso iniziale** testo, specificare il percorso del manifesto dell'applicazione nel server Web o nella condivisione. Ad esempio,  *\\\myServer\myShare\AppToDeploy.application*.

20. Se è stato aggiunto il *deploy* estensione in un passaggio precedente, selezionare anche **Usa l'estensione. deploy** qui.

21. Selezionare il **opzioni di aggiornamento** scheda e specificare quanto spesso si desidera che questa applicazione per l'aggiornamento. Se l'applicazione usa <xref:System.Deployment.Application.UpdateCheckInfo> per cercare gli aggiornamenti se stesso, cancellare il **l'applicazione deve controllare disponibilità di aggiornamenti** casella di controllo.

22. Selezionare il **riferimento all'applicazione** scheda e quindi fare clic sui **Seleziona manifesto** pulsante. Viene visualizzata una finestra di dialogo Apri.

23. Selezionare il manifesto dell'applicazione creata in precedenza e quindi fare clic su **aperto**.

24. Selezionare **File**, **Salva con nome** dal menu di scelta. Oggetto **opzioni di firma** verrà visualizzata la finestra di dialogo che richiede di firmare il manifesto della distribuzione.

25. Se si dispone di un certificato archiviato come file nel file system, usare il **firma con file di certificato** opzione e selezionare il certificato dal file system con i puntini di sospensione (**...** ) pulsante. Quindi digitare la password del certificato.

     -oppure-

     Se il certificato si trova in un archivio di certificati accessibile dal computer, selezionare la **firma con certificato archiviato** opzione e selezionare il certificato dall'elenco fornito.

26. Fare clic su **OK** per firmare il manifesto della distribuzione. Il **Salva con nome** verrà visualizzata la finestra di dialogo.

27. Nel **Salva con nome** della finestra di dialogo Sposta su una directory nella radice di distribuzione e quindi fare clic su **salvare**.

28. Copiare tutti i file nella directory di distribuzione per il supporto o nella destinazione di distribuzione. Può trattarsi di un file della cartella in un sito Web o FTP del sito, una condivisione file o un CD-ROM.

29. Fornire agli utenti con l'URL, UNC o supporti fisici necessari per installare l'applicazione. Se si specifica un URL o un percorso UNC, è necessario indicare agli utenti il percorso completo del manifesto di distribuzione. Ad esempio, se viene distribuito AppToDeploy http://webserver01/ nella directory AppToDeploy, il percorso URL completo dovrebbe essere http://webserver01/AppToDeploy/AppToDeploy.application.

## <a name="next-steps"></a>Passaggi successivi
 Quando è necessario distribuire una nuova versione dell'applicazione, creare una nuova directory denominata in base alla nuova versione, ad esempio, 1.0.0.1 copiare i nuovi file di applicazione nella nuova directory. Successivamente, è necessario seguire i passaggi precedenti per creare e firmare un nuovo manifesto dell'applicazione, aggiornare e firmare il manifesto della distribuzione. Prestare attenzione a specificare la stessa versione superiore in entrambe le *Mage.exe* `-New` e `-Update` chiamate, come [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Aggiorna solo le versioni successive, con l'intero più a sinistra più significativo. Se è stata usata *MageUI.exe*, è possibile aggiornare il manifesto di distribuzione aprendo il file, selezionare la **riferimento all'applicazione** scheda, fare clic sui **Seleziona manifesto** pulsante, e quindi selezionando il manifesto dell'applicazione aggiornata.

## <a name="see-also"></a>Vedere anche
- [Mage.exe (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [MageUI.exe (Strumento per la generazione e la modifica di manifesti, client grafico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Manifesto di distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)