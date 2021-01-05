---
title: Eseguire il debug remoto di un progetto C# o VB | Microsoft Docs
description: Per informazioni su come eseguire il debug di un'applicazione Visual Studio C# o Visual Basic da un computer remoto, seguire queste istruzioni dettagliate.
ms.custom:
- remotedebugging"=
- seodec18
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
ms.assetid: a9753fbb-e7f4-47f0-9dbe-9de90c6c8457
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 76364dd6817774c38daa62463cd5bc635075ba73
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815698"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Debug remoto di un progetto C# o Visual Basic in Visual Studio
Per eseguire il debug di un'applicazione di Visual Studio distribuita in un computer diverso, installare ed eseguire Remote Tools nel computer in cui è stata distribuita l'app, configurare il progetto per la connessione al computer remoto da Visual Studio e quindi eseguire l'app.

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

## <a name="remote-debug-the-project"></a><a name="remote_csharp"></a> Eseguire il debug remoto del progetto
Il debugger non può distribuire applicazioni desktop Visual C# o Visual Basic in un computer remoto, ma può comunque eseguirne il debug in modalità remota come illustrato di seguito. Nella procedura seguente si presuppone che si desideri eseguirne il debug in un computer denominato **mjo-DL**, come illustrato nella figura seguente.

1. Creare un progetto WPF denominato **MyWpf**.

2. Impostare un punto di interruzione facilmente raggiungibile nel codice.

    Ad esempio, è possibile impostare un punto di interruzione in un gestore pulsanti. A tale scopo, Aprire MainWindow. XAML e aggiungere un controllo Button dalla casella degli strumenti, quindi fare doppio clic sul pulsante per aprirlo.

3. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Proprietà**.

4. Nella pagina **Proprietà** scegliere la scheda **Debug**.

    ![Screenshot della scheda debug nelle proprietà di Visual Studio Esplora soluzioni. La proprietà Usa computer remoto è impostata su' MJO-DL: 4022'.](../debugger/media/remotedebuggercsharp.png)

5. Verificare che la casella di testo **Directory di lavoro** sia vuota.

6. Scegliere **Usa computer remoto** e digitare **nomecomputer: Port** nella casella di testo. Il numero di porta viene visualizzato nella finestra del debugger remoto. Il numero di porta incrementa 2 in ogni versione di Visual Studio.

    In questo esempio, usare:
    ::: moniker range=">=vs-2019"
    **Mjo-DL: 4024** in Visual Studio 2019
    ::: moniker-end
    ::: moniker range="vs-2017"
    **MJO-DL:4022** on Visual Studio 2017
    ::: moniker-end

7. Assicurarsi che l'opzione **Attiva il debug di codice nativo** non sia selezionata.

8. Compilare il progetto.

9. Creare una cartella nel computer remoto che si trovi nello stesso percorso della cartella di **debug** nel computer di Visual Studio: **\<source path> \MyWPF\MyWPF\bin\Debug**.

10. Copiare il file eseguibile appena compilato dal computer di Visual Studio alla nuova cartella nel computer remoto.

    > [!CAUTION]
    > Non apportare modifiche al codice o alla ricompilazione (oppure è necessario ripetere questo passaggio). Il file eseguibile copiato nel computer remoto deve corrispondere esattamente all'origine locale e ai simboli.

    È possibile copiare il progetto manualmente, utilizzare XCopy, Robocopy, PowerShell o altre opzioni.

11. Verificare che il debugger remoto sia in esecuzione nel computer di destinazione. in caso contrario, cercare **debugger remoto** nel menu **Start** . La finestra del debugger remoto ha un aspetto simile al seguente.

     ![Screenshot della finestra del debugger remoto di Visual Studio 2017. Viene elencata un'azione che indica che il debugger è in esecuzione nel computer di destinazione.](../debugger/media/remotedebuggerwindow.png)

12. Avviare il debug in Visual Studio (**Debug > Avvia debug** o **F5**).

13. Se richiesto, immettere le credenziali di rete per la connessione al computer remoto.

     Le credenziali necessarie variano a seconda della configurazione di sicurezza della rete. Ad esempio, in un computer di dominio è possibile immettere il nome di dominio e la password. In un computer non di dominio, è possibile immettere il nome del computer e un nome di account utente valido, <strong>MJO-DL\name@something.com</strong> ad esempio, insieme alla password corretta.

     La finestra principale dell'applicazione WPF apparirà aperta nel computer remoto.

14. Se necessario, intervenire per raggiungere il punto di interruzione. Il punto di interruzione dovrebbe essere attivo. In caso contrario, non sono stati caricati i simboli per l'applicazione. Riprovare e, se non funziona, ottenere informazioni sul caricamento dei simboli e su come risolverli in informazioni sui [file di simboli e le impostazioni dei simboli di Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/).

15. Nel computer di Visual Studio l'esecuzione viene arrestata in corrispondenza del punto di interruzione.

    Se sono presenti file non di codice che devono essere usati dall'applicazione, è necessario includerli nel progetto di Visual Studio. Creare una cartella di progetto per i file aggiuntivi (nella **Esplora soluzioni** fare clic su **Aggiungi > nuova cartella**). Aggiungere i file alla cartella (in **Esplora soluzioni** fare clic su **Aggiungi > Elemento esistente**, quindi selezionare i file). Nella pagina **Proprietà** di ogni file impostare **Copia nella directory di output** su **Copia sempre**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurare il debug con simboli remoti

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Vedi anche
- [Debug in Visual Studio](../debugger/index.yml)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Configurare la Windows Firewall per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Assegnazioni delle porte del debugger remoto](../debugger/remote-debugger-port-assignments.md)
- [Debug remoto di ASP.NET in un computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Errori e risoluzione dei problemi di debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)