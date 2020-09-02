---
title: Distribuire manualmente le app ClickOnce che conservano la personalizzazione
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47db202d07fd88bfb5e922964caf2cdd5008c6fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "66263418"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>Procedura dettagliata: distribuire manualmente un'applicazione ClickOnce che non richiede una nuova firma e che conserva le informazioni di personalizzazione
Quando si crea un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione e la si assegna a un cliente per la pubblicazione e la distribuzione, il cliente ha tradizionalmente dovuto aggiornare il manifesto di distribuzione e firmarlo di nuovo. Sebbene questo sia ancora il metodo preferito nella maggior parte dei casi, il .NET Framework 3,5 consente di creare [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzioni che possono essere distribuite dai clienti senza dover rigenerare un nuovo manifesto di distribuzione. Per ulteriori informazioni, vedere la pagina relativa alla [distribuzione di applicazioni ClickOnce per i server di test e di produzione senza firma](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md).

 Quando si crea un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione e la si assegna a un cliente per la pubblicazione e la distribuzione, l'applicazione può usare la personalizzazione del cliente o può mantenere la personalizzazione. Ad esempio, se l'applicazione è un'unica applicazione proprietaria, potrebbe essere necessario mantenere la personalizzazione. Se l'applicazione è altamente personalizzata per ogni cliente, è consigliabile utilizzare la personalizzazione del cliente. Il .NET Framework 3,5 consente di mantenere le informazioni di personalizzazione, di pubblicazione e di sicurezza quando si assegna un'applicazione a un'organizzazione per la distribuzione. Per ulteriori informazioni, vedere [la pagina relativa alla creazione di applicazioni ClickOnce per la distribuzione da altri utenti](../deployment/creating-clickonce-applications-for-others-to-deploy.md).

> [!NOTE]
> In questa procedura dettagliata le distribuzioni vengono create manualmente tramite lo strumento da riga di comando *Mage.exe* o lo strumento grafico *MageUI.exe*. Per ulteriori informazioni sulle distribuzioni manuali, vedere [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="prerequisites"></a>Prerequisiti
 Per eseguire la procedura descritta in questa procedura dettagliata, è necessario quanto segue:

- Windows Forms Application che si è pronti per la distribuzione. Questa applicazione verrà denominata *WindowsFormsApp1*.

- Visual Studio o il Windows SDK.

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>Per distribuire un'applicazione ClickOnce con più distribuzioni e supporto di personalizzazione usando Mage.exe

1. Aprire un prompt dei comandi di Visual Studio o un [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] prompt dei comandi e passare alla directory in cui vengono archiviati i [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] file.

2. Creare una directory denominata dopo la versione corrente della distribuzione. Se è la prima volta che si distribuisce l'applicazione, è probabile che si scelga **1.0.0.0**.

   > [!NOTE]
   > La versione della distribuzione può essere diversa dalla versione dei file dell'applicazione.

3. Creare una sottodirectory denominata **bin** e copiare qui tutti i file dell'applicazione, inclusi i file eseguibili, gli assembly, le risorse e i file di dati.

4. Generare il manifesto dell'applicazione con una chiamata a Mage.exe.

   ```cmd
   mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"
   ```

5. Firmare il manifesto dell'applicazione con il certificato digitale.

   ```cmd
   mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx
   ```

6. Generare il manifesto di distribuzione con una chiamata a *Mage.exe*. Per impostazione predefinita, *Mage.exe* contrassegna la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione come applicazione installata, in modo che possa essere eseguita sia online che offline. Per rendere disponibile l'applicazione solo quando l'utente è online, utilizzare l' `-i` argomento con un valore di `f` . Poiché questa applicazione sfrutta la funzionalità di distribuzione multipla, escludere l' `-providerUrl` argomento per *Mage.exe*. Nelle versioni del .NET Framework precedenti alla versione 3,5, escludendo `-providerUrl` per un'applicazione offline, verrà generato un errore.

   ```cmd
   mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest
   ```

7. Non firmare il manifesto della distribuzione.

8. Fornire tutti i file al cliente, che distribuirà l'applicazione nella rete.

9. A questo punto, il cliente deve firmare il manifesto della distribuzione con il proprio certificato generato automaticamente. Se, ad esempio, il cliente lavora per una società denominata Adventure Works, può generare un certificato autofirmato usando lo strumento *MakeCert.exe* . Usare quindi lo strumento *Pvk2pfx.exe* per combinare i file creati da *MakeCert.exe* in un file PFX che può essere passato al *Mage.exe*.

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

10. Il cliente usa quindi questo certificato per firmare il manifesto di distribuzione.

    ```cmd
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx
    ```

11. Il cliente distribuisce l'applicazione agli utenti.

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>Per distribuire un'applicazione ClickOnce con più distribuzioni e supporto di personalizzazione usando MageUI.exe

1. Aprire un prompt dei comandi di Visual Studio o un [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] prompt dei comandi e passare alla directory in cui vengono archiviati i [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] file.

2. Creare una sottodirectory denominata **bin** e copiare qui tutti i file dell'applicazione, inclusi i file eseguibili, gli assembly, le risorse e i file di dati.

3. Creare una sottodirectory denominata dopo la versione corrente della distribuzione. Se è la prima volta che si distribuisce l'applicazione, è probabile che si scelga **1.0.0.0**.

   > [!NOTE]
   > La versione della distribuzione può essere diversa dalla versione dei file dell'applicazione.

4. Spostare la \\ directory **bin** nella directory creata nel passaggio 2.

5. Avviare lo strumento grafico *MageUI.exe*.

   ```cmd
   MageUI.exe
   ```

6. Creare un nuovo manifesto dell'applicazione selezionando **file**, **nuovo**, **manifesto dell'applicazione** dal menu.

7. Nella scheda **nome** predefinito immettere il nome e il numero di versione della distribuzione. Specificare anche un valore per **Publisher**, che verrà usato come nome della cartella per il collegamento di collegamento dell'applicazione nel menu Start quando viene distribuito.

8. Selezionare la scheda **Opzioni applicazione** e fare clic su **Usa manifesto applicazione per informazioni sull'attendibilità**. In questo modo verrà abilitata la personalizzazione di terze parti per questa [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione.

9. Selezionare la scheda **file** e fare clic sul pulsante **Sfoglia** accanto alla casella di testo **Directory applicazione** .

10. Selezionare la directory che contiene i file dell'applicazione creati nel passaggio 2, quindi fare clic su **OK** nella finestra di dialogo Selezione cartella.

11. Fare clic sul pulsante **popola** per aggiungere tutti i file dell'applicazione all'elenco file. Se l'applicazione contiene più file eseguibili, contrassegnare il file eseguibile principale per questa distribuzione come applicazione di avvio selezionando il **punto di ingresso** dall'elenco a discesa **tipo file** . Se l'applicazione contiene un solo file eseguibile, *MageUI.exe* lo contrassegnerà.

12. Selezionare la scheda **autorizzazioni necessarie** e selezionare il livello di attendibilità che l'applicazione deve dichiarare. Il valore predefinito è **attendibilità totale**, che sarà appropriato per la maggior parte delle applicazioni.

13. Selezionare **file**, **Salva** dal menu e salvare il manifesto dell'applicazione. Verrà richiesto di firmare il manifesto dell'applicazione al momento del salvataggio.

14. Se si dispone di un certificato archiviato come file nella file system, utilizzare l'opzione per il **file del certificato di firma** e selezionare il certificato dall'file System utilizzando il pulsante con i puntini di sospensione (**...**).

     -oppure-

     Se il certificato viene mantenuto in un archivio certificati a cui è possibile accedere dal computer, selezionare l' **opzione firma con certificato archiviato**e selezionare il certificato dall'elenco fornito.

15. Selezionare **file**, **nuovo**, **manifesto distribuzione** dal menu per creare il manifesto di distribuzione e quindi nella scheda **nome** specificare un nome e un numero di versione (**1.0.0.0** in questo esempio).

16. Passare alla scheda **aggiornamento** e specificare la frequenza con cui si vuole aggiornare l'applicazione. Se l'applicazione usa l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] API di distribuzione per verificare la disponibilità di aggiornamenti, deselezionare la casella di controllo con l'etichetta **questa applicazione deve verificare la disponibilità di aggiornamenti**.

17. Passare alla scheda **riferimento all'applicazione** . È possibile pre-popolare tutti i valori in questa scheda facendo clic sul pulsante **Seleziona manifesto** e selezionando il manifesto dell'applicazione creato nei passaggi precedenti.

18. Scegliere **Salva** e salvare il manifesto di distribuzione su disco. Verrà richiesto di firmare il manifesto dell'applicazione al momento del salvataggio. Fare clic su **Annulla** per salvare il manifesto senza firma.

19. Fornire tutti i file dell'applicazione al cliente.

20. A questo punto, il cliente deve firmare il manifesto della distribuzione con il proprio certificato generato automaticamente. Se, ad esempio, il cliente lavora per una società denominata Adventure Works, può generare un certificato autofirmato usando lo strumento *MakeCert.exe* . Usare quindi lo strumento *Pvk2pfx.exe* per combinare i file creati da *MakeCert.exe* in un file PFX che può essere passato al *MageUI.exe*.

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

21. Con il certificato generato, il cliente ora firma il manifesto di distribuzione aprendo il manifesto di distribuzione in *MageUI.exe*e quindi salvarlo. Quando viene visualizzata la finestra di dialogo firma, il cliente seleziona l'opzione **per il file del certificato di firma** e sceglie il file PFX salvato su disco.

22. Il cliente distribuisce l'applicazione agli utenti.

## <a name="see-also"></a>Vedere anche
- [Mage.exe (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [MageUI.exe (Strumento per la generazione e la modifica di manifesti, client grafico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
- [MakeCert](/windows/desktop/SecCrypto/makecert)
