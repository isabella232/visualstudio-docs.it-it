---
title: Debug remoto | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: hero-article
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- CSharp
- FSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
caps.latest.revision: 81
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc6cbcb4bba7e808a72ca389ab8ad9157e80375c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531310"
---
# <a name="remote-debugging"></a>Remote Debugging
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [debug remoto](https://docs.microsoft.com/visualstudio/debugger/remote-debugging).  
  
È possibile eseguire il debug di un'applicazione Visual Studio che è stata distribuita in un computer diverso.  A questo scopo si usa Visual Studio Remote Debugger.  
  
 Le informazioni qui riportate sono valide per applicazioni desktop di Windows e applicazioni ASP.NET.  Per informazioni sul debug remoto di App Windows Store e App di Azure, vedere [debug remoto in App Windows Store e Azure](#bkmk_winstoreAzure).  
  
## <a name="get-the-remote-tools"></a>Download di remote tools  
È possibile scaricare remote tools direttamente sul dispositivo o sul server che si desidera debug o si possono ottenere gli strumenti remoti dal computer host con Visual Studio installato.

### <a name="to-download-and-install-the-remote-tools"></a>Per scaricare e installare remote tools
  
1.  Nel computer server o dispositivo che si desidera eseguire il debug (piuttosto che il computer che esegue Visual Studio), installare la versione corretta di remote tools.

    |Versione|Collegamento|Note|
    |-|-|-|
    |Visual Studio 2015 Update 3|[Remote tools](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Se richiesto, accedere al gruppo di Visual Studio Dev Essentials gratuito o è possibile accedere solo con una sottoscrizione valida di Visual Studio. Quindi aprire nuovamente il collegamento se necessario. Scaricare sempre la versione corrispondente del sistema operativo del dispositivo (x 86, x64 o ARM versione)|
    |Visual Studio 2015 (precedente)|[Remote tools](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Se richiesto, accedere al gruppo di Visual Studio Dev Essentials gratuito o è possibile accedere solo con una sottoscrizione valida di Visual Studio. Quindi aprire nuovamente il collegamento se necessario.|
    |Visual Studio 2013|[Remote tools](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|2000A nella documentazione di Visual Studio 2013|
    |Visual Studio 2012|[Remote tools](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|2000A nella documentazione di Visual Studio 2012|
  
2.  Nella pagina di download, scegliere la versione degli strumenti che corrisponde al sistema operativo (x 86, x64 o ARM versione) e scaricare remote tools.
  
    > [!IMPORTANT]
    >  Si consiglia di che installare la versione più recente di remote tools corrispondente alla versione di Visual Studio. Le versioni non corrispondenti non sono consigliate.  
    >   
    >  Inoltre, è necessario installare gli strumenti remoti che hanno la stessa architettura del sistema operativo in cui si desidera installarlo. In altre parole, se si vuole eseguire il debug di un'applicazione a 32 bit su un un computer remoto che esegue un sistema operativo a 64 bit, è necessario installare la versione a 64 bit di remote tools sul computer remoto.  
  
3.  Dopo avere scaricato il file eseguibile, seguire le istruzioni per installare l'applicazione nel computer remoto. Vedere [istruzioni di configurazione](#bkmk_setup)

Se si prova a copiare il debugger remoto (msvsmon.exe) al computer remoto ed eseguirlo, tenere presente che il **configurazione guidata del Debugger remoto** (**rdbgwiz.exe**) viene installato solo quando si scarica il strumenti e si potrebbe essere necessario utilizzare la procedura guidata per la configurazione in un secondo momento, soprattutto se si desidera che il debugger remoto per l'esecuzione come servizio. Per altre informazioni, vedere [(facoltativo) configurare il debugger remoto come servizio](#bkmk_configureService) sotto.

### <a name="to-run-the-remote-debugger-from-a-file-share"></a>Per eseguire il debugger remoto da una condivisione file

È possibile trovare il debugger remoto (**msvsmon.exe**) in un computer con Visual Studio 2015 Community, Professional o Enterprise già installato. Per molti scenari, il modo più semplice per impostare il debug remoto consiste nell'eseguire il debugger remoto (msvsmon.exe) da una condivisione file. Per le limitazioni di utilizzo, vedere pagina della Guida del debugger remoto (**Guida / utilizzo** nel debugger remoto).

1. Trovare **msvsmon.exe** nella directory corrispondente alla versione di Visual Studio. Per Visual Studio 2015:

      **Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x86\msvsmon.exe**
      
      **Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x64\msvsmon.exe**

2. Condividi i **Remote Debugger** cartella nel computer di Visual Studio.

3. Nel computer remoto, eseguire **msvsmon.exe**. Seguire le [istruzioni di configurazione](#bkmk_setup).

> [!TIP] 
> Per l'installazione dalla riga di comando e i riferimenti alla riga di comando, vedere la pagina della Guida per **msvsmon.exe** digitando ``msvsmon.exe /?`` nella riga di comando nel computer con installato Visual Studio (o passare a **Guida / utilizzo**nel debugger remoto).

  
## <a name="supported-operating-systems"></a>Supported Operating Systems  
 Nel computer remoto deve essere in esecuzione uno dei seguenti sistemi operativi:  
  
-   Windows 10  
  
-   Windows 8 o 8.1  
  
-   Windows 7 Service Pack 1  
  
-   Windows Server 2012 o Windows Server 2012 R2  
  
-   Windows Server 2008 Service Pack 2 o Windows Server 2008 R2 Service Pack 1  
  
## <a name="supported-hardware-configurations"></a>Configurazioni Hardware supportate  
  
-   Processore da 1,6 GHz o superiore  
  
-   1 GB di RAM (1,5 GB se in esecuzione in una macchina virtuale)  
  
-   1 GB di spazio disponibile su disco rigido  
  
-   Unità disco rigido a 5400 rpm  
  
-   Scheda video che supporta DirectX 9 con una risoluzione di 1024 x 768 o superiore  
  
## <a name="network-configuration"></a>Configurazione di rete  
 Il computer remoto e quello che esegue Visual Studio devono essere connessi tramite una rete, un gruppo di lavoro o un gruppo home o collegati direttamente con un cavo Ethernet. Il debug tramite Internet non è supportato.  
  
## <a name="bkmk_setup"></a>Configurare il debugger remoto  
 È necessario avere autorizzazioni amministrative per il computer remoto  
  
1.  Trovare l'applicazione del debugger remoto. (Aprire il menu Start e cercare **Remote Debugger**.)
  
     Se si esegue il debugger remoto in un server remoto, è possibile fare doppio clic il Debugger remoto di app e scegliere **Esegui come amministratore** (oppure, è possibile eseguire il debugger remoto come servizio). Se non si vengono eseguite in un server remoto, semplicemente avviare normalmente.
  
3.  Quando si avvia remote tools per la prima volta (o prima che sia stato configurato), il **configurazione debug remoto** verrà visualizzata la finestra di dialogo.  
  
     ![RemoteDebuggerConfWizardPage](../debugger/media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
4.  Se l'API del servizio Windows non è installato (che si verifica solo in Windows Server 2008 R2), scegliere il **installare** pulsante.  
  
5.  Selezionare i tipi di reti su cui usare Remote Tools. Almeno un tipo di rete deve essere selezionato. Se i computer sono connessi tramite un dominio, è necessario scegliere il primo elemento. Se i computer sono connessi tramite un gruppo di lavoro o un gruppo home, è necessario scegliere il secondo o il terzo elemento a seconda delle esigenze.  
  
6.  Scegli **Configura debug remoto** per configurare il firewall e avviare lo strumento.  
  
7.  Al termine della configurazione viene visualizzata la finestra del debugger remoto.
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
     Il debugger remoto è in attesa di una connessione. Prendere nota del nome del server e la porta numero che viene visualizzato, in quanto servirà in un secondo momento per la configurazione in Visual Studio.  
  
 Al termine delle operazioni di debug ed è necessario arrestare il debugger remoto, fare clic su **File / Esci** nella finestra. È possibile riavviarlo dal **avviare** menu o dalla riga di comando:  
  
 **\<Directory di installazione di Visual Studio > Debugger \Common7\IDE\Remote\\< x86, x64 o Appx\msvsmon.exe**.  
  
## <a name="configure-the-remote-debugger"></a>Configurare il debugger remoto  
 È possibile modificare alcuni aspetti della configurazione del debugger remoto dopo che è stata avviata per la prima volta.
  
-   Per consentire ad altri utenti di connettersi al debugger remoto, scegliere **strumenti / autorizzazioni**. È necessario avere privilegi di amministratore per concedere o negare autorizzazioni.

    > [!IMPORTANT]
    > È possibile eseguire il debugger remoto con un account utente diverso dall'account utente in uso nel computer di Visual Studio, ma è necessario aggiungere l'account utente diverso alle autorizzazioni del debugger remoto. 

     In alternativa, è possibile avviare il debugger remoto dalla riga di comando con il **/Allow \<username >** parametro: **msvsmon /Allow \< username@computer>**.
  
-   Per modificare la modalità di autenticazione o il numero di porta oppure per specificare un valore di timeout per remote tools: scegliere **Strumenti / opzioni**.  
  
     Per un elenco dei numeri di porta usati per impostazione predefinita, vedere [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md).  
  
     > [!WARNING]
>  È possibile scegliere di eseguire Remote Tools in modalità Nessuna autenticazione che, tuttavia, è fortemente sconsigliata perché priva di qualsiasi sicurezza di rete. Scegliere la modalità Nessuna autenticazione solo se si ha la certezza che la rete non è soggetta a rischi derivanti da traffico ostile o dannoso.

##  <a name="bkmk_configureService"></a> (Facoltativo) Configurare il debugger remoto come servizio
 Per il debug in ASP.NET e altri ambienti server, si deve eseguire il debugger remoto come amministratore o, se si desidera sempre in esecuzione, eseguire il debugger remoto come servizio.
  
 Se si desidera configurare il debugger remoto come servizio, seguire questa procedura.  
  
1.  Trovare la **Configurazione guidata del debugger remoto** (rdbgwiz.exe). Si tratta di un'applicazione separata dal debugger remoto. È disponibile solo quando si installa Remote Tools e non è inclusa nell'installazione di Visual Studio.  
  
2.  Avviare la configurazione guidata. Quando viene visualizzata la prima pagina, fare clic su **Avanti**.  
  
3.  Selezionare la casella di controllo **Esegui Visual Studio 2015 Remote Debugger come servizio** .  
  
4.  Aggiungere il nome dell'account utente e la password.  
  
     Potrebbe essere necessario aggiungere il diritto utente **Accedi come servizio** a questo account. A tale scopo, trovare **Criteri di sicurezza locali** (secpol. msc) nella pagina o nella finestra iniziale **avviare** oppure digitare **secpol** al prompt dei comandi. Quando viene visualizzata la finestra, fare doppio clic su **Assegnazione diritti utente**e trovare **Accedi come servizio** nel riquadro di destra. Fare doppio clic. Aggiungere l'account utente per il **delle proprietà** finestra e fare clic su **OK**.) Fare clic su **successivo**.  
  
5.  Selezionare il tipo di rete con cui si vuole che Remote Tools comunichi. Almeno un tipo di rete deve essere selezionato. Se i computer sono connessi tramite un dominio, è necessario scegliere il primo elemento. Se i computer sono connessi tramite un gruppo di lavoro o un gruppo home, è necessario scegliere il secondo o il terzo elemento. Scegliere **Avanti**.  
  
6.  Se è possibile avviare il servizio, viene visualizzato il messaggio **Configurazione guidata di Visual Studio Remote Debugger completata**. Se non è possibile avviare il servizio, viene visualizzato il messaggio **Impossibile completare la Configurazione guidata di Visual Studio Remote Debugger**. La pagina offre anche alcuni suggerimenti da seguire per l'avvio del servizio.  
  
7.  Scegliere **Fine**.  
  
 A questo punto il debugger remoto è in esecuzione come servizio. Per verificarlo, passare a **Pannello di controllo / Servizi** e cercare **Visual Studio 2015 Remote Debugger**.  
  
 È possibile arrestare e avviare il servizio del debugger remoto da **Pannello di controllo / Servizi**.  

## <a name="remote-debug-an-aspnet-application"></a>Eseguire il debug remoto di un'applicazione ASP.NET  
 La distribuzione di un'applicazione ASP.NET in un computer remoto che esegue IIS richiede diversi passaggi, a seconda del sistema operativo e della versione di IIS. Per i computer remoti che eseguono Windows Server 2008 o Windows Server 2012 con IIS 7.5 o versione successiva, vedere [Remote Debugging ASP.NET on a Remote IIS Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).
 
 Se si esegue il debug di un'app ASP.NET Core, vedere [pubblicazione in IIS](https://docs.asp.net/en/latest/publishing/iis.html). Sono necessari passaggi diversi per pubblicare un ASP.NET Core in IIS. Dopo aver pubblicato correttamente un'app ASP.NET Core, è possibile remoto risulti [esattamente come le altre App ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md), ad eccezione del fatto che il processo, è necessario collegare a è dnx.exe invece di w3wp.exe.

## <a name="remote-debug-a-visual-c-project"></a>Eseguire il debug remoto di un progetto Visual C++  
 Nella procedura seguente, il nome e percorso del progetto sono C:\remotetemp\MyMfc e il nome del computer remoto viene **MJO DL**.  
  
1.  Creare un'applicazione MFC denominata **mymfc.**  
  
2.  Impostare un punto di interruzione in una posizione nell'applicazione che sia facilmente raggiungibile, ad esempio nella **MainFrm. cpp**, all'inizio di `CMainFrame::OnCreate`.  
  
3.  In Esplora soluzioni fare doppio clic sul progetto e scegliere **proprietà**. Aprire il **debug** scheda.  
  
4.  Impostare il **Debugger da avviare** al **Debugger Windows remoto**.  
  
     ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5.  Apportare le seguenti modifiche alle proprietà:  
  
    |Impostazione|Valore|
    |-|-|  
    |Comando remoto|C:\remotetemp\mymfc.exe|  
    |Directory di lavoro|C:\remotetemp|  
    |Nome server remoto|MJO-DL:*NumeroPorta*|  
    |Connessione|Remoto con autenticazione di Windows|  
    |Tipo di debugger|Solo nativo|  
    |Directory di distribuzione|C:\remotetemp|  
    |File aggiuntivi da distribuire|C:\data\mymfcdata.txt|  
  
     Se si distribuiscono file aggiuntivi (facoltativi), la cartella deve essere presente in entrambi i computer.  
  
6.  In Esplora soluzioni fare doppio clic la soluzione e scegliere **Configuration Manager**.  
  
7.  Per il **Debug** configurazione, selezionare la **Distribuisci** casella di controllo.  
  
     ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8.  Avviare il debug (**Debug / Avvia debug**, o **F5**).  
  
9. Il file eseguibile viene distribuito automaticamente al computer remoto.  
  
10. Se richiesto, immettere le credenziali di rete per la connessione al computer remoto.  
  
     Le credenziali necessarie sono specifiche di configurazione della sicurezza della rete. Ad esempio, in un computer di dominio, si potrebbe scegliere un certificato di sicurezza o immettere il nome di dominio e la password. In un computer non di dominio, è possibile immettere il nome del computer e un nome di account utente valido, ad esempio **MJO-DL\name@something.com**, con password non corretta.  
  
11. Nel computer di Visual Studio l'esecuzione viene arrestata in corrispondenza del punto di interruzione.  
  
    > [!TIP]
    >  In alternativa, è possibile distribuire i file come passaggio separato. Nel **Esplora soluzioni** fare doppio clic il **mymfc** nodo e quindi scegliere **Distribuisci**.  
  
 Se sono presenti file non di codice che devono essere usati dall'applicazione, è necessario includerli nel progetto di Visual Studio. Creare una cartella di progetto per i file aggiuntivi (nelle **Esplora soluzioni**, fare clic su **Aggiungi / nuova cartella**.) Quindi aggiungere i file nella cartella (nelle **Esplora soluzioni**, fare clic su **Add / esistente elemento**, quindi selezionare i file.). Nel **delle proprietà** pagina per ogni file, impostare **copia in Directory di Output** a **Copia sempre**.  
  
## <a name="remote-debug-a-visual-c-or-visual-basic-project"></a>Eseguire il debug remoto di un progetto Visual C# o Visual Basic  
 Il debugger non può distribuire applicazioni desktop Visual C# o Visual Basic in un computer remoto, ma può comunque eseguirne il debug in modalità remota come illustrato di seguito. La procedura seguente presuppone che si desidera eseguire il debug in un computer denominato **MJO DL**, come illustrato nella figura precedente.
  
1.  Creare un progetto WPF denominato **MyWpf**.  
  
2.  Impostare un punto di interruzione facilmente raggiungibile nel codice.  
  
     Ad esempio, è possibile impostare un punto di interruzione in un gestore pulsanti. A tale scopo, aprire MainWindow. XAML e aggiungere un pulsante dalla casella degli strumenti, quindi fare doppio clic sul pulsante per aprire il gestore.
  
3.  In Esplora soluzioni fare clic sul progetto e scegliere **proprietà**.  
  
4.  Nel **delle proprietà** pagina, scegliere il **Debug** scheda.  
  
     ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5.  Assicurarsi che il **directory di lavoro** casella di testo è vuota.  
  
6.  Scegli **Usa computer remoto**e il tipo **MJO-DL:4020** nella casella di testo. (4020 è il numero di porta visualizzato nella finestra del debugger remoto).  
  
7.  Verificare che l'opzione **Abilita debug codice nativo** non è selezionata.  
  
8.  Compilare il progetto.  
  
9. Creare una cartella nel computer remoto che è lo stesso percorso come il **Debug** cartella nel computer Visual Studio:  **\<percorso di origine > \MyWPF\MyWPF\bin\Debug**.  
  
10. Copiare il file eseguibile appena compilato dal computer di Visual Studio alla nuova cartella nel computer remoto.
  
    > [!CAUTION]
    >  Non apportare modifiche al codice o ricompilazione (o è necessario ripetere questo passaggio). Il file eseguibile copiato nel computer remoto deve corrispondere esattamente all'origine locale e ai simboli.

    È possibile copiare manualmente il progetto, usare Xcopy, Robocopy, Powershell o altre opzioni.
  
11. Assicurarsi che il debugger remoto è in esecuzione nel computer di destinazione. (In caso contrario, cercare **Remote Debugger** nel **avviare** menu. ) Nella finestra del debugger remoto appare come segue.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. In Visual Studio, avviare il debug (**Debug / Avvia debug**, o **F5**).  
  
13. Se richiesto, immettere le credenziali di rete per la connessione al computer remoto.  
  
     Le credenziali necessarie variano a seconda della configurazione di sicurezza della rete. In un computer di dominio, ad esempio, è possibile immettere il nome di dominio e la password. In un computer non di dominio, è possibile immettere il nome del computer e un nome di account utente valido, ad esempio **MJO-DL\name@something.com**, con password non corretta.

     La finestra principale dell'applicazione WPF dovrebbe essere aperta nel computer remoto.
  
14. Se necessario, intervenire per raggiungere il punto di interruzione. Il punto di interruzione dovrebbe essere attivo. In caso contrario, non sono stati caricati i simboli per l'applicazione. Riprova e se il problema persiste, ottenere informazioni sul caricamento dei simboli e come risolvere i problemi di averli [file dei simboli e Visual Studio le impostazioni dei simboli](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/05/understanding-symbol-files-and-visual-studio-s-symbol-settings.aspx).
  
15. Nel computer di Visual Studio l'esecuzione viene arrestata in corrispondenza del punto di interruzione.
  
 Se sono presenti file non di codice che devono essere usati dall'applicazione, è necessario includerli nel progetto di Visual Studio. Creare una cartella di progetto per i file aggiuntivi (nelle **Esplora soluzioni**, fare clic su **Aggiungi / nuova cartella**.) Quindi aggiungere i file nella cartella (nelle **Esplora soluzioni**, fare clic su **Add / esistente elemento**, quindi selezionare i file.). Nel **delle proprietà** pagina per ogni file, impostare **copia in Directory di Output** a **Copia sempre**.
  
## <a name="set-up-debugging-with-remote-symbols"></a>Configurare il debug con simboli remoti  
 Dovrebbe essere possibile eseguire il debug del codice con i simboli generati nel computer di Visual Studio. L'uso di simboli locali consente di migliorare notevolmente le prestazioni del debugger remoto.  Se è necessario usare simboli remoti, indicare a Remote Debugging Monitor di eseguire la ricerca di simboli nel computer remoto.  
  
 A partire da Visual Studio 2013 Update 2, è possibile usare la seguente opzione della riga di comando di msvsmon per usare i simboli remoti per il codice gestito: `Msvsmon / /FallbackLoadRemoteManagedPdbs`  
  
 Per altre informazioni, vedere Guida al debug remoto (premere **F1** la finestra del debugger remoto, oppure fare clic su **Guida / utilizzo**). È possibile trovare altre informazioni, vedere [.NET simbolo modifiche nel caricamento remoto in Visual Studio 2012 e 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)  
  
##  <a name="bkmk_winstoreAzure"></a> Debug remoto in App Windows Store e Azure  
 Per informazioni sul debug remoto con le app di Windows Store, vedere [eseguire il Debug e testare le app di Windows Store in un computer remoto da Visual Studio](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx).  
  
 Per informazioni sul debug in Azure, vedere uno dei seguenti argomenti:  
  
-   [Debug di un servizio Cloud o macchina virtuale in Visual Studio](http://msdn.microsoft.com/library/azure/ff683670.aspx)  
  
-   [Debug di back-end .NET in Visual Studio](http://blogs.msdn.com/b/azuremobile/archive/2014/03/14/debugging-net-backend-in-visual-studio.aspx)  
  
-   Introduzione al debug remoto su siti Web di Azure ([parte 1](http://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/), [parte 2](http://azure.microsoft.com/blog/2014/05/07/introduction-to-remote-debugging-azure-web-sites-part-2-inside-remote-debugging/), [parte 3](http://azure.microsoft.com/blog/2014/05/08/introduction-to-remote-debugging-on-azure-web-sites-part-3-multi-instance-environment-and-git/)).  
  
## <a name="see-also"></a>Vedere anche  
 [Debugging in Visual Studio](../debugger/debugging-in-visual-studio.md)  (Debug in Visual Studio)  
 [Configurare il Firewall di Windows per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Assegnazioni di porta del Debugger remoto](../debugger/remote-debugger-port-assignments.md)   
 [Debug remoto di ASP.NET in un computer remoto con IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)  
 [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)



