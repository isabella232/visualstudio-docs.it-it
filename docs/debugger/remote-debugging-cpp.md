---
title: Eseguire il Debug remoto un progetto Visual C++ | Microsoft Docs
ms.custom: remotedebugging
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
ms.assetid: 8b8eca0d-122f-4eda-848a-cf0945f207d0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 88deb9957766b4e4e0802a1eded352a6ccb04f98
ms.sourcegitcommit: a916ce1eec19d49f060146f7dd5b65f3925158dd
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2019
ms.locfileid: "55231571"
---
# <a name="remote-debugging-a-visual-c-project-in-visual-studio"></a>Un progetto Visual C++ in Visual Studio di debug remoto
Per eseguire il debug di un'applicazione di Visual Studio in un altro computer, installare ed eseguire remote tools sul computer in cui si distribuirà l'app, configurare il progetto per connettersi al computer remoto da Visual Studio e quindi distribuire ed eseguire l'app.

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

## <a name="remote_cplusplus"></a> Eseguire il debug remoto di un progetto Visual C++  
 Nella procedura seguente, il nome e percorso del progetto sono C:\remotetemp\MyMfc e il nome del computer remoto viene **MJO DL**.  
  
1. Creare un'applicazione MFC denominata **mymfc.**  
  
2. Impostare un punto di interruzione in un punto dell'applicazione che sia facilmente raggiungibile, ad esempio in **MainFrm.cpp**, all'inizio di `CMainFrame::OnCreate`.  
  
3. In Esplora soluzioni fare doppio clic sul progetto e scegliere **proprietà**. Aprire la scheda **Debug**.  
  
4. Impostare **Debugger da avviare** su **Debugger Windows remoto**.  
  
    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5. Apportare le seguenti modifiche alle proprietà:  
  
   |Impostazione|Valore|
   |-|-|  
   |Comando remoto|C:\remotetemp\mymfc.exe|  
   |Directory di lavoro|C:\remotetemp|  
   |Nome server remoto|MJO-DL:*numeroporta*|  
   |Connessione|Remoto con autenticazione di Windows|  
   |Tipo di debugger|Solo nativo|  
   |Directory di distribuzione|C:\remotetemp|  
   |File aggiuntivi da distribuire|C:\data\mymfcdata.txt|  
  
    Se si distribuiscono file aggiuntivi (facoltativi), la cartella deve essere presente in entrambi i computer.  
  
6. In Esplora soluzioni fare doppio clic la soluzione e scegliere **Configuration Manager**.  
  
7. Per la configurazione **Debug**, selezionare la casella di controllo **Distribuisci**.  
  
    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8. Avviare il debug (**Debug > Avvia debug** o **F5**).  
  
9. Il file eseguibile viene distribuito automaticamente al computer remoto.  
  
10. Se richiesto, immettere le credenziali di rete per la connessione al computer remoto.  
  
     Le credenziali necessarie sono specifiche di configurazione della sicurezza della rete. Ad esempio, in un computer di dominio, si potrebbe scegliere un certificato di sicurezza o immettere il nome di dominio e la password. In un computer non di dominio, è possibile immettere il nome del computer e un nome di account utente valido, ad esempio <strong>MJO-DL\name@something.com</strong>, con password non corretta.  
  
11. Nel computer di Visual Studio l'esecuzione viene arrestata in corrispondenza del punto di interruzione.  
  
    > [!TIP]
    > In alternativa, è possibile distribuire i file come passaggio separato. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo **mymfc**, quindi scegliere **Distribuisci**.
  
    Se si dispone di file non di codice che sono richieste dall'applicazione, è possibile specificarli nella **i file aggiuntivi da distribuire** nel **Debugger Windows remoto** pagina.

    In alternativa, è possibile includere i file nel progetto e impostare il **contenuti** proprietà **Sì** nel **proprietà** pagina per ogni file. Questi file vengono copiati il **Directory di distribuzione** specificato per il **Debugger Windows remoto** pagina. È inoltre possibile modificare il **tipo di elemento** al **copia File** e specificare proprietà aggiuntive sono se sono necessari i file da copiare in una sottocartella della **Directory di distribuzione**.
  
## <a name="set-up-debugging-with-remote-symbols"></a>Configurare il debug con simboli remoti 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)] 
  
## <a name="see-also"></a>Vedere anche  
 [Debug in Visual Studio](../debugger/index.md)  
 [Presentazione del debugger](../debugger/debugger-feature-tour.md)   
 [Configurare Windows Firewall per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)   
 [Debug remoto di ASP.NET in un computer remoto con IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)