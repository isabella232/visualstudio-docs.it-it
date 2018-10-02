---
title: "Procedura dettagliata: Distribuzione manuale di un'applicazione ClickOnce che non richiede una nuova firma e conserva le informazioni di personalizzazione | Microsoft Docs"
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 85453b899501d83191016bde0edd40b4e2a96d94
ms.sourcegitcommit: d705e015cb525bfa87a0b93e93376c3956ec2707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/29/2018
ms.locfileid: "47590496"
---
# <a name="walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>Procedura dettagliata: distribuzione manuale di una applicazione ClickOnce che non richiede una nuova firma e conserva le informazioni di personalizzazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce che non richiede la ripetizione della firma e mantiene informazioni di personalizzazione](https://docs.microsoft.com/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information).  
  
Quando si crea un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dell'applicazione e quindi passarla a un cliente per pubblicare e distribuire, il cliente ha in genere aggiornare il manifesto di distribuzione e firmare nuovamente la soluzione. Sebbene questo rappresenti il metodo consigliato nella maggior parte dei casi, .NET Framework 3.5 consente di creare [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] le distribuzioni che possono essere distribuite dai clienti senza la necessità di rigenerare un nuovo manifesto di distribuzione. Per altre informazioni, vedere [distribuzione di applicazioni ClickOnce per test e i server di produzione senza Resigning](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md).  
  
 Quando si crea un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dell'applicazione e quindi passarla a un cliente per pubblicare e distribuire, l'applicazione può usare la personalizzazione del cliente o conservare le proprie. Ad esempio, se l'applicazione è una singola applicazione proprietaria, si potrebbe essere necessario mantenere la personalizzazione. Se l'applicazione è altamente personalizzata per ogni cliente, si potrebbe voler usare la personalizzazione del cliente. .NET Framework 3.5 consente di conservare la personalizzazione, informazioni sull'editore e la firma di sicurezza quando si concede un'applicazione a un'organizzazione per la distribuzione. Per altre informazioni, vedere [creazione di applicazioni ClickOnce per altri utenti su Distribuisci](../deployment/creating-clickonce-applications-for-others-to-deploy.md).  
  
