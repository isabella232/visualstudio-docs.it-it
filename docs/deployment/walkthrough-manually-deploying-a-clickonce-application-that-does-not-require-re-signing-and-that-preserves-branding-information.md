---
title: "Procedura dettagliata: Distribuzione manuale di un'applicazione ClickOnce che non richiede la ripetizione della firma e conserva le informazioni sul marchio | Documenti Microsoft"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- branding
- preserved branding information
- ClickOnce deployment, manually
- multiple ClickOnce deployment and branding
- ClickOnce deployment, SDK tools
- customer deployments
- manual ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, deployed by others
ms.assetid: c21822fb-d4ee-42e4-b72d-41ee9786efe5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cb4838e44549f762e609913c92d677832d897edb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>Procedura dettagliata: distribuzione manuale di una applicazione ClickOnce che non richiede una nuova firma e conserva le informazioni di personalizzazione
Quando si crea un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione e quindi assegnarle a un cliente per pubblicare e distribuire, il cliente ha in genere era necessario aggiornare il manifesto di distribuzione e firmarlo di nuovo. Mentre è ancora il metodo preferito nella maggior parte dei casi, .NET Framework 3.5 consente di creare [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] le distribuzioni che possono essere distribuite dai clienti senza la necessità di rigenerare un nuovo manifesto di distribuzione. Per ulteriori informazioni, vedere [la distribuzione di applicazioni ClickOnce per test e i server di produzione senza Resigning](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md).  
  
 Quando si crea un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione e quindi assegnarle a un cliente per pubblicare e distribuire, l'applicazione può utilizzare informazioni di personalizzazione del cliente o conservare le proprie. Ad esempio, se l'applicazione è una singola applicazione proprietaria, potrebbe essere necessario mantenere la personalizzazione. Se l'applicazione è altamente personalizzato per ogni cliente, si desidera utilizzare informazioni di personalizzazione del cliente. .NET Framework 3.5 consente di conservare la personalizzazione, informazioni sull'editore e la firma di sicurezza quando si assegnata distribuire un'applicazione a un'organizzazione. Per altre informazioni, vedere [creazione di applicazioni ClickOnce per gli altri utenti alla pagina Distribuisci](../deployment/creating-clickonce-applications-for-others-to-deploy.md).  
  
