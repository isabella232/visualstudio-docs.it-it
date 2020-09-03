---
title: Debug remoto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 68ebd9ab8c4f9d3cda1371d90a8da459edb1592b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "74300554"
---
# <a name="remote-debugging"></a>Remote Debugging
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile eseguire il debug di un'applicazione Visual Studio che è stata distribuita in un computer diverso.  A questo scopo si usa Visual Studio Remote Debugger.  
  
 Le informazioni qui riportate sono valide per applicazioni desktop di Windows e applicazioni ASP.NET.  Per informazioni sul debug remoto di app di Windows Store e app di Azure, vedere [Remote Debugging on Windows Store and Azure Apps](#bkmk_winstoreAzure).  
  
## <a name="get-the-remote-tools"></a>Ottenere Remote Tools  
È possibile scaricare Remote Tools direttamente nel dispositivo o nel server di cui si vuole eseguire il debug oppure è possibile ottenere Remote Tools dal computer host con Visual Studio installato.

### <a name="to-download-and-install-the-remote-tools"></a>Per scaricare e installare Remote Tools
  
1. Nel computer del dispositivo o del server di cui si vuole eseguire il debug, invece del computer che esegue Visual Studio, ottenere la versione corretta di Remote Tools.

    |Versione|Collegamento|Note|
    |-|-|-|
    |Visual Studio 2015 Update 3|[Strumenti remoti](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Se richiesto, partecipare al gruppo gratuito Visual Studio Dev Essentials oppure è sufficiente accedere con una sottoscrizione valida di Visual Studio. Quindi, riaprire il collegamento, se necessario. Scaricare sempre la versione corrispondente al sistema operativo del dispositivo (x86, x64 o versione ARM)|
    |Visual Studio 2015 (versione precedente)|[Strumenti remoti](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Se richiesto, partecipare al gruppo gratuito Visual Studio Dev Essentials oppure è sufficiente accedere con una sottoscrizione valida di Visual Studio. Quindi, riaprire il collegamento, se necessario.|
    |Visual Studio 2013|[Strumenti remoti](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Pagina di download nella documentazione di Visual Studio 2013|
    |Visual Studio 2012|[Strumenti remoti](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Pagina di download nella documentazione di Visual Studio 2012|
  
2. Nella pagina di download scegliere la versione degli strumenti che corrisponde al sistema operativo (x86, x64 o versione ARM) e scaricare Remote Tools.
  
    > [!IMPORTANT]
    > Si consiglia di installare la versione più recente di Remote Tools che corrisponde alla versione di Visual Studio. Le versioni non corrispondenti non sono consigliate.  
    >   
    >  Inoltre, è necessario installare Remote Tools con la stessa architettura del sistema operativo in cui si vuole installarlo. In altre parole, se si desidera eseguire il debug di un'applicazione a 32 bit in un computer remoto che esegue un sistema operativo a 64 bit, è necessario installare la versione a 64 bit di Remote Tools nel computer remoto.  
  
3. Dopo avere scaricato il file eseguibile, seguire le istruzioni per installare l'applicazione nel computer remoto. Vedere [le istruzioni di installazione](#bkmk_setup)

Se si tenta di copiare il debugger remoto (msvsmon.exe) nel computer remoto ed eseguirlo, tenere presente che la **Configurazione guidata del debugger remoto** (**rdbgwiz.exe**) viene installata solo quando si scaricano gli strumenti e potrebbe essere necessario utilizzare la procedura guidata per la configurazione in un secondo momento, soprattutto se si desidera che il debugger remoto venga eseguito come servizio. Per ulteriori informazioni, vedere [(facoltativo) configurare il debugger remoto come servizio](#bkmk_configureService) .

### <a name="to-run-the-remote-debugger-from-a-file-share"></a>Per eseguire il debugger remoto da una condivisione file

È possibile trovare il debugger remoto (**msvsmon.exe**) in un computer in cui è già installato Visual Studio 2015 community, Professional o Enterprise. Per molti scenari, il modo più semplice per configurare il debug remoto consiste nell'eseguire il debugger remoto (msvsmon.exe) da una condivisione file. Per le limitazioni di utilizzo, vedere la pagina della guida del debugger remoto (**Guida/utilizzo** nel debugger remoto).

1. Trovare **msvsmon.exe** nella directory che corrisponde alla versione di Visual Studio. Per Visual Studio 2015:

      **Programmi\Microsoft Visual Studio 14.0 \ Common7\IDE\Remote Debugger\x86\msvsmon.exe**
      
      **Programmi\Microsoft Visual Studio 14.0 \ Common7\IDE\Remote Debugger\x64\msvsmon.exe**

2. Condividere la cartella del **debugger remoto** nel computer che esegue Visual Studio.

3. Nel computer remoto eseguire **msvsmon.exe**. Seguire le [istruzioni di installazione](#bkmk_setup).

> [!TIP] 
> Per informazioni di riferimento sulla riga di comando e sull'installazione della riga di comando, vedere la pagina della Guida per **msvsmon.exe** digitando nella riga di comando nel computer in cui è ``msvsmon.exe /?`` installato Visual Studio oppure passare a **Guida/utilizzo** nel debugger remoto.

## <a name="supported-operating-systems"></a>Sistemi operativi supportati  
 Nel computer remoto deve essere in esecuzione uno dei seguenti sistemi operativi:  
  
- Windows 10  
  
- Windows 8 o 8.1  
  
- Windows 7 Service Pack 1  
  
- Windows Server 2012 o Windows Server 2012 R2  
  
- Windows Server 2008 Service Pack 2 o Windows Server 2008 R2 Service Pack 1  
  
## <a name="supported-hardware-configurations"></a>Configurazioni Hardware supportate  
  
- Processore da 1,6 GHz o superiore  
  
- 1 GB di RAM (1,5 GB se in esecuzione in una macchina virtuale)  
  
- 1 GB di spazio disponibile su disco rigido  
  
- Unità disco rigido a 5400 rpm  
  
- Scheda video che supporta DirectX 9 con una risoluzione di 1024 x 768 o superiore  
  
## <a name="network-configuration"></a>Configurazione di rete  
 Il computer remoto e quello che esegue Visual Studio devono essere connessi tramite una rete, un gruppo di lavoro o un gruppo home o collegati direttamente con un cavo Ethernet. Il debug tramite Internet non è supportato.  
  
## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a>Configurare il debugger remoto  
 È necessario avere autorizzazioni amministrative per il computer remoto  
  
1. Trovare l'applicazione del debugger remoto. Aprire il menu Start e cercare **remote debugger**.
  
    Se si esegue il debugger remoto in un server remoto, è possibile fare clic con il pulsante destro del mouse sull'app Remote Debugger e scegliere **Esegui come amministratore** (oppure è possibile eseguire il debugger remoto come servizio). Se non è in esecuzione in un server remoto, è sufficiente avviarlo normalmente.
  
2. Quando si avvia Remote Tools per la prima volta (o prima di averlo configurato), viene visualizzata la finestra di dialogo **configurazione debug remoto** eseguito.  
  
    ![RemoteDebuggerConfWizardPage](../debugger/media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
3. Se l'API del servizio Windows non è installata (che si verifica solo in Windows Server 2008 R2), scegliere il pulsante **Installa** .  
  
4. Selezionare i tipi di reti su cui usare Remote Tools. Almeno un tipo di rete deve essere selezionato. Se i computer sono connessi tramite un dominio, è necessario scegliere il primo elemento. Se i computer sono connessi tramite un gruppo di lavoro o un gruppo home, è necessario scegliere il secondo o il terzo elemento a seconda delle esigenze.  
  
5. Scegliere **Configura debug remoto** per configurare il firewall e avviare lo strumento.  
  
6. Al termine della configurazione viene visualizzata la finestra del debugger remoto.
  
    ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
    Il debugger remoto è ora in attesa di una connessione. Prendere nota del nome del server e del numero di porta visualizzato, perché sarà necessario in un secondo momento per la configurazione in Visual Studio.  
  
   Al termine del debug ed è necessario arrestare il debugger remoto, fare clic su **File/Esci** dalla finestra. È possibile riavviarlo dal menu **Start** o dalla riga di comando:  
  
   ** \<Visual Studio installation directory> Debugger \Common7\IDE\Remote \\<x86, x64 o Appx\msvsmon.exe**.  
  
## <a name="configure-the-remote-debugger"></a>Configurare il debugger remoto  
 È possibile modificare alcuni aspetti della configurazione del debugger remoto dopo che è stata avviata per la prima volta.
  
- Per consentire ad altri utenti di connettersi al debugger remoto, scegliere **strumenti/autorizzazioni**. È necessario disporre dei privilegi di amministratore per concedere o negare autorizzazioni.

  > [!IMPORTANT]
  > È possibile eseguire il debugger remoto con un account utente diverso dall'account utente in uso nel computer di Visual Studio, ma è necessario aggiungere l'account utente diverso alle autorizzazioni del debugger remoto. 

   In alternativa, è possibile avviare il debugger remoto dalla riga di comando con il **parametro \<username> /Allow** : **msvsmon/allow \<username@computer> **.
  
- Per modificare la modalità di autenticazione o il numero di porta oppure per specificare un valore di timeout per Remote Tools: scegliere **Strumenti/Opzioni**.  
  
   Per un elenco dei numeri di porta usati per impostazione predefinita, vedere [assegnazioni di porte del debugger remoto](../debugger/remote-debugger-port-assignments.md).  
  
   > [!WARNING]
  > È possibile scegliere di eseguire Remote Tools in modalità Nessuna autenticazione che, tuttavia, è fortemente sconsigliata perché priva di qualsiasi sicurezza di rete. Scegliere la modalità Nessuna autenticazione solo se si ha la certezza che la rete non è soggetta a rischi derivanti da traffico ostile o dannoso.

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a> Opzionale Configurare il debugger remoto come servizio
 Per il debug in ASP.NET e in altri ambienti server, è necessario eseguire il debugger remoto come amministratore o, se si vuole che sia sempre in esecuzione, eseguire il debugger remoto come servizio.
  
 Se si desidera configurare il debugger remoto come servizio, attenersi alla seguente procedura.  
  
1. Trovare la **Configurazione guidata del debugger remoto** (rdbgwiz.exe). Si tratta di un'applicazione separata dal debugger remoto. È disponibile solo quando si installa Remote Tools. e non è inclusa nell'installazione di Visual Studio.  
  
2. Avviare la configurazione guidata. Quando viene visualizzata la prima pagina, fare clic su **Avanti**.  
  
3. Selezionare la casella di controllo **Esegui Visual Studio 2015 Remote Debugger come servizio** .  
  
4. Aggiungere il nome dell'account utente e la password.  
  
    Potrebbe essere necessario aggiungere il diritto utente **Accedi come servizio** a questo account. A tale scopo, trovare **Criteri di sicurezza locali** (secpol. msc) nella pagina o nella finestra iniziale **** oppure digitare **secpol** al prompt dei comandi. Quando viene visualizzata la finestra, fare doppio clic su **Assegnazione diritti utente**e trovare **Accedi come servizio** nel riquadro di destra. Fare doppio clic. Aggiungere l'account utente alla finestra **Proprietà** e fare clic su **OK**. Fare clic su **Avanti**.  
  
5. Selezionare il tipo di rete con cui si vuole che Remote Tools comunichi. Almeno un tipo di rete deve essere selezionato. Se i computer sono connessi tramite un dominio, è necessario scegliere il primo elemento. Se i computer sono connessi tramite un gruppo di lavoro o un gruppo home, è necessario scegliere il secondo o il terzo elemento. Fare clic su **Avanti**.  
  
6. Se è possibile avviare il servizio, viene visualizzato il messaggio **Configurazione guidata di Visual Studio Remote Debugger completata**. Se non è possibile avviare il servizio, viene visualizzato il messaggio **Impossibile completare la Configurazione guidata di Visual Studio Remote Debugger**. La pagina offre anche alcuni suggerimenti da seguire per l'avvio del servizio.  
  
7. Fare clic su **Fine**.  
  
   A questo punto il debugger remoto è in esecuzione come servizio. Per verificarlo, passare a **Pannello di controllo / Servizi** e cercare **Visual Studio 2015 Remote Debugger**.  
  
   È possibile arrestare e avviare il servizio del debugger remoto da **Pannello di controllo / Servizi**.  

## <a name="remote-debug-an-aspnet-application"></a>Eseguire il debug remoto di un'applicazione ASP.NET  
 La distribuzione di un'applicazione ASP.NET in un computer remoto che esegue IIS richiede diversi passaggi, a seconda del sistema operativo e della versione di IIS. Per i computer remoti che eseguono Windows Server 2008 o Windows Server 2012 in cui è installato IIS 7,5 o versione successiva, vedere [Remote Debugging ASP.NET on a Remote IIS computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).
 
 Per eseguire il debug di un'app ASP.NET Core, vedere la pagina relativa [alla pubblicazione in IIS](https://docs.asp.net/en/latest/publishing/iis.html). Sono necessari diversi passaggi per pubblicare un ASP.NET Core in IIS. Dopo la pubblicazione di un'app ASP.NET Core, è possibile eseguirne il debug remoto [come le altre app ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md), ad eccezione del fatto che il processo a cui è necessario connettersi è dnx.exe invece che w3wp.exe.

## <a name="remote-debug-a-visual-c-project"></a>Eseguire il debug remoto di un progetto Visual C++  
 Nella procedura seguente il nome e il percorso del progetto sono C:\remotetemp\MyMfc e il nome del computer remoto è **mjo-DL**.  
  
1. Creare un'applicazione MFC denominata **mymfc.**  
  
2. Impostare un punto di interruzione in un punto dell'applicazione che sia facilmente raggiungibile, ad esempio in **MainFrm.cpp**, all'inizio di `CMainFrame::OnCreate`.  
  
3. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Proprietà**. Aprire la scheda **Debug**.  
  
4. Impostare **Debugger da avviare** su **Debugger Windows remoto**.  
  
    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5. Apportare le seguenti modifiche alle proprietà:  
  
   |Impostazione|Valore|
   |-|-|  
   |Comando remoto|C:\remotetemp\mymfc.exe|  
   |Directory di lavoro|C:\remotetemp|  
   |Nome server remoto|MJO-DL:*numeroporta*|  
   |Connessioni|Remoto con autenticazione di Windows|  
   |Tipo di debugger|Solo nativo|  
   |Directory di distribuzione|C:\remotetemp|  
   |File aggiuntivi da distribuire|C:\data\mymfcdata.txt|  
  
    Se si distribuiscono file aggiuntivi (facoltativo), la cartella deve essere presente in entrambi i computer.  
  
6. In Esplora soluzioni fare clic con il pulsante destro del mouse sulla soluzione e scegliere **Configuration Manager**.  
  
7. Per la configurazione **Debug**, selezionare la casella di controllo **Distribuisci**.  
  
    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8. Avviare il debug (**debug/Avvia debug**o **F5**).  
  
9. Il file eseguibile viene distribuito automaticamente al computer remoto.  
  
10. Se richiesto, immettere le credenziali di rete per la connessione al computer remoto.  
  
     Le credenziali necessarie sono specifiche per la configurazione di sicurezza della rete. Ad esempio, in un computer di dominio, è possibile scegliere un certificato di sicurezza oppure immettere il nome di dominio e la password. In un computer non di dominio, è possibile immettere il nome del computer e un nome di account utente valido, <strong>MJO-DL\name@something.com</strong> ad esempio, insieme alla password corretta.  
  
11. Nel computer di Visual Studio l'esecuzione viene arrestata in corrispondenza del punto di interruzione.  
  
    > [!TIP]
    > In alternativa, è possibile distribuire i file come passaggio separato. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo **mymfc**, quindi scegliere **Distribuisci**.  
  
    Se sono presenti file non di codice che devono essere usati dall'applicazione, è necessario includerli nel progetto di Visual Studio. Creare una cartella di progetto per i file aggiuntivi (nella **Esplora soluzioni**fare clic su **Aggiungi/nuova cartella**). Quindi aggiungere i file alla cartella (nella **Esplora soluzioni**fare clic su **Aggiungi/elemento esistente**, quindi selezionare i file). Nella pagina **Proprietà** di ogni file impostare **Copia nella directory di output** su **Copia sempre**.  
  
## <a name="remote-debug-a-visual-c-or-visual-basic-project"></a>Eseguire il debug remoto di un progetto Visual C# o Visual Basic  
 Il debugger non può distribuire applicazioni desktop Visual C# o Visual Basic in un computer remoto, ma può comunque eseguirne il debug in modalità remota come illustrato di seguito. Nella procedura seguente si presuppone che si desideri eseguirne il debug in un computer denominato **mjo-DL**, come illustrato nella figura precedente.
  
1. Creare un progetto WPF denominato **MyWpf**.  
  
2. Impostare un punto di interruzione facilmente raggiungibile nel codice.  
  
    Ad esempio, è possibile impostare un punto di interruzione in un gestore pulsanti. A tale scopo, Aprire MainWindow. XAML e aggiungere un controllo Button dalla casella degli strumenti, quindi fare doppio clic sul pulsante per aprirlo.
  
3. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Proprietà**.  
  
4. Nella pagina **Proprietà** scegliere la scheda **Debug**.  
  
    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5. Verificare che la casella di testo **Directory di lavoro** sia vuota.  
  
6. Scegliere **Usa computer remoto**e digitare **mjo-DL: 4020** nella casella di testo. 4020 è il numero di porta visualizzato nella finestra del debugger remoto.  
  
7. Assicurarsi che l'opzione **Attiva il debug di codice nativo** non sia selezionata.  
  
8. Compilare il progetto.  
  
9. Creare una cartella nel computer remoto che si trovi nello stesso percorso della cartella di **debug** nel computer di Visual Studio: ** \<source path> \MyWPF\MyWPF\bin\Debug**.  
  
10. Copiare il file eseguibile appena compilato dal computer di Visual Studio alla nuova cartella nel computer remoto.
  
    > [!CAUTION]
    > Non apportare modifiche al codice o alla ricompilazione (oppure è necessario ripetere questo passaggio). Il file eseguibile copiato nel computer remoto deve corrispondere esattamente all'origine locale e ai simboli.

    È possibile copiare il progetto manualmente, utilizzare XCOPY, Robocopy, PowerShell o altre opzioni.
  
11. Verificare che il debugger remoto sia in esecuzione nel computer di destinazione. In caso contrario, cercare **remote debugger** nel menu **Start** . ) La finestra del debugger remoto ha un aspetto simile al seguente.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. In Visual Studio avviare il debug (**debug/Avvia debug**o **F5**).  
  
13. Se richiesto, immettere le credenziali di rete per la connessione al computer remoto.  
  
     Le credenziali necessarie variano a seconda della configurazione di sicurezza della rete. Ad esempio, in un computer di dominio è possibile immettere il nome di dominio e la password. In un computer non di dominio, è possibile immettere il nome del computer e un nome di account utente valido, <strong>MJO-DL\name@something.com</strong> ad esempio, insieme alla password corretta.

     La finestra principale dell'applicazione WPF dovrebbe essere aperta nel computer remoto.
  
14. Se necessario, intervenire per raggiungere il punto di interruzione. Il punto di interruzione dovrebbe essere attivo. In caso contrario, non sono stati caricati i simboli per l'applicazione. Riprovare e, se non funziona, ottenere informazioni sul caricamento dei simboli e su come risolverli in informazioni sui [file di simboli e le impostazioni dei simboli di Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/).
  
15. Nel computer di Visual Studio l'esecuzione viene arrestata in corrispondenza del punto di interruzione.
  
    Se sono presenti file non di codice che devono essere usati dall'applicazione, è necessario includerli nel progetto di Visual Studio. Creare una cartella di progetto per i file aggiuntivi (nella **Esplora soluzioni**fare clic su **Aggiungi/nuova cartella**). Quindi aggiungere i file alla cartella (nella **Esplora soluzioni**fare clic su **Aggiungi/elemento esistente**, quindi selezionare i file). Nella pagina **Proprietà** di ogni file impostare **Copia nella directory di output** su **Copia sempre**.
  
## <a name="set-up-debugging-with-remote-symbols"></a>Configurare il debug con simboli remoti  
 Dovrebbe essere possibile eseguire il debug del codice con i simboli generati nel computer di Visual Studio. L'uso di simboli locali consente di migliorare notevolmente le prestazioni del debugger remoto.  Se è necessario usare simboli remoti, indicare a Remote Debugging Monitor di eseguire la ricerca di simboli nel computer remoto.  
  
 A partire da Visual Studio 2013 Update 2 è possibile usare la seguente opzione della riga di comando di msvsmon per usare i simboli remoti per il codice gestito: `Msvsmon / /FallbackLoadRemoteManagedPdbs`  
  
 Per ulteriori informazioni, vedere la guida per il debug remoto (premere **F1** nella finestra del debugger remoto oppure fare clic su **Guida/utilizzo**). Altre informazioni sono disponibili nel post del blog [.NET Remote Symbol Loading Changes in Visual Studio 2012 and 2013](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/) (Modifiche nel caricamento remoto dei simboli .NET in Visual Studio 2012 e 2013).  
  
## <a name="remote-debugging-on-windows-store-and-azure-apps"></a><a name="bkmk_winstoreAzure"></a> Debug remoto in Windows Store e app di Azure  
 Per informazioni sul debug remoto con le app di Windows Store, vedere [debug e test di app di Windows Store in un dispositivo remoto da Visual Studio](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx).  
  
 Per informazioni sul debug in Azure, vedere uno dei seguenti argomenti:  
  
- [Debug di un servizio cloud o di una macchina virtuale in Visual Studio](../azure/vs-azure-tools-debug-cloud-services-virtual-machines.md)  
  
- [Debug del back-end .NET in Visual Studio](https://blogs.msdn.microsoft.com/azuremobile/2014/03/14/debugging-net-backend-in-visual-studio/)  
  
- Introduzione al debug remoto nei siti Web di Azure ([parte 1](https://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/), [parte 2](https://azure.microsoft.com/blog/2014/05/07/introduction-to-remote-debugging-azure-web-sites-part-2-inside-remote-debugging/), [parte 3](https://azure.microsoft.com/blog/2014/05/08/introduction-to-remote-debugging-on-azure-web-sites-part-3-multi-instance-environment-and-git/)).  
  
## <a name="see-also"></a>Vedere anche  
 [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Configurare la Windows Firewall per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Assegnazioni delle porte del debugger remoto](../debugger/remote-debugger-port-assignments.md)   
 [Debug remoto di ASP.NET in un computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)  
 [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)
