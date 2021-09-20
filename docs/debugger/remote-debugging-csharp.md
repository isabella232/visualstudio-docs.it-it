---
title: Eseguire il debug remoto di un progetto VB C# o | Microsoft Docs
description: Per informazioni su come eseguire il debug Visual Studio'applicazione C# o Visual Basic da un computer remoto, seguire queste istruzioni dettagliate.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- dotnet
ms.openlocfilehash: 4bce1ee0c6dd5af379856ae86292fd682964d1b7
ms.sourcegitcommit: c2afe12aaf04456846613550b367cf86eb082f4b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/20/2021
ms.locfileid: "128004549"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Debug remoto di un progetto C# o Visual Basic in Visual Studio
Per eseguire il debug di un'applicazione Visual Studio distribuita in un computer diverso, installare ed eseguire gli strumenti remoti nel computer in cui è stata distribuita l'app, configurare il progetto per connettersi al computer remoto da Visual Studio e quindi eseguire l'app.

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

## <a name="remote-debug-the-project"></a><a name="remote_csharp"></a> Eseguire il debug remoto del progetto
Il debugger non può distribuire applicazioni desktop Visual C# o Visual Basic in un computer remoto, ma può comunque eseguirne il debug in modalità remota come illustrato di seguito. Nella procedura seguente si presuppone che si voglia eseguirne il debug in un computer denominato **MJO-DL,** come illustrato nella figura seguente.

1. Creare un progetto WPF denominato **MyWpf**.

2. Impostare un punto di interruzione facilmente raggiungibile nel codice.

    Ad esempio, è possibile impostare un punto di interruzione in un gestore pulsanti. A tale scopo, aprire MainWindow.xaml e aggiungere un controllo Pulsante dalla casella degli strumenti, quindi fare doppio clic sul pulsante per aprire il gestore.

3. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Proprietà**.

4. Nella pagina **Proprietà** scegliere la scheda **Debug**.

    ![Screenshot della scheda Debug nella finestra Visual Studio Esplora soluzioni proprietà. La proprietà Usa computer remoto è impostata su 'MJO-DL:4022'.](../debugger/media/remotedebuggercsharp.png)

5. Verificare che la casella di testo **Directory di lavoro** sia vuota.

6. Scegliere **Usa computer remoto** e digitare **yourmachinename:port** nella casella di testo. Il numero di porta viene visualizzato nella finestra del debugger remoto. Il numero di porta incrementa 2 in ogni versione di Visual Studio).

    In questo esempio usare:
    ::: moniker range="vs-2022"
    **MJO-DL:4026** in Visual Studio 2019
    ::: moniker-end
    ::: moniker range="vs-2019"
    **MJO-DL:4024** in Visual Studio 2019
    ::: moniker-end
    ::: moniker range="vs-2017"
    **MJO-DL:4022** on Visual Studio 2017
    ::: moniker-end

7. Assicurarsi che l'opzione **Attiva il debug di codice nativo** non sia selezionata.

8. Compilare il progetto.

9. Creare una cartella nel computer remoto che sia lo stesso percorso della cartella **Debug** nel computer Visual Studio: **\<source path> \MyWPF\MyWPF\bin\Debug**.

10. Copiare il file eseguibile appena compilato dal computer di Visual Studio alla nuova cartella nel computer remoto.

    > [!CAUTION]
    > Non apportare modifiche al codice o ricompilare (oppure è necessario ripetere questo passaggio). Il file eseguibile copiato nel computer remoto deve corrispondere esattamente all'origine locale e ai simboli.

    È possibile copiare il progetto manualmente, usare XCopy, Robocopy, PowerShell o altre opzioni.

11. Assicurarsi che il debugger remoto sia in esecuzione nel computer di destinazione (in caso contrario, cercare **Debugger** remoto nel menu **Start).** La finestra del debugger remoto è simile alla seguente.

     ![Screenshot della finestra Visual Studio Debugger remoto di Visual Studio 2017. Viene elencata un'azione che indica che il debugger è in esecuzione nel computer di destinazione.](../debugger/media/remotedebuggerwindow.png)

12. Avviare il debug in Visual Studio (**Debug > Avvia debug** o **F5**).

13. Se richiesto, immettere le credenziali di rete per connettersi al computer remoto.

     Le credenziali necessarie variano a seconda della configurazione di sicurezza della rete. Ad esempio, in un computer di dominio è possibile immettere il nome di dominio e la password. In un computer non di dominio è possibile immettere il nome del computer e un nome di account utente valido, ad esempio <strong>MJO-DL\name@something.com</strong> , insieme alla password corretta.

     La finestra principale dell'applicazione WPF apparirà aperta nel computer remoto.

14. Se necessario, eseguire un'azione per raggiunto il punto di interruzione. Il punto di interruzione dovrebbe essere attivo. In caso contrario, non sono stati caricati i simboli per l'applicazione. Riprovare e, se ciò non funziona, ottenere informazioni sul caricamento dei simboli e su come risolverli in Informazioni sui file di simboli e sulle impostazioni dei simboli Visual Studio di [.](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)

15. Nel computer di Visual Studio l'esecuzione viene arrestata in corrispondenza del punto di interruzione.

    Se sono presenti file non di codice che devono essere usati dall'applicazione, è necessario includerli nel Visual Studio progetto. Creare una cartella di progetto per i file aggiuntivi (nella **Esplora soluzioni** fare clic su > **Nuova cartella**). Aggiungere i file alla cartella (in **Esplora soluzioni** fare clic su **Aggiungi > Elemento esistente**, quindi selezionare i file). Nella pagina **Proprietà** di ogni file impostare **Copia nella directory di output** su **Copia sempre**.

## <a name="set-up-debugging-with-remote-symbols"></a>Configurare il debug con simboli remoti

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Vedi anche
- [Debug in Visual Studio](../debugger/index.yml)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Configurare il firewall Windows per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Assegnazioni di porta del debugger remoto](../debugger/remote-debugger-port-assignments.md)
- [Debug remoto di ASP.NET in un computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Errori di debug remoto e risoluzione dei problemi](../debugger/remote-debugging-errors-and-troubleshooting.md)
