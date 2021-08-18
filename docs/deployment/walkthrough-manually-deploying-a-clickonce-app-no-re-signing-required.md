---
title: Distribuire manualmente ClickOnce'app & mantenere la personalizzazione
description: Informazioni su come creare ClickOnce che devono essere distribuite dai clienti senza generare un nuovo manifesto di distribuzione e che possono usare la personalizzazione del cliente.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: edcba59250fad70c2b18b35a8a14a3b95c8db251
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073734"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>Procedura dettagliata: Distribuire manualmente un'ClickOnce che non richiede la nuova firma e che mantiene le informazioni di personalizzazione
Quando si crea un'applicazione e quindi la si assegna a un cliente per la pubblicazione e la distribuzione, il cliente ha tradizionalmente dovuto aggiornare il manifesto della distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] e firmarlo di nuovo. Anche se questo è ancora il metodo preferito nella maggior parte dei casi, .NET Framework 3.5 consente di creare distribuzioni che possono essere distribuite dai clienti senza dover rigenerare un nuovo manifesto di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione. Per altre informazioni, vedere [Distribuire applicazioni ClickOnce per i server di test e di produzione senza dimettersi.](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)

 Quando si crea un'applicazione e quindi la si assegna a un cliente per la pubblicazione e la distribuzione, l'applicazione può usare la personalizzazione del cliente o mantenere [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] la personalizzazione. Ad esempio, se l'applicazione è una singola applicazione proprietaria, è consigliabile mantenere la personalizzazione. Se l'applicazione è altamente personalizzata per ogni cliente, è consigliabile usare la personalizzazione del cliente. La .NET Framework 3.5 consente di mantenere la personalizzazione, le informazioni sull'editore e la firma di sicurezza quando si assegna un'applicazione a un'organizzazione da distribuire. Per altre informazioni, vedere [Creare ClickOnce applicazioni per la distribuzione da parte di altri utenti.](../deployment/creating-clickonce-applications-for-others-to-deploy.md)