> [!NOTE]
>  In questa procedura dettagliata si creare distribuzioni manualmente usando lo strumento da riga di comando Mage.exe o lo strumento grafico MageUI.exe. Per altre informazioni sulle distribuzioni manuali, vedere [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire i passaggi in questa procedura dettagliata è necessario quanto segue:  
  
-   Un'applicazione Windows Forms che si è pronti per la distribuzione. Questa applicazione verrà indicata al WindowsFormsApp1.  
  
-   Visual Studio o il Windows SDK.  
  
### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>Per distribuire un'applicazione ClickOnce con più distribuzioni e supporto della personalizzazione tramite Mage.exe  
  
1.  Aprire un prompt dei comandi di Visual Studio o un [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] prompt dei comandi e passare alla directory in cui verranno archiviati i [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] file.  
  
2.  Creare una directory denominata alla versione corrente della distribuzione. Se questa è la prima volta che si sta distribuendo l'applicazione, si sceglierà probabilmente **1.0.0.0**.  
  
    > [!NOTE]
    >  La versione della distribuzione può essere diverso dalla versione dei file dell'applicazione.  
  
3.  Creare una sottodirectory denominata **bin** e copiare tutti i file dell'applicazione in questo caso, inclusi file eseguibili, gli assembly, le risorse e i file di dati.  
  
4.  Generare il manifesto dell'applicazione con una chiamata a Mage.exe.  
  
    ```  
    mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"  
    ```  
  
5.  Firmare il manifesto dell'applicazione con il proprio certificato digitale.  
  
    ```  
    mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx  
    ```  
  
6.  Generare il manifesto di distribuzione con una chiamata a Mage.exe. Per impostazione predefinita, si contrassegnerà Mage.exe il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] distribuzione come un'applicazione installata, in modo che non può essere eseguito sia online e offline. Per rendere l'applicazione disponibile solo quando l'utente è online, usare il `-i` argomento con un valore di `f`. Poiché questa applicazione sfrutterà la più funzionalità di distribuzione, escludere il `-providerUrl` argomento Mage.exe. (Nelle versioni di .NET Framework precedenti alla versione 3.5, l'esclusione `-providerUrl` per un'applicazione non in linea causerà un errore.)  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest   
    ```  
  
7.  Non firmare il manifesto di distribuzione.  
  
8.  Fornire tutti i file al cliente, che verrà distribuita l'applicazione nella propria rete.  
  
9. A questo punto, il cliente deve firmare il manifesto di distribuzione con il proprio certificato a generazione automatica. Ad esempio, se il cliente appropriato per una società denominata Adventure Works, può generare un certificato autofirmato utilizzando lo strumento MakeCert.exe. Successivamente, utilizzare lo strumento Pvk2pfx.exe per combinare i file creati da MakeCert.exe in un file PFX che può essere passato a Mage.exe.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
10. Il cliente Usa quindi questo certificato per firmare il manifesto di distribuzione.  
  
    ```  
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx  
    ```  
  
11. Il cliente distribuisce l'applicazione agli utenti.  
  
### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>Per distribuire un'applicazione ClickOnce con più distribuzioni e supporto della personalizzazione tramite MageUI.exe  
  
1.  Aprire un prompt dei comandi di Visual Studio o un [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] prompt dei comandi e passare alla directory in cui verranno archiviati i [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] file.  
  
2.  Creare una sottodirectory denominata **bin** e copiare tutti i file dell'applicazione in questo caso, inclusi file eseguibili, gli assembly, le risorse e i file di dati.  
  
3.  Creare una sottodirectory denominata in base alla versione corrente della distribuzione. Se questa è la prima volta che si sta distribuendo l'applicazione, si sceglierà probabilmente **1.0.0.0**.  
  
    > [!NOTE]
    >  La versione della distribuzione può essere diverso dalla versione dei file dell'applicazione.  
  
4.  Spostare il \\ **bin** directory nella directory creata nel passaggio 2.  
  
5.  Avviare lo strumento con interfaccia grafico MageUI.exe.  
  
    ```  
    MageUI.exe  
    ```  
  
6.  Creare un nuovo manifesto dell'applicazione selezionando **File**, **New**, **Application Manifest** dal menu di scelta.  
  
7.  Nel valore predefinito **nome** , immettere il nome e numero di versione di questa distribuzione. Inoltre, fornire un valore per **server di pubblicazione**, che verrà usato come nome della cartella per il collegamento di scelta rapida dell'applicazione nel menu Start quando viene distribuita.  
  
8.  Selezionare il **Opzioni applicazione** scheda e fare clic su **Usa manifesto applicazione per informazioni sull'attendibilità**. Ciò consentirà di terze parti della personalizzazione per questo [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dell'applicazione.  
  
9. Selezionare il **file** scheda e fare clic sui **Sfoglia** pulsante accanto alla casella di testo di Directory dell'applicazione.  
  
10. Selezionare la directory che contiene i file dell'applicazione che è stato creato nel passaggio 2, quindi fare clic su **OK** nella finestra di dialogo Selezione cartella.  
  
11. Scegliere il **Popola** pulsante per aggiungere tutti i file dell'applicazione per l'elenco dei file. Se l'applicazione contiene più di un file eseguibile, contrassegnare il file eseguibile principale per la distribuzione dell'applicazione di avvio selezionando **punto di ingresso** dalle **tipo di File** elenco a discesa. (Se l'applicazione contiene solo un file eseguibile, MageUI.exe verrà contrassegnarla per l'utente.)  
  
12. Selezionare il **autorizzazioni necessarie** scheda e selezionare il livello di attendibilità è necessaria l'applicazione per l'asserzione. Il valore predefinito è **attendibilità**, che sarà appropriato per la maggior parte delle applicazioni.  
  
13. Selezionare **File**, **salvare** dal menu, quindi salvare il manifesto dell'applicazione. Verrà richiesto per firmare il manifesto dell'applicazione durante il salvataggio.  
  
14. Se si dispone di un certificato archiviato come file nel file system, usare il **Sign come file di certificato** opzione e selezionare il certificato dal file system con i puntini di sospensione (**...** ) pulsante.  
  
     oppure  
  
     Se il certificato si trova in un archivio di certificati che sono accessibili dal computer, selezionare la **segno con l'opzione certificati archiviati**e selezionare il certificato dall'elenco fornito.  
  
15. Selezionare **File**, **New**, **manifesto della distribuzione** dal menu per creare il manifesto di distribuzione e quindi nel **nome** scheda, fornire un nome e numero di versione (**1.0.0.0** in questo esempio).  
  
16. Passare al **aggiornare** scheda e specificare la frequenza con cui si desidera questo aggiornamento dell'applicazione. Se l'applicazione usa la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] API di distribuzione per verificare la presenza di aggiornamenti, deselezionare la casella di controllo etichettata **l'applicazione deve controllare disponibilità di aggiornamenti**.  
  
17. Passare al **riferimento all'applicazione** scheda. È possibile popolare anticipatamente tutti i valori in questa scheda, fare clic il **Seleziona manifesto** pulsante e selezionando il manifesto dell'applicazione creata nei passaggi precedenti.  
  
18. Scegli **salvare** e salvare il manifesto di distribuzione su disco. Verrà richiesto per firmare il manifesto dell'applicazione durante il salvataggio. Fare clic su **annullare** per salvare il manifesto senza firmarla.  
  
19. Tutti i file dell'applicazione di fornire al cliente.  
  
20. A questo punto, il cliente deve firmare il manifesto di distribuzione con il proprio certificato a generazione automatica. Ad esempio, se il cliente appropriato per una società denominata Adventure Works, può generare un certificato autofirmato utilizzando lo strumento MakeCert.exe. Successivamente, utilizzare lo strumento Pvk2pfx.exe per combinare i file creati da MakeCert.exe in un file PFX che può essere passato a MageUI.exe.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
21. Con il certificato generato, il cliente accede a questo punto il manifesto di distribuzione aprendo il manifesto di distribuzione MageUI.exe e quindi salvarla. Quando viene visualizzata la finestra di dialogo firma, il cliente seleziona **Sign come file di certificato** opzione e sceglie il file PFX che ha salvato su disco.  
  
22. Il cliente distribuisce l'applicazione agli utenti.  
  
## <a name="next-steps"></a>Passaggi successivi  
  
## <a name="see-also"></a>Vedere anche  
 [Mage.exe (Strumento per la generazione e la modifica di manifesti)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (Manifest Generation and Editing Tool, client grafico)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)   
 [Makecert.exe (Certificate Creation Tool)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) (Makecert.exe, strumento di creazione certificati)