> [!NOTE]
>  In questa procedura dettagliata è creare distribuzioni manualmente utilizzando lo strumento da riga di comando Mage.exe o lo strumento grafico MageUI.exe. Per ulteriori informazioni sulle distribuzioni manuale, vedere [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire i passaggi in questa procedura dettagliata è necessario quanto segue:  
  
-   Un'applicazione Windows Form che si è pronti per la distribuzione. Questa applicazione sanno considerati come WindowsFormsApp1.  
  
-   Visual Studio o Windows SDK.  
  
### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>Per distribuire un'applicazione ClickOnce con più distribuzioni e supporto della personalizzazione con Mage.exe  
  
1.  Aprire un prompt dei comandi di Visual Studio o un [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] prompt dei comandi e passare alla directory in cui verranno archiviati i [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] file.  
  
2.  Creare una directory denominata dopo la versione corrente della distribuzione. Se questa è la prima volta che si sta distribuendo l'applicazione, si sceglierà probabilmente **1.0.0.0**.  
  
    > [!NOTE]
    >  La versione della distribuzione potrebbe essere diverso dalla versione dei file dell'applicazione.  
  
3.  Creare una sottodirectory denominata **bin** e copiare tutti i file dell'applicazione in questo caso, inclusi file eseguibili, assembly, le risorse e i file di dati.  
  
4.  Generare il manifesto dell'applicazione con una chiamata a Mage.exe.  
  
    ```  
    mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"  
    ```  
  
5.  Firmare il manifesto dell'applicazione con il certificato digitale.  
  
    ```  
    mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx  
    ```  
  
6.  Generare il manifesto di distribuzione con una chiamata a Mage.exe. Per impostazione predefinita, Mage.exe contrassegnerà il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione come un'applicazione installata, in modo che non può essere eseguito sia online e offline. Per rendere l'applicazione disponibile solo quando l'utente è online, usare il `-i` argomento con un valore di `f`. Poiché questa applicazione sarà possibile avvalersi della funzionalità di distribuzione più, escludere il `-providerUrl` argomento Mage.exe. (Nelle versioni di .NET Framework precedenti alla versione 3.5, l'esclusione `-providerUrl` per un'applicazione offline verrà generato un errore.)  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest   
    ```  
  
7.  Non si firma il manifesto di distribuzione.  
  
8.  Fornire tutti i file per il cliente, che verrà distribuita l'applicazione nella propria rete.  
  
9. A questo punto, il cliente deve firmare il manifesto della distribuzione con il proprio certificato a generazione automatica. Ad esempio, se il cliente appropriato per una società denominata Adventure Works, può generare un certificato autofirmato utilizzando lo strumento MakeCert.exe. Successivamente, utilizzare lo strumento Pvk2pfx.exe per combinare i file creati da MakeCert.exe in un file PFX che può essere passato a Mage.exe.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
10. Successivamente, il cliente Usa questo certificato per firmare il manifesto di distribuzione.  
  
    ```  
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx  
    ```  
  
11. Il cliente distribuisce l'applicazione agli utenti.  
  
### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>Per distribuire un'applicazione ClickOnce con più distribuzioni e supporto della personalizzazione con MageUI.exe  
  
1.  Aprire un prompt dei comandi di Visual Studio o un [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] prompt dei comandi e passare alla directory in cui verranno archiviati i [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] file.  
  
2.  Creare una sottodirectory denominata **bin** e copiare tutti i file dell'applicazione in questo caso, inclusi file eseguibili, assembly, le risorse e i file di dati.  
  
3.  Creare una sottodirectory denominata dopo la versione corrente della distribuzione. Se questa è la prima volta che si sta distribuendo l'applicazione, si sceglierà probabilmente **1.0.0.0**.  
  
    > [!NOTE]
    >  La versione della distribuzione potrebbe essere diverso dalla versione dei file dell'applicazione.  
  
4.  Spostare il \\ **bin** directory nella directory creata nel passaggio 2.  
  
5.  Avviare lo strumento con interfaccia grafico MageUI.exe.  
  
    ```  
    MageUI.exe  
    ```  
  
6.  Creare un nuovo manifesto dell'applicazione selezionando **File**, **New**, **manifesto dell'applicazione** dal menu.  
  
7.  Nel valore predefinito **nome** , immettere il nome e numero di versione della distribuzione. Inoltre, fornire un valore per **Publisher**, che verrà utilizzato come nome della cartella per collegamento dell'applicazione nel menu Start quando viene distribuito.  
  
8.  Selezionare il **opzioni dell'applicazione** scheda e fare clic su **Usa manifesto applicazione per informazioni sull'attendibilità**. In questo modo la personalizzazione di terze parti per questo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione.  
  
9. Selezionare il **file** scheda e scegliere il **Sfoglia** pulsante accanto alla casella di testo di Directory dell'applicazione.  
  
10. Selezionare la directory che contiene i file dell'applicazione che è stato creato nel passaggio 2, quindi fare clic su **OK** nella finestra di dialogo di selezione cartelle.  
  
11. Fare clic su di **Popola** pulsante per aggiungere tutti i file dell'applicazione per l'elenco dei file. Se l'applicazione contiene più di un file eseguibile, contrassegnare il file eseguibile principale per la distribuzione dell'applicazione di avvio selezionando **punto di ingresso** dal **tipo di File** elenco a discesa. (Se l'applicazione contiene solo un file eseguibile, MageUI.exe contrassegnerà viene automaticamente.)  
  
12. Selezionare il **autorizzazioni necessarie** scheda e selezionare il livello di attendibilità è necessario l'applicazione per l'asserzione. Il valore predefinito è **attendibilità**, che sarà appropriata per la maggior parte delle applicazioni.  
  
13. Selezionare **File**, **salvare** dal menu di scelta, quindi salvare il manifesto dell'applicazione. Verrà richiesto per firmare il manifesto dell'applicazione quando si salva.  
  
14. Se si dispone di un certificato archiviato come file nel file system, utilizzare il **Sign come file di certificato** opzione e selezionare il certificato dal file system con i puntini di sospensione (**...** ) pulsante.  
  
     oppure  
  
     Se il certificato si trova in un archivio di certificati che è possibile accedere dal computer in uso, selezionare il **accesso con l'opzione certificato archiviato**e selezionare il certificato dall'elenco fornito.  
  
15. Selezionare **File**, **New**, **manifesto della distribuzione** dal menu per creare il manifesto della distribuzione, quindi nel **nome** scheda, fornire un nome e numero di versione (**1.0.0.0** in questo esempio).  
  
16. Passare il **aggiornare** scheda e specificare la frequenza con cui si desidera questa applicazione per l'aggiornamento. Se l'applicazione usa il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] API di distribuzione per cercare gli aggiornamenti, deselezionare la casella di controllo **questa applicazione trolla aggiornamenti**.  
  
17. Passare il **riferimento all'applicazione** scheda. È possibile pre-popolare tutti i valori in questa scheda, fare clic sui **Seleziona manifesto** pulsante e selezionando il manifesto dell'applicazione creato nei passaggi precedenti.  
  
18. Scegliere **salvare** e salvare il manifesto di distribuzione su disco. Verrà richiesto per firmare il manifesto dell'applicazione quando si salva. Fare clic su **annullare** per salvare il manifesto senza firma.  
  
19. Fornire tutti i file dell'applicazione al cliente.  
  
20. A questo punto, il cliente deve firmare il manifesto della distribuzione con il proprio certificato a generazione automatica. Ad esempio, se il cliente appropriato per una società denominata Adventure Works, può generare un certificato autofirmato utilizzando lo strumento MakeCert.exe. Successivamente, utilizzare lo strumento Pvk2pfx.exe per combinare i file creati da MakeCert.exe in un file PFX che può essere passato a MageUI.exe.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
21. Con il certificato generato, il cliente si disconnette ora il manifesto di distribuzione aprendo il manifesto di distribuzione in MageUI.exe e quindi a salvarlo. Quando viene visualizzata la finestra di dialogo firma, il cliente seleziona **Sign come file di certificato** opzione e sceglie il file PFX che ha salvato su disco.  
  
22. Il cliente distribuisce l'applicazione agli utenti.  
  
## <a name="next-steps"></a>Passaggi successivi  
  
## <a name="see-also"></a>Vedere anche  
 [Mage.exe (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (Manifest Generation and Editing Tool, client grafico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)   
 [MakeCert](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx)