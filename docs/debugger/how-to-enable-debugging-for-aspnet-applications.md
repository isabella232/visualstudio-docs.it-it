---
title: Abilitare il debug per le app ASP.NET | Microsoft Docs
ms.custom: H1HackMay2017
ms.date: 09/21/18
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: c8723a97f5751b790c946055693064c3b7d12237
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53881101"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Eseguire il debug di App ASP.NET o ASP.NET Core in Visual Studio

È possibile eseguire il debug di App ASP.NET e ASP.NET Core in Visual Studio. Il processo è diverso tra ASP.NET e ASP.NET Core, sia che venga eseguito in IIS Express o un server IIS locale. 

>[!NOTE]
>I passaggi e le impostazioni seguenti si applicano solo al debug delle App in un server locale. Debug di App in un server IIS remoto server utilizza **Connetti a processo**e Ignora queste impostazioni. Per altre informazioni e istruzioni per debug remoto di App ASP.NET in IIS, vedere [Remote debug ASP.NET in un computer IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) oppure [remoto il debug di ASP.NET Core in un computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

Il server predefinito di IIS Express è incluso in Visual Studio. IIS Express è il server di debug predefinito per i progetti ASP.NET e ASP.NET Core e preconfigurato. È il modo più semplice per il debug e ideale per il debug e il test iniziale. 

È anche possibile eseguire il debug di un'app ASP.NET o ASP.NET Core in un server IIS locale (versione 8.0 o versione successiva) che è configurata per eseguire l'app. Per eseguire il debug in IIS locale, è necessario soddisfare i requisiti seguenti: 

<a name="iis"></a>
- Selezionare **supporto IIS in fase di sviluppo** durante l'installazione di Visual Studio. (Se necessario, eseguire nuovamente l'installazione di Visual Studio, selezionare **Modify**e aggiungere questo componente.)
- Eseguire Visual Studio come amministratore. 
- Installare e configurare IIS correttamente con le versioni appropriate di ASP.NET e/o ASP.NET Core. Per altre informazioni e istruzioni, vedere [IIS 8.0 Using ASP.NET 3.5 e ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) oppure [Host ASP.NET Core in Windows con IIS](https://docs.microsoft.com/aspnet/core/host-and-deploy/iis/index).
- Assicurarsi che l'app viene eseguita in IIS senza errori.

## <a name="debug-aspnet-apps"></a>Il debug delle App ASP.NET 

IIS Express è l'impostazione predefinita e preconfigurato. Se esegue il debug in IIS locale, assicurarsi che siano soddisfatti i [i requisiti per il debug locale di IIS](#iis). 

1. Selezionare il progetto ASP.NET in Visual Studio **Esplora soluzioni** e fare clic sui **delle proprietà** icona, premere **Alt**+**invio**, oppure fare doppio clic su e scegliere **delle proprietà**.
   
1. Selezionare il **Web** scheda.
   
1. Nel **delle proprietà** riquadro, di sotto **server**, 
   - Per IIS Express, selezionare **IIS Express** dall'elenco a discesa.
   - Per IIS locale,
     1. Selezionare **IIS locale** dall'elenco a discesa.
     1. Accanto al **URL del progetto** campi, selezionare **crea Directory virtuale**, se non è stato impostato l'App in IIS.
   
1. Sotto **debugger**, selezionare **ASP.NET**.
   
   ![Le impostazioni del debugger ASP.NET](media/dbg-aspnet-enable-debugging2.png "ASP.NET le impostazioni del debugger")
   
1. Uso **File** > **Salva elementi selezionati** oppure **Ctrl**+**S** per salvare le modifiche. 
   
1. Per eseguire il debug dell'app, nel progetto, impostare punti di interruzione nel codice. Sulla barra degli strumenti di Visual Studio, assicurarsi che la configurazione è impostata su **Debug**, e viene visualizzato il browser desiderato nella **IIS Express (\<nome del Browser >)** o **IIS locale (\< Nome del browser >)** nel campo dell'emulatore. 
   
1. Per avviare il debug, selezionare **IIS Express (\<nome del Browser >)** oppure **IIS locale (\<nome Browser >)** sulla barra degli strumenti, selezionare **Avvia debug**dal **eseguire il Debug** dal menu oppure premere **F5**. Il debugger si fermerà in corrispondenza di punti di interruzione. Se il debugger non è possibile raggiungere i punti di interruzione, vedere [risolvere i problemi di debug](#troubleshoot-debugging).

## <a name="debug-aspnet-core-apps"></a>Eseguire il debug delle App ASP.NET Core 

IIS Express è l'impostazione predefinita e preconfigurato. Se esegue il debug in IIS locale, assicurarsi che siano soddisfatti i [i requisiti per il debug locale di IIS](#iis). 

1. Selezionare il progetto ASP.NET Core in Visual Studio **Esplora soluzioni** e fare clic sui **delle proprietà** icona, premere **Alt**+**invio**, o fare clic e scegliere **proprietà**.

1. Selezionare la scheda **Debug**.
   
1. Nel **delle proprietà** riquadro, accanto a **profilo**, 
   - Per IIS Express, selezionare **IIS Express** dall'elenco a discesa.
   - Per IIS locale, selezionare il nome dell'app dall'elenco a discesa oppure selezionare **New**, creare un nuovo nome del profilo e selezionare **OK**.
   
1. Accanto a **avvio veloce**, selezionare **IIS Express** oppure **IIS** dall'elenco a discesa. 
   
1. Assicurarsi che **Avvia browser** sia selezionata.
   
1. Sotto **variabili di ambiente**, verificare che l'opzione **ASPNETCORE_ENVIRONMENT** è presente con il valore **sviluppo**. In caso contrario, selezionare **Add** e aggiungerlo.
   
   ![Le impostazioni di ASP.NET Core debugger](../debugger/media/dbg-aspnet-enable-debugging3.png "le impostazioni del debugger di ASP.NET Core")
   
1. Uso **File** > **Salva elementi selezionati** oppure **Ctrl**+**S** per salvare le modifiche. 
   
1. Per eseguire il debug dell'app, nel progetto, impostare punti di interruzione nel codice. Sulla barra degli strumenti di Visual Studio, assicurarsi che la configurazione è impostata su **Debug**e il valore **IIS Express**, o il nome del nuovo profilo IIS, viene visualizzato nel campo dell'emulatore. 
   
1. Per avviare il debug, selezionare **IIS Express** oppure  **\<nome del profilo IIS >** sulla barra degli strumenti, selezionare **Avvia debug** dal **Debug** dal menu oppure premere **F5**. Il debugger si fermerà in corrispondenza di punti di interruzione. Se il debugger non è possibile raggiungere i punti di interruzione, vedere [risolvere i problemi di debug](#troubleshoot-debugging).

## <a name="troubleshoot-debugging"></a>Risolvere i problemi di debug

Se il debug locale di IIS non è possibile procedere con il punto di interruzione, seguire questi passaggi per risolvere i problemi. 

1. Avviare l'app web da IIS e verificare che venga eseguito correttamente. Lasciare l'app web in esecuzione.
   
2. Da Visual Studio, selezionare **Debug > Connetti a processo** o premere **Ctrl**+**Alt**+**P**, e connettersi al processo ASP.NET o ASP.NET Core (in genere **w3wp.exe** oppure **dotnet.exe**). Per altre informazioni, vedere [Connetti a processo](attach-to-running-processes-with-the-visual-studio-debugger.md) e [come trovare il nome del processo ASP.NET](how-to-find-the-name-of-the-aspnet-process.md).

Se è possibile connettersi e il punto di interruzione usando **Connetti a processo**, ma non tramite **Debug** > **Avvia debug** o **F5**, un'impostazione è probabilmente errata nelle proprietà del progetto. Se si usa un file host, assicurarsi che sia anche configurato correttamente.

## <a name="configure-debugging-in-the-webconfig-file"></a>Configurare il debug nel file Web. config  

I progetti ASP.NET *Web. config* per impostazione predefinita, i file che contengono entrambi informazioni configurazione e avviare app, incluse le impostazioni di debug. Il *Web. config* file devono essere configurati correttamente per il debug. Il **le proprietà** le impostazioni di aggiornamento nelle sezioni precedenti di *Web. config* file, ma è anche possibile configurare tali manualmente. 

> [!NOTE]
> I progetti ASP.NET Core non presentano inizialmente *Web. config* i file, ma usare *appSettings. JSON* e *launchsettings. JSON* file per la configurazione dell'app e l'avvio informazioni. La distribuzione dell'app crea un *Web. config* o i file nel progetto, ma in genere non contengono informazioni di debug.

> [!TIP]
> Può aggiornare il processo di distribuzione di *Web. config* le impostazioni, quindi, prima di provare a eseguire il debug, assicurarsi che il *Web. config* è configurato per il debug.
  
**Per configurare manualmente un *Web. config* file per il debug:**

1. In Visual Studio, aprire il progetto ASP.NET *Web. config* file.  
  
2. *Web. config* è un file XML, di conseguenza contiene sezioni annidate contrassegnate da tag. Individuare il `configuration/system.web/compilation` sezione. (Se il `compilation` elemento non esiste, crearla.)
  
3. Assicurarsi che il `debug` attributo la `compilation` elemento è impostato su `true`. (Se il `compilation` elemento non contiene una `debug` dell'attributo, aggiungerlo e impostarla su `true`.) 
  
   Se si usa IIS locale anziché il server IIS Express predefinito, assicurarsi che il `targetFramework` nel valore dell'attributo di `compilation` elemento corrisponde al framework nel server IIS.
  
   Il `compilation` elemento del *Web. config* file dovrebbe essere simile al seguente:

   > [!NOTE]
   > Questo esempio è un elemento parziale *Web. config* file. Sono disponibili le sezioni XML in genere aggiuntive nel `configuration` e `system.web` gli elementi e il `compilation` elemento potrebbe contenere anche altri attributi ed elementi.
  
   ```xml
   <configuration>  
      ...  
      <system.web>  
          <compilation  debug="true"  targetFramework="4.6.1" ... > 
             ...  
          </compilation>  
      </system.web>  
   </configuration>  
   ```

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] rileva automaticamente qualsiasi modifica apportata ai file *web.config* e applica le nuove impostazioni di configurazione. Non è necessario riavviare il computer o il server IIS rendere effettive le modifiche.  
  
Un sito Web può contenere più directory e sottodirectory virtuali, con *Web. config* file in ognuno di essi. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] le app ereditano le impostazioni di configurazione *Web. config* file a livelli superiori nel percorso URL. La gerarchica *Web. config* file impostazioni si applicano a tutti [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] App sottostanti nella gerarchia. Impostazione di una configurazione diversa in un *Web. config* file di livello inferiore nella gerarchia di override le impostazioni nel file superiore.  
  
Ad esempio, se si specifica `debug="true"` nelle <em>www.microsoft.com/aaa/web.config</em>, in qualsiasi app il *aaa* cartella o in qualsiasi sottocartella di *aaa* eredita tale impostazione, a meno che non sia uno di tali App sostituisce l'impostazione con il proprio *Web. config* file.  
  
## <a name="publish-in-debug-mode-using-the-file-system"></a>Pubblicazione in modalità di debug usando il file system

Esistono diversi modi per pubblicare le App in IIS. Questi passaggi illustrano come creare e distribuire un profilo di pubblicazione utilizzando il file system di debug. A tale scopo, è necessario eseguire Visual Studio come amministratore. 

> [!IMPORTANT]
> Se si modifica il codice o ricompilazione, è necessario ripetere questi passaggi per pubblicare di nuovo. 

1. In Visual Studio, fare clic sul progetto e scegliere **pubblica**.

3. Scegli **IIS, FTP, e così via** e fare clic su **Publish**.

    ![Pubblicazione in IIS](media/dbg-aspnet-local-iis.png "pubblicazione in IIS")

4. Nel **fare** finestra di dialogo per **metodo di pubblicazione**, scegliere **File system**.

5. Per la **percorso di destinazione**, selezionare **Sfoglia** (**...** ).
   
   - Per ASP.NET, selezionare **IIS locale**, selezionare il sito Web creato per l'app e quindi selezionare **Open**.
     
     ![Pubblicare in ASP.NET in IIS](media/dbg-aspnet-local-iis1.png "pubblicazione ASP.NET in IIS")
     
   - Per ASP.NET Core, selezionare **File System**, selezionare la cartella è impostato per l'app e quindi selezionare **Open**.

1. Scegliere **Avanti**. 

1. Sotto **Configuration**, selezionare **Debug** dall'elenco a discesa.

1. Selezionare **Salva**.

1. Nel **Publish** finestra di dialogo assicurarsi **fare** (o il nome del profilo appena creato) viene visualizzata, e **LastUsedBuildConfiguration** è impostata su  **Eseguire il debug**. 

1. Selezionare **Pubblica**.

    ![Pubblicazione in IIS](media/dbg-aspnet-local-iis-select-site.png "pubblicazione in IIS")

> [!IMPORTANT]
> Modalità di debug riduce notevolmente le prestazioni dell'app. Per prestazioni ottimali, impostare `debug="false"` nella *Web. config* e specificare una build di rilascio quando si distribuisce un'app di produzione o condurre misurazioni delle prestazioni.  

## <a name="see-also"></a>Vedere anche  
[Debug di ASP.NET: requisiti di sistema](aspnet-debugging-system-requirements.md)   
[Procedura: Eseguire il processo di lavoro con un account utente](how-to-run-the-worker-process-under-a-user-account.md)   
[Procedura: Trovare il nome del processo ASP.NET](how-to-find-the-name-of-the-aspnet-process.md)   
[Eseguire il debug di applicazioni Web distribuite](debugging-deployed-web-applications.md)   
[Procedura dettagliata: Debug di un Web Form](walkthrough-debugging-a-web-form.md)   
[Procedura: Eseguire il debug di eccezioni ASP.NET](how-to-debug-aspnet-exceptions.md)   
[Eseguire il debug di applicazioni Web: Errori e risoluzione dei problemi](debugging-web-applications-errors-and-troubleshooting.md)
