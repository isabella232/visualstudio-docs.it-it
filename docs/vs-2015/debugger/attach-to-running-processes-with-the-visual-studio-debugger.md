---
title: Connettersi ai processi in esecuzione con il debugger | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.processes.attach
- vs.debug.process
- vs.debug.programs
- vs.debug.detaching
- vs.debug.processes
- vs.debug.error.attach
- vs.debug.remotemachine
dev_langs:
- C++
- CSharp
- FSharp
- VB
- c++
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
caps.latest.revision: 62
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf4d63d7d00e91daa2564992f801896075f73aab
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918937"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Connessione a processi in esecuzione con il debugger di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile collegare il debugger di Visual Studio a un processo in esecuzione in un computer locale o remoto. Al termine dell'esecuzione del processo, fare clic su **debug/Connetti a processo** oppure premere **CTRL + ALT + P**per aprire la finestra di dialogo **Connetti a processo** .

È possibile usare questa funzionalità per eseguire il debug di app in esecuzione in un computer locale o remoto, eseguire il debug di più processi simultaneamente o eseguire il debug di un'applicazione non creata in Visual Studio. Spesso è utile quando si vuole eseguire il debug di un'app, ma (per qualsiasi motivo) non è stata avviata l'app da Visual Studio con il debugger collegato. Ad esempio, se si esegue l'app senza il debugger e si raggiunge un'eccezione, è possibile connettersi al processo che esegue l'app per avviare il debug.

