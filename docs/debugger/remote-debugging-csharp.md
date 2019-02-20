---
title: Eseguire il Debug remoto un C# o un progetto di Visual Basic | Microsoft Docs
ms.custom:
- remotedebugging"=
- seodec18
ms.date: 08/14/2017
ms.topic: conceptual
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: a9753fbb-e7f4-47f0-9dbe-9de90c6c8457
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 470212f3b6dc4151b793dcd62b9ff1d39fc2e55b
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2019
ms.locfileid: "56316223"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Debug remoto un C# o un progetto di Visual Basic in Visual Studio
Per eseguire il debug di un'applicazione di Visual Studio che è stata distribuita in un altro computer, installare ed eseguire remote tools sul computer in cui è distribuita l'app, configurare il progetto per la connessione al computer remoto da Visual Studio e quindi eseguire l'app.

![Componenti del debugger remoto](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")
  
Per informazioni sulle app di Windows universali (UWP) di debug remoto, vedere [eseguire il Debug di un pacchetto dell'App installato](debug-installed-app-package.md).

## <a name="requirements"></a>Requisiti

Il debugger remoto è supportato in Windows 7 e versioni successive (non phone) e le versioni di Windows Server a partire da Windows Server 2008 Service Pack 2. Per un elenco completo dei requisiti, vedere [requisiti](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Non è supportato tra due computer connessi tramite un proxy di debug. Debug tramite una latenza elevata o una connessione di larghezza di banda ridotta, ad esempio Internet, accesso remoto o la rete Internet tra paesi non è consigliabile e può avere esito negativo o essere inaccettabile.
  
## <a name="download-and-install-the-remote-tools"></a>Scaricare e installare Remote Tools

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> In alcuni scenari, può essere più efficiente per eseguire il debugger remoto da una condivisione file. Per altre informazioni, vedere [eseguire il debugger remoto da una condivisione file](../debugger/remote-debugging.md#fileshare_msvsmon).
  
## <a name="BKMK_setup"></a> Configurare il debugger remoto

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se è necessario aggiungere le autorizzazioni per altri utenti, modificare la modalità di autenticazione o il numero di porta per il debugger remoto, vedere [configurare il debugger remoto](../debugger/remote-debugging.md#configure_msvsmon).
  
## <a name="remote_csharp"></a> Eseguire il debug remoto del progetto
Il debugger non può distribuire applicazioni desktop Visual C# o Visual Basic in un computer remoto, ma può comunque eseguirne il debug in modalità remota come illustrato di seguito. La procedura seguente presuppone che si desidera eseguire il debug in un computer denominato **MJO DL**, come mostrato nell'illustrazione seguente.
  
1. Creare un progetto WPF denominato **MyWpf**.  
  
2. Impostare un punto di interruzione facilmente raggiungibile nel codice.  
  
    Ad esempio, è possibile impostare un punto di interruzione in un gestore pulsanti. A tale scopo, aprire MainWindow. XAML e aggiungere un pulsante dalla casella degli strumenti, quindi fare doppio clic sul pulsante per aprire il gestore.
  
3. In Esplora soluzioni fare clic sul progetto e scegliere **proprietà**.  
  
4. Nella pagina **Proprietà** scegliere la scheda **Debug**.  
  
    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5. Verificare che la casella di testo **Directory di lavoro** sia vuota.  
  
6. Scegli **Usa computer remoto**e il tipo **MJO-DL:4022** nella casella di testo. (4022 è il numero di porta visualizzato nella finestra del debugger remoto. Il numero della porta incrementa 2 in ogni versione di Visual Studio).
  
7. Assicurarsi che l'opzione **Attiva il debug di codice nativo** non sia selezionata.  
  
8. Compilare il progetto.  
  
9. Creare una cartella nel computer remoto con lo stesso percorso della cartella **Debug** nel computer di Visual Studio: **\<percorso di origine>\MyWPF\MyWPF\bin\Debug**.  
  
10. Copiare il file eseguibile appena compilato dal computer di Visual Studio alla nuova cartella nel computer remoto.
  
    > [!CAUTION]
    >  Non apportare modifiche al codice o ricompilazione (o è necessario ripetere questo passaggio). Il file eseguibile copiato nel computer remoto deve corrispondere esattamente all'origine locale e ai simboli.

    È possibile copiare manualmente il progetto, usare Xcopy, Robocopy, Powershell o altre opzioni.
  
11. Assicurarsi che il debugger remoto è in esecuzione nel computer di destinazione (in caso contrario, cercare **Remote Debugger** nel **avviare** menu). Finestra del debugger remoto appare come segue.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. Avviare il debug in Visual Studio (**Debug > Avvia debug** o **F5**).  
  
13. Se richiesto, immettere le credenziali di rete per la connessione al computer remoto.  
  
     Le credenziali necessarie variano a seconda della configurazione di sicurezza della rete. In un computer di dominio, ad esempio, è possibile immettere il nome di dominio e la password. In un computer non di dominio, è possibile immettere il nome del computer e un nome di account utente valido, ad esempio <strong>MJO-DL\name@something.com</strong>, con password non corretta.

     La finestra principale dell'applicazione WPF apparirà aperta nel computer remoto.
  
14. Se necessario, intervenire per raggiungere il punto di interruzione. Il punto di interruzione dovrebbe essere attivo. In caso contrario, non sono stati caricati i simboli per l'applicazione. Riprova e se il problema persiste, ottenere informazioni sul caricamento dei simboli e come risolvere i problemi di averli [file dei simboli e Visual Studio le impostazioni dei simboli](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/).
  
15. Nel computer di Visual Studio l'esecuzione viene arrestata in corrispondenza del punto di interruzione.
  
    Se si dispone di tutti i file non di codice che devono essere utilizzate dall'applicazione, è necessario includerli nel progetto di Visual Studio. Creare una cartella di progetto per i file aggiuntivi (in **Esplora soluzioni** fare clic su **Aggiungi > Nuova cartella**). Aggiungere i file alla cartella (in **Esplora soluzioni** fare clic su **Aggiungi > Elemento esistente**, quindi selezionare i file). Nella pagina **Proprietà** di ogni file impostare **Copia nella directory di output** su **Copia sempre**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurare il debug con simboli remoti 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Debug in Visual Studio](../debugger/index.md)  
 [Presentazione del debugger](../debugger/debugger-feature-tour.md)   
 [Configurare Windows Firewall per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)   
 [Debug remoto di ASP.NET in un computer remoto con IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)