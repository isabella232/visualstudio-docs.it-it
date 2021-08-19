---
title: Distribuire manualmente un'app ClickOnce app
description: Informazioni su come creare una ClickOnce distribuzione tramite la versione della riga di comando o la versione grafica del Strumento per la generazione e la modifica di manifesti.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 83bc3a73bede906f23dfc2b561bc3e2e3179af81
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122153771"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application"></a>Procedura dettagliata: Distribuire manualmente un'applicazione ClickOnce
Se non è possibile usare Visual Studio per distribuire l'applicazione o se è necessario usare funzionalità di distribuzione avanzate, ad esempio la distribuzione di applicazioni attendibili, è necessario usare lo strumento da riga di comando diMage.exeper creare i [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesti. Questa procedura dettagliata descrive come creare una distribuzione usando la versione della riga di comando (Mage.exe) o la versione grafica (MageUI.exe) del [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Strumento per la generazione e la modifica di manifesti.****

## <a name="prerequisites"></a>Prerequisiti
 Questa procedura dettagliata presenta alcuni prerequisiti e opzioni che è necessario scegliere prima di compilare una distribuzione.

- Installare *Mage.exe* e *MageUI.exe*.

   *Mage.exe* e *MageUI.exe* fanno parte di [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] . È necessario avere installato [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] o la versione di [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] inclusa in Visual Studio. Per altre informazioni, vedere [Windows SDK](https://www.microsoft.com/download/details.aspx?id=8279) su MSDN.

- Fornire un'applicazione da distribuire.

   Questa procedura dettagliata presuppone che l'utente Windows un'applicazione che si è pronti per la distribuzione. Questa applicazione verrà definita AppToDeploy.

- Determinare come verrà distribuita la distribuzione.

   Le opzioni di distribuzione includono: Web, condivisione file o CD. Per altre informazioni, vedere [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md).

- Determinare se l'applicazione richiede un livello di attendibilità elevato.

   Se l'applicazione richiede l'attendibilità totale, ad esempio l'accesso completo al sistema dell'utente, è possibile usare l'opzione diMage.exe`-TrustLevel` per impostare questa opzione.  Se si vuole definire un set di autorizzazioni personalizzato per l'applicazione, è possibile copiare la sezione delle autorizzazioni Internet o Intranet da un altro manifesto, modificarla in base alle proprie esigenze e aggiungerla al manifesto dell'applicazione usando un editor di testo o *MageUI.exe*. Per altre informazioni, vedere [Panoramica della distribuzione di applicazioni attendibili.](../deployment/trusted-application-deployment-overview.md)

- Ottenere un certificato Authenticode.

   È consigliabile firmare la distribuzione con un certificato Authenticode. È possibile generare un certificato di test usando gli strumenti Visual Studio, *MageUI.exe* o *MakeCert.exe* *ePvk2Pfx.exe* oppure è possibile ottenere un certificato da un'autorità di certificazione (CA). Se si sceglie di usare la distribuzione di applicazioni attendibili, è necessario eseguire anche un'installazione una sola volta del certificato in tutti i computer client. Per altre informazioni, vedere [Cenni preliminari sulla distribuzione di applicazioni attendibili.](../deployment/trusted-application-deployment-overview.md)

  > [!NOTE]
  > È anche possibile firmare la distribuzione con un certificato CNG che è possibile ottenere da un'autorità di certificazione.

- Assicurarsi che l'applicazione non abbia un manifesto con informazioni di Controllo dell'account utente.

   È necessario determinare se l'applicazione contiene un manifesto con informazioni sul controllo dell'account utente, ad esempio un `<dependentAssembly>` elemento . Per esaminare un manifesto dell'applicazione, è possibile usare l'Windows Sysinternals [Sigcheck.](/sysinternals/downloads/sigcheck)

   Se l'applicazione contiene un manifesto con i dettagli di Controllo dell'account utente, è necessario compilarlo nuovamente senza le informazioni sul controllo dell'account utente. Per un progetto C# in Visual Studio, aprire le proprietà del progetto e selezionare la scheda Applicazione. **Nell'elenco** a discesa Manifesto selezionare **Crea applicazione senza un manifesto.** Per un progetto Visual Basic in Visual Studio, aprire le proprietà del progetto, selezionare la scheda Applicazione e fare clic su Visualizza controllo dell'account utente **Impostazioni**. Nel file manifesto aperto rimuovere tutti gli elementi all'interno del singolo `<asmv1:assembly>` elemento.

- Determinare se l'applicazione richiede prerequisiti nel computer client.

   [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Le applicazioni distribuite da Visual Studio possono includere un programma di avvio automatico per l'installazione dei prerequisiti (*setup.exe*) con la distribuzione. Questa procedura dettagliata crea i due manifesti necessari per una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione. È possibile creare un programma di avvio automatico dei prerequisiti usando [l'attività GenerateBootstrapper](../msbuild/generatebootstrapper-task.md).

### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>Per distribuire un'applicazione con lo Mage.exe da riga di comando

1. Creare una directory in cui archiviare i file [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] di distribuzione.

2. Nella directory di distribuzione appena creata creare una sottodirectory della versione. Se è la prima volta che si distribuisce l'applicazione, assegnare alla sottodirectory della versione il nome **1.0.0.0.**

   > [!NOTE]
   > La versione della distribuzione può essere diversa dalla versione dell'applicazione.

3. Copiare tutti i file dell'applicazione nella sottodirectory della versione, inclusi file eseguibili, assembly, risorse e file di dati. Se necessario, è possibile creare sottodirectory aggiuntive che contengono file aggiuntivi.

4. Aprire il [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] prompt Visual Studio prompt dei comandi e passare alla sottodirectory version.

5. Creare il manifesto dell'applicazione con una *chiamata aMage.exe*. L'istruzione seguente crea un manifesto dell'applicazione per il codice compilato per l'esecuzione nel processore Intel x86.

   ```cmd
   mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .
   ```

   > [!NOTE]
   > Assicurarsi di includere il punto (.) dopo `-FromDirectory` l'opzione , che indica la directory corrente. Se non si include il punto, è necessario specificare il percorso dei file dell'applicazione.

6. Firmare il manifesto dell'applicazione con il certificato Authenticode. Sostituire *mycert.pfx* con il percorso del file del certificato. Sostituire *passwd con* la password per il file del certificato.

   ```cmd
   mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd
   ```

   A partire da .NET Framework 4.6.2 SDK, distribuito con Visual Studio e con Windows SDK, *mage.exe* firma i manifesti con CNG e con certificati Authenticode. Usare gli stessi parametri della riga di comando dei certificati Authenticode.

7. Passare alla radice della directory di distribuzione.

8. Generare il manifesto della distribuzione con una chiamata a *Mage.exe*. Per impostazione predefinita, *Mage.exe* contrassegnerà la distribuzione come applicazione installata, in modo che possa [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] essere eseguita sia online che offline. Per rendere disponibile l'applicazione solo quando l'utente è online, usare `-Install` l'opzione con il valore `false` . Se si usa l'impostazione predefinita e gli utenti installeranno l'applicazione da un sito Web o da una condivisione file, assicurarsi che il valore dell'opzione punti al percorso del manifesto dell'applicazione nel server Web o nella `-ProviderUrl` condivisione.

   ```cmd
   mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application
   ```

9. Firmare il manifesto della distribuzione con il certificato Authenticode o CNG.

    ```cmd
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd
    ```

10. Copiare tutti i file nella directory di distribuzione nel supporto o nella destinazione della distribuzione. Può trattarsi di una cartella in un sito Web o FTP, una condivisione file o un CD-ROM.

11. Fornire agli utenti l'URL, il supporto UNC o fisico necessario per installare l'applicazione. Se si specifica un URL o un UNC, è necessario fornire agli utenti il percorso completo del manifesto della distribuzione. Ad esempio, se AppToDeploy viene distribuito http://webserver01/ in nella directory AppToDeploy, il percorso URL completo sarà http://webserver01/AppToDeploy/AppToDeploy.application .

### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>Per distribuire un'applicazione con lo MageUI.exe grafico

1. Creare una directory in cui archiviare i file [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] di distribuzione.

2. Nella directory di distribuzione appena creata creare una sottodirectory della versione. Se è la prima volta che si distribuisce l'applicazione, assegnare alla sottodirectory della versione il nome **1.0.0.0.**

   > [!NOTE]
   > La versione della distribuzione è probabilmente diversa dalla versione dell'applicazione.

3. Copiare tutti i file dell'applicazione nella sottodirectory della versione, inclusi file eseguibili, assembly, risorse e file di dati. Se necessario, è possibile creare sottodirectory aggiuntive che contengono file aggiuntivi.

4. Avviare lo *strumentoMageUI.exe* grafico.

   ```cmd
   MageUI.exe
   ```

5. Creare un nuovo manifesto dell'applicazione selezionando **File**, **Nuovo**, **Manifesto dell'applicazione** dal menu.

6. Nella scheda **Nome predefinita** digitare il nome e il numero di versione della distribuzione. Specificare anche il **processore** per cui è compilata l'applicazione, ad esempio x86.

7. Selezionare la **scheda File** e quindi selezionare il pulsante con i puntini di sospensione (**...**) accanto alla casella di **testo Directory** applicazione. Verrà **visualizzata la finestra di dialogo** Cerca cartella .

8. Selezionare la sottodirectory della versione contenente i file dell'applicazione e quindi selezionare **OK.**

9. Se si esegue la distribuzione da Internet Information Services (IIS), selezionare la casella di controllo Durante il popolamento aggiungere l'estensione deploy a qualsiasi **file** in cui non è presente.

10. Passare al pulsante **Popola per** aggiungere tutti i file dell'applicazione all'elenco di file. Se l'applicazione contiene più file eseguibili, contrassegnare il file eseguibile principale per questa distribuzione come applicazione di avvio selezionando Punto di ingresso dall'elenco a discesa **Tipo** di file.  Se l'applicazione contiene un solo file eseguibile, *MageUI.exe* lo contrassegnerà per l'utente.

11. Selezionare la **scheda Autorizzazioni necessarie** e selezionare il livello di attendibilità necessario per l'asserzione da parte dell'applicazione. Il valore predefinito **è FullTrust,** che sarà adatto per la maggior parte delle applicazioni.

12. Selezionare **File**, **Salva con nome** dal menu. Verrà visualizzata la finestra di dialogo Opzioni di firma in cui viene richiesto di firmare il manifesto dell'applicazione.

13. Se nel file system è archiviato un certificato come file, usare l'opzione Firma con **file** di certificato e selezionare il certificato dal file system usando i puntini di sospensione (**...**) . Digitare quindi la password del certificato.

     -oppure-

     Se il certificato viene mantenuto in un archivio  certificati accessibile dal computer, selezionare l'opzione Firma con certificato archiviato e selezionare il certificato nell'elenco fornito.

14. Selezionare **OK per** firmare il manifesto dell'applicazione. Verrà visualizzata la finestra di dialogo **Salva con nome** .

15. Nella finestra **di dialogo Salva** con nome specificare la directory della versione e quindi selezionare **Salva**.

16. Selezionare **File**, **Nuovo**, **Manifesto della** distribuzione dal menu per creare il manifesto della distribuzione.

17. Nella scheda **Nome** specificare un nome e un numero di versione per questa distribuzione (**1.0.0.0** in questo esempio). Specificare anche il **processore** per cui è compilata l'applicazione, ad esempio x86.

18. Selezionare la **scheda Descrizione** e specificare i valori per **Publisher** e **Product**. Il **prodotto** è il nome assegnato all'applicazione nel Windows menu Start quando l'applicazione viene installata in un computer client per l'uso offline.

19. Selezionare la **scheda Opzioni di** distribuzione e nella casella di testo **Percorso** iniziale specificare il percorso del manifesto dell'applicazione nel server Web o nella condivisione. Ad esempio, *\\ \myServer\myShare\AppToDeploy.application*.

20. Se è stata aggiunta *l'estensione .deploy* in un passaggio precedente, selezionare anche Usa estensione di **file con estensione deploy** qui.

21. Selezionare la **scheda Opzioni di** aggiornamento e specificare la frequenza di aggiornamento dell'applicazione. Se l'applicazione usa per verificare la presenza di aggiornamenti, deselezionare la casella di controllo Questa <xref:System.Deployment.Application.UpdateCheckInfo> applicazione deve controllare **la** disponibilità di aggiornamenti.

22. Selezionare la **scheda Riferimento applicazione** e quindi passare al pulsante **Seleziona** manifesto. Verrà visualizzata una finestra di dialogo aperta.

23. Selezionare il manifesto dell'applicazione creato in precedenza e quindi **selezionare Apri**.

24. Selezionare **File**, **Salva con nome** dal menu. Verrà **visualizzata la finestra** di dialogo Opzioni di firma che richiede di firmare il manifesto della distribuzione.

25. Se si dispone di un certificato archiviato come file nel file system, usare l'opzione Firma con **file** di certificato e selezionare il certificato dal file system usando i puntini di sospensione (**...**) pulsante. Digitare quindi la password del certificato.

     -oppure-

     Se il certificato viene mantenuto in un archivio  certificati accessibile dal computer, selezionare l'opzione Firma con certificato archiviato e selezionare il certificato nell'elenco fornito.

26. Passare a **OK per** firmare il manifesto della distribuzione. Verrà visualizzata la finestra di dialogo **Salva con nome** .

27. Nella finestra **di dialogo Salva** con nome spostare di una directory verso l'alto nella radice della distribuzione e quindi selezionare **Salva**.

28. Copiare tutti i file nella directory di distribuzione nella destinazione o nel supporto di distribuzione. Può trattarsi di una cartella in un sito Web o FTP, una condivisione file o un CD-ROM.

29. Fornire agli utenti l'URL, il supporto UNC o fisico necessario per installare l'applicazione. Se si specifica un URL o un UNC, è necessario assegnare agli utenti il percorso completo del manifesto della distribuzione. Ad esempio, se AppToDeploy viene distribuito http://webserver01/ in nella directory AppToDeploy, il percorso URL completo sarà http://webserver01/AppToDeploy/AppToDeploy.application .

## <a name="next-steps"></a>Passaggi successivi
 Quando è necessario distribuire una nuova versione dell'applicazione, creare una nuova directory denominata in base alla nuova versione, ad esempio 1.0.0.1, e copiare i nuovi file dell'applicazione nella nuova directory. Successivamente, è necessario seguire i passaggi precedenti per creare e firmare un nuovo manifesto dell'applicazione e aggiornare e firmare il manifesto della distribuzione. Prestare attenzione a specificare la stessa  versione superiore sia nelMage.exeche nelle chiamate, poiché aggiorna solo le versioni più recenti, con il numero intero più a `-New` sinistra più `-Update` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] significativo. Se è statoMageUI.exe, è possibile aggiornare il manifesto  della distribuzione aprendolo,  selezionando la scheda Riferimento applicazione , passare al pulsante *Seleziona* manifesto e quindi selezionare il manifesto dell'applicazione aggiornato.

## <a name="see-also"></a>Vedi anche
- [Mage.exe (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [MageUI.exe (Strumento per la generazione e la modifica di manifesti, client grafico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [ClickOnce manifesto della distribuzione](../deployment/clickonce-deployment-manifest.md)
- [ClickOnce manifesto dell'applicazione](../deployment/clickonce-application-manifest.md)
