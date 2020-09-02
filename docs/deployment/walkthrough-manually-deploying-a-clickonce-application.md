---
title: "Procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce | Microsoft Docs"
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
ms.openlocfilehash: 4aad87832a5bdae0d28d461d4cc289551eee7fee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "88249985"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application"></a>Procedura dettagliata: Distribuire manualmente un'applicazione ClickOnce
Se non è possibile usare Visual Studio per distribuire l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione oppure è necessario usare le funzionalità di distribuzione avanzate, ad esempio la distribuzione di applicazioni attendibili, è consigliabile usare lo strumento da riga di comando *Mage.exe* per creare i [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesti. In questa procedura dettagliata viene descritto come creare una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione utilizzando la versione della riga di comando (*Mage.exe*) o la versione grafica (*MageUI.exe*) del strumento per la generazione e la modifica di manifesti.

## <a name="prerequisites"></a>Prerequisiti
 Questa procedura dettagliata include alcuni prerequisiti e opzioni che è necessario scegliere prima di creare una distribuzione.

- Installare *Mage.exe* e *MageUI.exe*.

   *Mage.exe* e *MageUI.exe* sono parte di [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] . È necessario che sia [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] installato o la versione di [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] inclusa in Visual Studio. Per ulteriori informazioni, vedere [Windows SDK](https://www.microsoft.com/download/details.aspx?id=8279) su MSDN.

- Fornire un'applicazione da distribuire.

   In questa procedura dettagliata si presuppone che si disponga di un'applicazione Windows che si è pronti per la distribuzione. Questa applicazione verrà denominata AppToDeploy.

- Determinare il modo in cui verrà distribuita la distribuzione.

   Le opzioni di distribuzione includono: Web, condivisione file o CD. Per altre informazioni, vedere [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md).

- Determinare se l'applicazione richiede un livello di attendibilità elevato.

   Se l'applicazione richiede l'attendibilità totale, ad esempio l'accesso completo al sistema dell'utente, è possibile usare l' `-TrustLevel` opzione di *Mage.exe* per impostare questa impostazione. Se si desidera definire un set di autorizzazioni personalizzato per l'applicazione, è possibile copiare la sezione autorizzazione Internet o Intranet da un altro manifesto, modificarla in base alle proprie esigenze e aggiungerla al manifesto dell'applicazione utilizzando un editor di testo o *MageUI.exe*. Per ulteriori informazioni, vedere [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md).

- Ottenere un certificato Authenticode.

   È necessario firmare la distribuzione con un certificato Authenticode. È possibile generare un certificato di test tramite Visual Studio, *MageUI.exe*o *MakeCert.exe* e *Pvk2Pfx.exe* strumenti oppure è possibile ottenere un certificato da un'autorità di certificazione (CA). Se si sceglie di utilizzare la distribuzione di applicazioni attendibili, è necessario eseguire una sola installazione del certificato su tutti i computer client. Per ulteriori informazioni, vedere [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md).

  > [!NOTE]
  > È anche possibile firmare la distribuzione con un certificato CNG che è possibile ottenere da un'autorità di certificazione.

- Assicurarsi che l'applicazione non disponga di un manifesto con informazioni sul controllo dell'account utente.

   È necessario determinare se l'applicazione contiene un manifesto con informazioni sul controllo dell'account utente, ad esempio un `<dependentAssembly>` elemento. Per esaminare un manifesto dell'applicazione, è possibile usare l'utilità [sigcheck](/sysinternals/downloads/sigcheck) di Windows Sysinternals.

   Se l'applicazione contiene un manifesto con i dettagli dell'account utente, è necessario ricompilarlo senza le informazioni sul controllo dell'account utente. Per un progetto C# in Visual Studio, aprire le proprietà del progetto e selezionare la scheda applicazione. Nell'elenco a discesa **manifesto** selezionare **Crea applicazione senza un manifesto**. Per un progetto Visual Basic in Visual Studio, aprire le proprietà del progetto, selezionare la scheda applicazione e fare clic su **Visualizza impostazioni UAC**. Nel file manifesto aperto rimuovere tutti gli elementi all'interno del singolo `<asmv1:assembly>` elemento.

- Determinare se l'applicazione richiede prerequisiti nel computer client.

   [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] le applicazioni distribuite da Visual Studio possono includere un programma di avvio automatico dell'installazione dei prerequisiti (*setup.exe*) con la distribuzione. In questa procedura dettagliata vengono creati i due manifesti necessari per una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione. È possibile creare un programma di avvio automatico dei prerequisiti usando l' [attività GenerateBootstrapper](../msbuild/generatebootstrapper-task.md).

### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>Per distribuire un'applicazione con lo strumento da riga di comando Mage.exe

1. Creare una directory in cui archiviare i [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] file di distribuzione.

2. Nella directory di distribuzione appena creata creare una sottodirectory della versione. Se è la prima volta che si distribuisce l'applicazione, denominare la versione della sottodirectory **1.0.0.0**.

   > [!NOTE]
   > La versione della distribuzione può essere diversa dalla versione dell'applicazione.

3. Copiare tutti i file dell'applicazione nella sottodirectory della versione, inclusi i file eseguibili, gli assembly, le risorse e i file di dati. Se necessario, è possibile creare sottodirectory aggiuntive che contengono file aggiuntivi.

4. Aprire il [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] prompt dei comandi di o di Visual Studio e passare alla sottodirectory versione.

5. Creare il manifesto dell'applicazione con una chiamata a *Mage.exe*. L'istruzione seguente crea un manifesto dell'applicazione per il codice compilato per l'esecuzione nel processore Intel x86.

   ```cmd
   mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .
   ```

   > [!NOTE]
   > Assicurarsi di includere il punto (.) dopo l' `-FromDirectory` opzione, che indica la directory corrente. Se non si include il punto, è necessario specificare il percorso dei file dell'applicazione.

6. Firmare il manifesto dell'applicazione con il certificato Authenticode. Sostituire My *cert. pfx* con il percorso del file di certificato. Sostituire *passwd* con la password per il file del certificato.

   ```cmd
   mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd
   ```

   A partire da .NET Framework SDK 4.6.2, distribuito con Visual Studio e con il Windows SDK, *mage.exe* firma i manifesti con CNG, oltre che con i certificati Authenticode. Usare gli stessi parametri della riga di comando di con i certificati Authenticode.

7. Passare alla radice della directory di distribuzione.

8. Generare il manifesto di distribuzione con una chiamata a *Mage.exe*. Per impostazione predefinita, *Mage.exe* contrassegna la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione come applicazione installata, in modo che possa essere eseguita sia online che offline. Per rendere disponibile l'applicazione solo quando l'utente è online, utilizzare l' `-Install` opzione con un valore di `false` . Se si usa l'impostazione predefinita e gli utenti installeranno l'applicazione da un sito Web o da una condivisione file, assicurarsi che il valore dell' `-ProviderUrl` opzione punti al percorso del manifesto dell'applicazione nel server Web o nella condivisione.

   ```cmd
   mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application
   ```

9. Firmare il manifesto della distribuzione con il certificato Authenticode o CNG.

    ```cmd
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd
    ```

10. Copiare tutti i file nella directory di distribuzione nella destinazione o nel supporto di distribuzione. Può trattarsi di una cartella in un sito Web o in un sito FTP, una condivisione file o un CD-ROM.

11. Fornire agli utenti l'URL, l'UNC o i supporti fisici necessari per installare l'applicazione. Se si fornisce un URL o un UNC, è necessario assegnare agli utenti il percorso completo del manifesto di distribuzione. Se, ad esempio, AppToDeploy viene distribuito http://webserver01/ nella directory AppToDeploy, il percorso completo dell'URL sarà http://webserver01/AppToDeploy/AppToDeploy.application .

### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>Per distribuire un'applicazione con lo strumento grafico MageUI.exe

1. Creare una directory in cui archiviare i [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] file di distribuzione.

2. Nella directory di distribuzione appena creata creare una sottodirectory della versione. Se è la prima volta che si distribuisce l'applicazione, denominare la versione della sottodirectory **1.0.0.0**.

   > [!NOTE]
   > La versione della distribuzione è probabilmente diversa dalla versione dell'applicazione.

3. Copiare tutti i file dell'applicazione nella sottodirectory della versione, inclusi i file eseguibili, gli assembly, le risorse e i file di dati. Se necessario, è possibile creare sottodirectory aggiuntive che contengono file aggiuntivi.

4. Avviare lo strumento grafico *MageUI.exe* .

   ```cmd
   MageUI.exe
   ```

5. Creare un nuovo manifesto dell'applicazione selezionando **file**, **nuovo**, **manifesto dell'applicazione** dal menu.

6. Nella scheda **nome** predefinito digitare il nome e il numero di versione della distribuzione. Specificare anche il **processore** per cui viene compilata l'applicazione, ad esempio x86.

7. Selezionare la scheda **file** e quindi fare clic sul pulsante con i puntini di sospensione (**...**) accanto alla casella di testo **Directory applicazione** . Verrà visualizzata la finestra **di dialogo Sfoglia per cartelle** .

8. Selezionare la sottodirectory di versione contenente i file dell'applicazione e quindi fare clic su **OK**.

9. Se si intende eseguire la distribuzione da Internet Information Services (IIS), selezionare la casella di controllo **quando si popola aggiungere l'estensione. Deploy a qualsiasi file che non lo contiene** .

10. Passare al pulsante **popola** per aggiungere tutti i file dell'applicazione all'elenco file. Se l'applicazione contiene più file eseguibili, contrassegnare il file eseguibile principale per questa distribuzione come applicazione di avvio selezionando il **punto di ingresso** dall'elenco a discesa **tipo file** . Se l'applicazione contiene un solo file eseguibile, *MageUI.exe* lo contrassegnerà.

11. Selezionare la scheda **autorizzazioni necessarie** e selezionare il livello di attendibilità che l'applicazione deve dichiarare. Il valore predefinito è **FullTrust**, che sarà adatto per la maggior parte delle applicazioni.

12. Selezionare **file**, **Salva con nome** dal menu. Viene visualizzata una finestra di dialogo Opzioni di firma che richiede di firmare il manifesto dell'applicazione.

13. Se si dispone di un certificato archiviato come file nella file system, utilizzare l'opzione **firma con file di certificato** e selezionare il certificato dall'file System utilizzando il pulsante con i puntini di sospensione (**...**). Digitare quindi la password del certificato.

     -oppure-

     Se il certificato viene mantenuto in un archivio certificati accessibile dal computer, selezionare l'opzione **firma con certificato archiviato** e selezionare il certificato dall'elenco fornito.

14. Selezionare **OK** per firmare il manifesto dell'applicazione. Verrà visualizzata la finestra di dialogo **Salva con nome** .

15. Nella finestra di dialogo **Salva con nome** specificare la directory della versione e quindi selezionare **Salva**.

16. Selezionare **file**, **nuovo**, **manifesto distribuzione** dal menu per creare il manifesto della distribuzione.

17. Nella scheda **nome** specificare un nome e un numero di versione per questa distribuzione (**1.0.0.0** in questo esempio). Specificare anche il **processore** per cui viene compilata l'applicazione, ad esempio x86.

18. Selezionare la scheda **Descrizione** e specificare i valori per **autore** e **prodotto**. (**Product** è il nome assegnato all'applicazione dal menu Start di Windows quando l'applicazione viene installata in un computer client per l'utilizzo offline).

19. Selezionare la scheda **Opzioni di distribuzione** e nella casella di testo **percorso iniziale** specificare il percorso del manifesto dell'applicazione nel server Web o nella condivisione. Ad esempio, * \\ \myServer\myShare\AppToDeploy.Application*.

20. Se è stata aggiunta l'estensione *. deploy* in un passaggio precedente, selezionare anche **USA. distribuire l'estensione del nome file** qui.

21. Selezionare la scheda **Opzioni di aggiornamento** e specificare la frequenza con cui si desidera che l'applicazione venga aggiornata. Se l'applicazione usa <xref:System.Deployment.Application.UpdateCheckInfo> per verificare la disponibilità di aggiornamenti, deselezionare la casella di controllo **questa applicazione deve verificare la disponibilità di aggiornamenti** .

22. Selezionare la scheda **riferimento all'applicazione** , quindi passare al pulsante **Seleziona manifesto** . Verrà visualizzata una finestra di dialogo aperta.

23. Selezionare il manifesto dell'applicazione creato in precedenza e quindi selezionare **Apri**.

24. Selezionare **file**, **Salva con nome** dal menu. Viene visualizzata una finestra di dialogo **Opzioni di firma** che richiede di firmare il manifesto della distribuzione.

25. Se si dispone di un certificato archiviato come file nella file system, utilizzare l'opzione **firma con file di certificato** e selezionare il certificato dall'file System utilizzando il pulsante con i puntini di sospensione (**...**). Digitare quindi la password del certificato.

     -oppure-

     Se il certificato viene mantenuto in un archivio certificati accessibile dal computer, selezionare l'opzione **firma con certificato archiviato** e selezionare il certificato dall'elenco fornito.

26. Passare a **OK** per firmare il manifesto della distribuzione. Verrà visualizzata la finestra di dialogo **Salva con nome** .

27. Nella finestra di dialogo **Salva con nome** spostare verso l'alto di una directory nella radice della distribuzione, quindi selezionare **Salva**.

28. Copiare tutti i file nella directory di distribuzione nella destinazione o nel supporto di distribuzione. Può trattarsi di una cartella in un sito Web o in un sito FTP, una condivisione file o un CD-ROM.

29. Fornire agli utenti l'URL, l'UNC o i supporti fisici necessari per installare l'applicazione. Se si fornisce un URL o un UNC, è necessario assegnare agli utenti il percorso completo del manifesto di distribuzione. Se, ad esempio, AppToDeploy viene distribuito http://webserver01/ nella directory AppToDeploy, il percorso completo dell'URL sarà http://webserver01/AppToDeploy/AppToDeploy.application .

## <a name="next-steps"></a>Passaggi successivi
 Quando è necessario distribuire una nuova versione dell'applicazione, creare una nuova directory denominata dopo la nuova versione, ad esempio 1.0.0.1, e copiare i nuovi file dell'applicazione nella nuova directory. Successivamente, è necessario seguire i passaggi precedenti per creare e firmare un nuovo manifesto dell'applicazione e aggiornare e firmare il manifesto della distribuzione. Prestare attenzione a specificare la stessa versione più elevata sia nella *Mage.exe* `-New` che nelle `-Update` chiamate, perché [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Aggiorna solo versioni più elevate, con l'Integer più a sinistra più significativo. Se è stato usato *MageUI.exe*, è possibile aggiornare il manifesto di distribuzione aprendolo, selezionando la scheda **riferimento all'applicazione** , passare al pulsante **Seleziona manifesto** , quindi selezionare il manifesto dell'applicazione aggiornato.

## <a name="see-also"></a>Vedere anche
- [Mage.exe (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [MageUI.exe (Strumento per la generazione e la modifica di manifesti, client grafico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)