> [!TIP]
> Non si è certi che sia necessario usare **Connetti a processo** per lo scenario di debug? Vedere [scenari di debug comuni](#BKMK_Scenarios). Se si desidera eseguire il debug di applicazioni ASP.NET che sono state distribuite in IIS, vedere [Remote Debugging ASP.NET on a Remote IIS computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

## <a name="BKMK_Attach_to_a_running_process"></a>Connettersi a un processo in esecuzione nel computer locale
 Per connettersi a un processo, è necessario conoscere il nome del processo (vedere [scenari di debug comuni](#BKMK_Scenarios) per alcuni nomi di processo comuni).

1. In Visual Studio selezionare **debug/Connetti a processo** oppure premere **CTRL + ALT + P**.

2. Nella finestra di dialogo **Connetti a processo** individuare il programma con il quale si desidera stabilire una connessione nell'elenco **Processi disponibili** .

     Per selezionare rapidamente il processo desiderato, digitare la prima lettera del nome del processo. Se non si conosce il nome del processo, vedere [scenari di debug comuni](#BKMK_Scenarios).

     ![DBG_Basics_Attach_To_Process](../debugger/media/dbg-basics-attach-to-process.png "DBG_Basics_Attach_To_Process")

     Se il processo viene eseguito con un account utente diverso, selezionare la casella di controllo **Mostra processi di tutti gli utenti** .

3. Nella casella **Connetti a** verificare che sia presente il tipo di codice di cui eseguire il debug. L'impostazione predefinita **Automatico** tenta di determinare il tipo di codice di cui si desidera eseguire il debug. Per impostare manualmente il tipo di codice, eseguire le operazioni seguenti

    1. Nella finestra di dialogo **Connetti a** scegliere **Seleziona**.

    2. Nella finestra di dialogo **Seleziona tipo di codice** fare clic su **Esegui il debug di questi tipi di codice** e selezionare i tipi da sottoporre a debug.

    3. Fare clic su **OK**.

4. Scegliere **Connetti**.

## <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Connettersi a un processo in un computer remoto
 Per connettersi a un processo, è necessario conoscere il nome del processo (vedere [scenari di debug comuni](#BKMK_Scenarios) per alcuni nomi di processo comuni). Per linee guida più complete per le app ASP.NET che sono state distribuite in IIS, vedere [Remote Debugging ASP.NET on a Remote IIS computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Per le altre applicazioni, è possibile trovare il nome del processo in Gestione attività.

 Quando si usa la finestra di dialogo **Connetti a processo** , è possibile selezionare un altro computer configurato per il debug remoto. Per ulteriori informazioni, vedere [Remote Debugging](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c). Dopo avere selezionato un computer remoto, è possibile visualizzare l'elenco dei processi disponibili in esecuzione in tale computer e connettersi a uno o più di questi processi per eseguire il debug.

 **Per selezionare un computer remoto:**

1. In Visual Studio selezionare **debug/Connetti a processo** oppure premere **CTRL + ALT + P**.

2. Nella finestra di dialogo **Connetti a processo** selezionare il tipo di connessione appropriato nell'elenco **Trasporto** . Per la maggior parte dei casi è possibile usare l'impostazione**Predefinito** .

   L'impostazione **Trasporto** viene mantenuta tra una sessione di debug e l'altra.

3. Usare la casella di riepilogo **Qualificatore** per scegliere il nome del computer remoto in uno dei seguenti modi:

   1. Digitare il nome nella casella di riepilogo **Qualificatore** .

      > [!NOTE]
      > Se nei passaggi successivi non è possibile connettersi utilizzando il nome del computer remoto, utilizzare l'indirizzo IP. Il numero di porta può essere visualizzato automaticamente dopo aver selezionato il processo. È anche possibile immetterlo manualmente. Nell'illustrazione seguente, 4020 è la porta predefinita per il debugger remoto.

   2. Fare clic sulla freccia a discesa della casella di riepilogo **Qualificatore** e selezionare il nome del computer dall'elenco a discesa.

   3. Fare clic sul pulsante **trova** accanto all'elenco **qualificatore** per aprire la finestra di dialogo **Seleziona connessione debugger remoto** . Nella finestra di dialogo **Seleziona connessione debugger remoto** sono elencati tutti i dispositivi presenti nella subnet locale e qualsiasi dispositivo connesso direttamente al computer tramite un cavo Ethernet. Fare clic sul computer o sul dispositivo desiderati e scegliere **Seleziona**.

      L'impostazione **Qualificatore** viene invece mantenuta tra due sessioni di debug solo il qualificatore consente di stabilire correttamente una connessione di debug.

4. Fare clic su **Aggiorna**.

     L'elenco **Processi disponibili** viene visualizzato automaticamente quando si apre la finestra di dialogo **Processi** . I processi possono essere avviati e interrotti in background mentre la finestra di dialogo è aperta. È quindi possibile che il contenuto non sia sempre aggiornato. Per visualizzare i processi correnti, è possibile aggiornare l'elenco in qualsiasi momento usando il pulsante **Aggiorna**.

5. Nella finestra di dialogo **Connetti a processo** individuare il programma con il quale si desidera stabilire una connessione nell'elenco **Processi disponibili** .

    Se il processo viene eseguito con un account utente diverso, selezionare la casella di controllo **Mostra processi di tutti gli utenti** .

6. Scegliere **Connetti**.

## <a name="additional-info"></a>Info aggiuntive

Durante l'esecuzione del debug è possibile essere connessi a più di un programma, ma in un dato momento solo uno di tali programmi potrà essere attivo nel debugger. È possibile impostare il programma attivo nella barra degli strumenti **Posizione di debug** o nella finestra **Processi** . Per altre informazioni, vedere [Procedura: Impostare il processo corrente](https://msdn.microsoft.com/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).

Se si tenta di connettersi a un processo appartenente a un account utente non attendibile, verrà visualizzata una finestra di dialogo contenente un avviso di sicurezza per chiedere conferma dell'operazione. Per altre informazioni vedere [avviso di sicurezza: Connessione a un processo appartenente a un utente non attendibile può essere pericolosa. Se le informazioni seguenti sono sospette o non si è certi della loro provenienza e del loro stato, non connettersi al processo](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015).

In alcuni casi, quando viene eseguito il debug in una sessione di Desktop remoto (Servizi terminal), nell'elenco **Processi disponibili** non vengono visualizzati tutti i processi disponibili. Se si esegue Visual Studio con un account utente limitato, nell'elenco **Processi disponibili** non verranno visualizzati i processi in esecuzione nella Sessione 0 utilizzata per i servizi e gli altri processi del server, incluso w3wp.exe. È possibile risolvere il problema eseguendo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] con un account amministratore o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dalla console del server invece di una sessione di Servizi Terminal. Se nessuna di queste soluzioni alternative è possibile, una terza opzione consiste nel connettersi al processo eseguendo `vsjitdebugger.exe -p` *ProcessID* dalla riga di comando di Windows. È possibile determinare l'ID processo usando tlist.exe. Per ottenere tlist.exe, scaricare e installare gli strumenti di debug per Windows disponibili in  [Download di WDK e WinDbg](/windows-hardware/drivers/dashboard/).

## <a name="BKMK_Scenarios"></a>Scenari di debug comuni

Per consentire all'utente di stabilire se è necessario usare **Connetti a processo** e il processo a cui connettersi, vengono visualizzati alcuni scenari di debug comuni (l'elenco non è esaustivo). Se sono disponibili altre istruzioni, vengono forniti i collegamenti.

Per alcuni tipi di app, ad esempio le app di Windows Store, non è possibile connettersi direttamente al nome di un processo, ma usare l'opzione di menu **debug del pacchetto dell'app installata** (vedere la tabella).

> [!NOTE]
> Per informazioni sul debug di base in Visual Studio, vedere la pagina relativa [all'introduzione al debugger](../debugger/getting-started-with-the-debugger.md).

|Scenario|Metodo Debug|Nome processo|Note e collegamenti|
|-|-|-|-|
|Eseguire il debug di un'app gestita o nativa nel computer locale|Usare Connetti a processo o [debug standard](../debugger/getting-started-with-the-debugger.md)|*appname*.exe|Per accedere rapidamente alla finestra di dialogo, premere **CTRL + ALT + P** , quindi digitare la prima lettera del nome del processo.|
|Eseguire il debug di app ASP.NET nel computer locale dopo l'avvio dell'app senza il debugger|Usare Connetti a processo|iiexpress.exe|Questa operazione può essere utile per velocizzare il caricamento dell'app, ad esempio quando si esegue la profilatura. |
|Debug remoto ASP.NET 4 o 4,5 su un server IIS|USA Remote Tools e Connetti a processo|w3wp.exe|Vedere [Remote Debugging ASP.NET on a Remote IIS computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|ASP.NET Core di debug remoto in un server IIS|USA Remote Tools e Connetti a processo|dnx.exe|Per la distribuzione di app, vedere [pubblicare in IIS](https://docs.asp.net/en/latest/publishing/iis.html). Per il debug, vedere [Remote Debugging ASP.NET on a Remote IIS computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Eseguire il debug di altri tipi di app supportati in un processo server|USA Remote Tools (se il server è remoto) e Connetti a processo|iexplore. exe o altri processi|Se necessario, utilizzare Gestione attività per identificare il processo. Vedere [debug remoto](../debugger/remote-debugging.md) e sezioni successive in questo argomento|
|Eseguire il debug remoto di un'app desktop di Windows|Strumenti remoti e F5|N/D| Vedere [debug remoto](../debugger/remote-debugging.md)|
|Eseguire il debug remoto di un'app di Windows universale (UWP), OneCore, HoloLens o Internet.|Debug pacchetto dell'app installato|N/D|USA **debug/altre destinazioni di debug/Esegui debug del pacchetto dell'app installata** anziché **Connetti a processo**|
|Eseguire il debug di un'app di Windows universale (UWP), OneCore, HoloLens o Internet che non è stata avviata da Visual Studio|Debug pacchetto dell'app installato|N/D|USA **debug/altre destinazioni di debug/Esegui debug del pacchetto dell'app installata** anziché **Connetti a processo**|

> [!WARNING]
> Per connettersi a un'app universale di Windows scritta in JavaScript, per prima cosa è necessario abilitare il debug per l'app. Vedere [Attach the debugger](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) in Windows Dev Center.

> [!NOTE]
> Affinché il debugger possa connettersi a codice scritto in C++, è necessario che venga generato l'elemento `DebuggableAttribute`. È possibile aggiungere automaticamente questo elemento al codice mediante il collegamento all'opzione del linker [/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) .

## <a name="what-debugger-features-can-i-use"></a>Quali funzionalità del debugger è possibile usare?

Per usare le funzionalità complete del debugger di Visual Studio, ad esempio il raggiungimento di punti di interruzione, quando ci si connette a un processo, il file eseguibile deve corrispondere esattamente all'origine e ai simboli locali (ovvero, il debugger deve essere in grado di caricare i [file di simboli (con estensione PBD)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)corretti). Per impostazione predefinita, è necessaria una compilazione di debug.

Per gli scenari di debug remoto, è necessario che il codice sorgente (o una copia del codice sorgente) sia già aperto in Visual Studio. I file binari dell'app compilata nel computer remoto devono provenire dalla stessa build del computer locale.

In alcuni scenari di debug locale è possibile eseguire il debug in Visual Studio senza accedere all'origine se i file di simboli corretti sono presenti con l'app (per impostazione predefinita, è necessaria una build di debug). Per altre informazioni, vedere [specificare i file di simboli e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="BKMK_Troubleshoot_attach_errors"></a> Risolvere gli errori di connessione
 I processi in esecuzione a cui il debugger tenta di connettersi possono contenere uno o più tipi di codice. I tipi di codice a cui il debugger può connettersi vengono visualizzati e selezionati nella finestra di dialogo **Seleziona tipo di codice** .

 In alcuni casi il debugger riesce a connettersi a un tipo di codice ma non a un altro. Questa situazione può verificarsi quando si tenta di stabilire una connessione a un processo in esecuzione in un computer remoto, nel quale potrebbero essere stati installati i componenti per il debug remoto solo per alcuni tipi di codice. Può inoltre verificarsi quando si tenta di stabilire una connessione a due o più processi per il debug diretto di un database. Durante il debug SQL è supportata esclusivamente la connessione a un singolo processo.

 Se il debugger è in grado di connettersi solo ad alcuni tipi di codice, verrà visualizzato un messaggio che identifica i tipi per i quali la connessione ha avuto esito negativo.

 Se il debugger riesce a connettersi ad almeno un tipo di codice, è possibile procedere con il debug del processo. Sarà possibile eseguire il debug solo dei tipi di codice con i quali è stata stabilita una connessione. Il messaggio di esempio sopra riportato segnala che non è stato possibile stabilire una connessione al tipo di codice di script. Non sarà quindi possibile eseguire il debug del codice di script nel processo. Il codice di script del processo verrà comunque eseguito, ma non sarà possibile impostare punti di interruzione, visualizzare dati o eseguire altre operazioni di debug nello script.

 Se si desidera ottenere informazioni più specifiche sulla causa che ha impedito al debugger di connettersi a un tipo di codice, è possibile provare a ripetere la connessione solo a quel tipo di codice.

 **Per ottenere informazioni specifiche sulla causa della mancata connessione di un tipo di codice**

1. Disconnettersi dal processo. Scegliere **Disconnetti tutto** dal menu **Debug**.

2. Riconnettersi al processo, selezionando un solo tipo di codice.

   1. Nella finestra di dialogo **Connetti a processo** selezionare il processo nell'elenco **Processi disponibili** .

   2. Fare clic su **Seleziona**.

   3. Nella finestra di dialogo **Seleziona tipo di codice** selezionare il pulsante di opzione **Esegui il debug di questi tipi di codice** e il tipo di codice per cui si è verificato il problema di connessione. Deselezionare tutti gli altri codici.

   4. Fare clic su **OK**. La finestra di dialogo **Seleziona tipo di codice** verrà chiusa.

   5. Nella finestra di dialogo **Connetti a processo** scegliere **Connetti**.

      La connessione non verrà eseguita e verrà visualizzato un messaggio di errore specifico.

## <a name="see-also"></a>Vedere anche
 Debug di [più processi](../debugger/debug-multiple-processes.md) [esecuzione del](../debugger/just-in-time-debugging-in-visual-studio.md) debug [remoto](../debugger/remote-debugging.md)
