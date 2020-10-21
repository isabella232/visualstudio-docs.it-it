---
title: Eseguire il debug remoto di un progetto C++ | Microsoft Docs
ms.custom: remotedebugging
ms.date: 08/14/2018
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
ms.openlocfilehash: 0173ed557afa47129e0cc92d9ef9b2d94a7b198f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "92298729"
---
# <a name="remote-debugging-a-c-project-in-visual-studio"></a>Debug remoto di un progetto C++ in Visual Studio
Per eseguire il debug di un'applicazione di Visual Studio in un computer diverso, installare ed eseguire Remote Tools nel computer in cui verrà distribuita l'app, configurare il progetto per la connessione al computer remoto da Visual Studio e quindi distribuire ed eseguire l'app.

![Componenti del debugger remoto](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Per informazioni sul debug remoto di app di Windows universale (UWP), vedere [eseguire il debug di un pacchetto dell'app installato](debug-installed-app-package.md).

## <a name="requirements"></a>Requisiti

Il debugger remoto è supportato in Windows 7 e versioni successive (non telefono) e versioni di Windows Server a partire da Windows Server 2008 Service Pack 2. Per un elenco completo dei requisiti, vedere [requisiti](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Il debug tra due computer connessi tramite un proxy non è supportato. Non è consigliabile eseguire il debug su una connessione a larghezza di banda elevata o a bassa latenza, ad esempio Internet remoto, o su Internet tra paesi, e potrebbe avere esito negativo o essere inaccettabile.

## <a name="download-and-install-the-remote-tools"></a>Scaricare e installare Remote Tools

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> In alcuni scenari, può essere più efficiente eseguire il debugger remoto da una condivisione file. Per altre informazioni, vedere [eseguire il debugger remoto da una condivisione file](../debugger/remote-debugging.md#fileshare_msvsmon).

## <a name="set-up-the-remote-debugger"></a><a name="BKMK_setup"></a> Configurare il debugger remoto

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se è necessario aggiungere autorizzazioni per utenti aggiuntivi, modificare la modalità di autenticazione o il numero di porta per il debugger remoto, vedere [configurare il debugger remoto](../debugger/remote-debugging.md#configure_msvsmon).

## <a name="remote-debug-a-c-project"></a><a name="remote_cplusplus"></a> Eseguire il debug remoto di un progetto C++
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
   |Connessione|Remoto con autenticazione di Windows|
   |Tipo di debugger|Solo nativo|
   |Directory di distribuzione|C:\remotetemp|
   |File aggiuntivi da distribuire|C:\data\mymfcdata.txt|

    Se si distribuiscono file aggiuntivi (facoltativo), la cartella deve essere presente in entrambi i computer.

6. In Esplora soluzioni fare clic con il pulsante destro del mouse sulla soluzione e scegliere **Configuration Manager**.

7. Per la configurazione **Debug**, selezionare la casella di controllo **Distribuisci**.

    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")

8. Avviare il debug (**Debug > Avvia debug** o **F5**).

9. Il file eseguibile viene distribuito automaticamente al computer remoto.

10. Se richiesto, immettere le credenziali di rete per la connessione al computer remoto.

     Le credenziali necessarie sono specifiche per la configurazione di sicurezza della rete. Ad esempio, in un computer di dominio, è possibile scegliere un certificato di sicurezza oppure immettere il nome di dominio e la password. In un computer non di dominio, è possibile immettere il nome del computer e un nome di account utente valido, <strong>MJO-DL\name@something.com</strong> ad esempio, insieme alla password corretta.

11. Nel computer di Visual Studio l'esecuzione viene arrestata in corrispondenza del punto di interruzione.

    > [!TIP]
    > In alternativa, è possibile distribuire i file come passaggio separato. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo **mymfc**, quindi scegliere **Distribuisci**.

    Se sono presenti file non di codice necessari per l'applicazione, è possibile specificarli in **file aggiuntivi da distribuire** nella pagina del **debugger Windows remoto** .

    In alternativa, è possibile includere i file nel progetto e impostare la proprietà **Content** su **Sì** nella pagina delle **proprietà** per ogni file. Questi file vengono copiati nella **directory di distribuzione** specificata nella pagina **debugger Windows remoto** . È anche possibile modificare il **tipo di elemento** in **copy file** e specificare proprietà aggiuntive se è necessario copiare i file in una sottocartella della **directory di distribuzione**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurare il debug con simboli remoti

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Vedere anche
- [Debug in Visual Studio](../debugger/index.yml)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Configurare Windows Firewall per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Assegnazioni delle porte del debugger remoto](../debugger/remote-debugger-port-assignments.md)
- [Debug remoto di ASP.NET in un computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)