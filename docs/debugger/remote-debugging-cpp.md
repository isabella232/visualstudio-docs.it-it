---
title: Eseguire il debug remoto di un Project | C++ Microsoft Docs
description: Per informazioni su come eseguire il debug Visual Studio'applicazione C++ da un computer remoto, seguire queste istruzioni dettagliate.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- cplusplus
ms.openlocfilehash: ffaa8d1dde6e1304cda0dec33809a01e36fdd56b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627917"
---
# <a name="remote-debugging-a-c-project-in-visual-studio"></a>Debug remoto di un'Project C++ in Visual Studio
Per eseguire il debug di un'applicazione Visual Studio in un computer diverso, installare ed eseguire gli strumenti remoti nel computer in cui si distribuirà l'app, configurare il progetto per connettersi al computer remoto da Visual Studio e quindi distribuire ed eseguire l'app.

![Componenti del debugger remoto](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Per informazioni sul debug remoto di universal Windows Apps (UWP), vedere [Eseguire il debug di un pacchetto di app installato.](debug-installed-app-package.md)

## <a name="requirements"></a>Requisiti

Il debugger remoto è supportato in Windows 7 e versioni successive (non per telefono) e nelle versioni di Windows Server a partire da Windows Server 2008 Service Pack 2. Per un elenco completo dei requisiti, vedere [Requisiti.](../debugger/remote-debugging.md#requirements_msvsmon)

> [!NOTE]
> Il debug tra due computer connessi tramite un proxy non è supportato. Non è consigliabile eseguire il debug su una connessione a latenza elevata o a larghezza di banda ridotta, ad esempio una connessione remota a Internet o su Internet tra paesi diversi, che potrebbe avere esito negativo o essere inaccettabilmente lenta.

## <a name="download-and-install-the-remote-tools"></a>Scaricare e installare Remote Tools

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> In alcuni scenari può essere più efficiente eseguire il debugger remoto da una condivisione file. Per altre informazioni, vedere [Eseguire il debugger remoto da una condivisione file.](../debugger/remote-debugging.md#fileshare_msvsmon)

## <a name="set-up-the-remote-debugger"></a><a name="BKMK_setup"></a> Configurare il debugger remoto

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se è necessario aggiungere autorizzazioni per altri utenti, modificare la modalità di autenticazione o il numero di porta per il debugger remoto, vedere [Configurare il debugger remoto.](../debugger/remote-debugging.md#configure_msvsmon)

## <a name="remote-debug-a-c-project"></a><a name="remote_cplusplus"></a> Eseguire il debug remoto di un progetto C++
 Nella procedura seguente il nome e il percorso del progetto sono C:\remotetemp\MyMfc e il nome del computer remoto è **MJO-DL.**

1. Creare un'applicazione MFC denominata **mymfc.**

2. Impostare un punto di interruzione in un punto dell'applicazione che sia facilmente raggiungibile, ad esempio in **MainFrm.cpp**, all'inizio di `CMainFrame::OnCreate`.

3. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e **scegliere Proprietà.** Aprire la scheda **Debug**.

4. Impostare **Debugger da avviare** su **Debugger Windows remoto**.

    ![Screenshot della scheda Debug nella finestra Visual Studio Esplora soluzioni proprietà. La proprietà Debugger da avviare è impostata su Debugger Windows remoto.](../debugger/media/remotedebuggingcplus.png)

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

    Se si distribuiscono file aggiuntivi (facoltativo), la cartella deve esistere in entrambi i computer.

6. In Esplora soluzioni fare clic con il pulsante destro del mouse sulla soluzione **e scegliere Gestione configurazione**.

7. Per la configurazione **Debug**, selezionare la casella di controllo **Distribuisci**.

    ![Screenshot del Gestione configurazione nel Visual Studio Esplora soluzioni. La configurazione Debug è selezionata e l'opzione Distribuisci è selezionata.](../debugger/media/remotedebugcplusdeploy.png)

8. Avviare il debug (**Debug > Avvia debug** o **F5**).

9. Il file eseguibile viene distribuito automaticamente al computer remoto.

10. Se richiesto, immettere le credenziali di rete per connettersi al computer remoto.

     Le credenziali necessarie sono specifiche della configurazione di sicurezza della rete. In un computer di dominio, ad esempio, è possibile scegliere un certificato di sicurezza o immettere il nome di dominio e la password. In un computer non di dominio è possibile immettere il nome del computer e un nome di account utente valido, ad esempio <strong>MJO-DL\name@something.com</strong> , insieme alla password corretta.

11. Nel computer di Visual Studio l'esecuzione viene arrestata in corrispondenza del punto di interruzione.

    > [!TIP]
    > In alternativa, è possibile distribuire i file come passaggio separato. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo **mymfc**, quindi scegliere **Distribuisci**.

    Se sono presenti file non di codice richiesti dall'applicazione, è possibile specificarli in un elenco delimitato da punto e virgola **in** File aggiuntivi da distribuire nella pagina Debugger **Windows remoto.**

    In alternativa, è possibile includere i file nel progetto e impostare la proprietà **Contenuto** su **Sì** nella **pagina** Proprietà per ogni file. Questi file vengono copiati nella **directory di distribuzione** specificata nella pagina Debugger **Windows** remoto. È anche possibile modificare **Tipo** di elemento in Copia **file** e specificare proprietà aggiuntive se è necessario copiare i file in una sottocartella della directory **di distribuzione**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurare il debug con simboli remoti

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Vedi anche
- [Debug in Visual Studio](../debugger/index.yml)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Configurare il firewall Windows per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Assegnazioni di porta del debugger remoto](../debugger/remote-debugger-port-assignments.md)
- [Debug remoto di ASP.NET in un computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Errori di debug remoto e risoluzione dei problemi](../debugger/remote-debugging-errors-and-troubleshooting.md)