> [!NOTE]
> In questa procedura dettagliata le distribuzioni vengono create manualmente usando lo strumento da riga di comandoMage.exe *o* lo strumento grafico *MageUI.exe*. Per altre informazioni sulle distribuzioni manuali, vedere [Procedura dettagliata: Distribuire manualmente un'ClickOnce app.](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)

## <a name="prerequisites"></a>Prerequisiti
 Per eseguire i passaggi di questa procedura dettagliata, sono necessari gli elementi seguenti:

- Applicazione Windows Forms che si è pronti per la distribuzione. Questa applicazione verrà definita *WindowsFormsApp1.*

- Visual Studio o Windows SDK.

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>Per distribuire un'ClickOnce con più distribuzioni e supporto di personalizzazione usando Mage.exe

1. Aprire un Visual Studio prompt dei comandi o un prompt dei comandi e passare alla directory in cui verranno archiviati [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] i [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] file.

2. Creare una directory denominata in base alla versione corrente della distribuzione. Se questa è la prima volta che si distribuisce l'applicazione, è probabile che si **sceglierà 1.0.0.0.0**.

   > [!NOTE]
   > La versione della distribuzione può essere diversa dalla versione dei file dell'applicazione.

3. Creare una sottodirectory denominata **bin** e copiare qui tutti i file dell'applicazione, inclusi file eseguibili, assembly, risorse e file di dati.

4. Generare il manifesto dell'applicazione con una chiamata a Mage.exe.

   ```cmd
   mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"
   ```

5. Firmare il manifesto dell'applicazione con il certificato digitale.

   ```cmd
   mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx
   ```

6. Generare il manifesto della distribuzione con una chiamata a *Mage.exe*. Per impostazione predefinita, *Mage.exe* la distribuzione verrà contrassegnata come applicazione installata, in modo che possa essere [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] eseguita sia online che offline. Per rendere disponibile l'applicazione solo quando l'utente è online, usare `-i` l'argomento con il valore `f` . Poiché questa applicazione sfrutta la funzionalità di distribuzione multipla, escludere l'argomento perMage.exe`-providerUrl` . ** Nelle versioni del .NET Framework precedenti alla versione 3.5, l'esclusione di un'applicazione `-providerUrl` offline restituirà un errore.

   ```cmd
   mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest
   ```

7. Non firmare il manifesto della distribuzione.

8. Fornire tutti i file al cliente, che distribuirà l'applicazione nella rete.

9. A questo punto, il cliente deve firmare il manifesto della distribuzione con il proprio certificato generato automaticamente. Ad esempio, se il cliente lavora per una società denominata Adventure Works, può generare un certificato autofirmato usando lo strumentoMakeCert.exe *lavoro.* Usare quindi lo strumento *Pvk2pfx.exe* per combinare i file creati da *MakeCert.exe* in un file PFX che può essere passato a *Mage.exe*.

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

10. Il cliente usa quindi questo certificato per firmare il manifesto della distribuzione.

    ```cmd
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx
    ```

11. Il cliente distribuisce l'applicazione agli utenti.

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>Per distribuire un'ClickOnce con più distribuzioni e supporto di personalizzazione usando MageUI.exe

1. Aprire un Visual Studio o un prompt dei comandi e passare alla directory in cui verranno [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] archiviati i [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] file.

2. Creare una sottodirectory denominata **bin** e copiare qui tutti i file dell'applicazione, inclusi file eseguibili, assembly, risorse e file di dati.

3. Creare una sottodirectory denominata dopo la versione corrente della distribuzione. Se questa è la prima volta che si distribuisce l'applicazione, è probabile che si **sceglierà 1.0.0.0.0**.

   > [!NOTE]
   > La versione della distribuzione può essere diversa dalla versione dei file dell'applicazione.

4. Spostare la directory \\ **bin** nella directory creata nel passaggio 2.

5. Avviare lo strumento grafico *MageUI.exe*.

   ```cmd
   MageUI.exe
   ```

6. Creare un nuovo manifesto dell'applicazione selezionando **File**, **Nuovo**, **Manifesto applicazione** dal menu.

7. Nella scheda **Nome** predefinita immettere il nome e il numero di versione della distribuzione. Specificare anche un valore per **Publisher**, che verrà usato come nome della cartella per il collegamento di collegamento dell'applicazione nel menu Start quando viene distribuito.

8. Selezionare la **scheda Opzioni applicazione e** fare clic su Usa manifesto **dell'applicazione per informazioni sull'attendibilità**. In questo modo si abiliterà la personalizzazione di terze parti per questa [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione.

9. Selezionare la **scheda File** e fare clic sul **pulsante Sfoglia** accanto alla casella di **testo Directory** applicazione.

10. Selezionare la directory che contiene i file dell'applicazione creati nel passaggio 2 e fare clic su **OK** nella finestra di dialogo di selezione della cartella.

11. Fare clic **sul pulsante Popola** per aggiungere tutti i file dell'applicazione all'elenco di file. Se l'applicazione contiene più file eseguibili, contrassegnare il file eseguibile principale per questa distribuzione come applicazione di avvio selezionando **Punto** di ingresso dall'elenco a discesa **Tipo** di file. Se l'applicazione contiene un  solo file eseguibile,MageUI.execontrassegnarlo per l'utente.

12. Selezionare la **scheda Autorizzazioni necessarie** e selezionare il livello di attendibilità necessario per l'asserzione dell'applicazione. Il valore predefinito è **Attendibilità** totale, che sarà appropriato per la maggior parte delle applicazioni.

13. Selezionare **File**, **Salva** dal menu e salvare il manifesto dell'applicazione. Al momento del salvataggio, verrà richiesto di firmare il manifesto dell'applicazione.

14. Se si dispone di un certificato archiviato come file nel file system, usare l'opzione Firma come **file** di certificato e selezionare il certificato dal file system usando i puntini di sospensione (**...**) pulsante.

     -oppure-

     Se il certificato viene mantenuto in un archivio certificati accessibile dal computer, selezionare l'opzione Firma con certificato archiviato **e** selezionare il certificato nell'elenco fornito.

15. Selezionare **File**, **Nuovo** **,** Manifesto distribuzione dal menu per  creare il manifesto della distribuzione e quindi nella scheda Nome specificare un nome e un numero di versione (**1.0.0.0** in questo esempio).

16. Passare alla **scheda Aggiorna** e specificare la frequenza di aggiornamento dell'applicazione. Se l'applicazione usa l'API di distribuzione per verificare la disponibilità di aggiornamenti, deselezionare la casella di controllo Questa [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione deve controllare la disponibilità di **aggiornamenti**.

17. Passare alla **scheda Riferimento applicazione.** È possibile precompilare tutti i valori in questa  scheda facendo clic sul pulsante Seleziona manifesto e selezionando il manifesto dell'applicazione creato nei passaggi precedenti.

18. Scegliere **Salva** e salvare il manifesto della distribuzione su disco. Al momento del salvataggio, verrà richiesto di firmare il manifesto dell'applicazione. Fare **clic su** Annulla per salvare il manifesto senza firmarlo.

19. Fornire tutti i file dell'applicazione al cliente.

20. A questo punto, il cliente deve firmare il manifesto della distribuzione con il proprio certificato generato automaticamente. Ad esempio, se il cliente lavora per una società denominata Adventure Works, può generare un certificato autofirmato usando lo strumentoMakeCert.exe *lavoro.* Usare quindi lo strumento *Pvk2pfx.exe* per combinare i file creati da *MakeCert.exe* in un file PFX che può essere passato a *MageUI.exe*.

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

21. Con il certificato generato, il cliente firma ora il manifesto della distribuzione aprendo il manifesto di distribuzione *in* MageUI.exee quindi salvando il manifesto. Quando viene visualizzata la finestra di dialogo di firma, il cliente seleziona l'opzione Firma come **file** di certificato e sceglie il file PFX salvato su disco.

22. Il cliente distribuisce l'applicazione agli utenti.

## <a name="see-also"></a>Vedi anche
- [Mage.exe (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [MageUI.exe (Strumento per la generazione e la modifica di manifesti, client grafico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
- [Makecert](/windows/desktop/SecCrypto/makecert)
