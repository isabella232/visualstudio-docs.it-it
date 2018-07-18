---
title: Collegamento a processi in esecuzione con il Debugger di Visual Studio | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 06/20/2018
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
- CSharp
- FSharp
- C++
- VB
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 260047497ddb9515505c13f0b861c8eee05d71b0
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2018
ms.locfileid: "36327333"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Connessione a processi in esecuzione con il debugger di Visual Studio
È possibile collegare il debugger di Visual Studio a un processo in esecuzione in un computer locale o remoto. Dopo l'esecuzione del processo, fare clic su **Debug > Connetti a processo** (o premere **CTRL + ALT + P**) per aprire il **Connetti a processo** nella finestra di dialogo.

È possibile usare questa funzionalità per il debug delle App in esecuzione in un computer locale o remoto, eseguire il debug di più processi contemporaneamente o eseguire il debug di un'applicazione che non è stata creata in Visual Studio. È spesso utile quando si desidera eseguire il debug di un'app, ma (per qualsiasi motivo) non è stato avviato l'app da Visual Studio con il debugger collegato. Ad esempio, se si esegue l'app senza il debugger e verificata un'eccezione, potrebbe quindi collegare al processo di esecuzione dell'app per avviare il debug.

> [!TIP]
> Non si è certi se è necessario usare **Connetti a processo** per lo scenario di debug? Visualizzare [comuni scenari di debug](#BKMK_Scenarios). Se si desidera eseguire il debug di applicazioni ASP.NET che sono state distribuite a IIS, vedere [Remote Debugging ASP.NET in un computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

##  <a name="BKMK_Attach_to_a_running_process"></a> Connettersi a un processo in esecuzione nel computer locale  
 Per connettersi a un processo, è necessario conoscere il nome del processo (vedere [comuni scenari di debug](#BKMK_Scenarios) per alcuni nomi di processo comuni).
  
1.  In Visual Studio, selezionare **Debug > Connetti a processo** (o premere **CTRL + ALT + P**).

    Se si vuole riconnettere rapidamente un processo in alternativa, vedere [riassocia a processo](#BKMK_reattach).
  
2.  Nella finestra di dialogo **Connetti a processo** individuare il programma con il quale si desidera stabilire una connessione nell'elenco **Processi disponibili** .  

     Per selezionare rapidamente il processo desiderato, digitare la prima lettera del nome del processo oppure è possibile digitare un valore nella casella del filtro per cercare un nome di processo. Se non si conosce il nome del processo, vedere [comuni scenari di debug](#BKMK_Scenarios).
     
     ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process") 
  
     Se il processo viene eseguito con un account utente diverso, selezionare la casella di controllo **Mostra processi di tutti gli utenti** .
  
3.  Nella casella **Connetti a** verificare che sia presente il tipo di codice di cui eseguire il debug. L'impostazione predefinita **Automatico** tenta di determinare il tipo di codice di cui si desidera eseguire il debug. Per impostare manualmente il tipo di codice, eseguire le operazioni seguenti  
  
    1.  Nella finestra di dialogo **Connetti a** scegliere **Seleziona**.  
  
    2.  Nella finestra di dialogo **Seleziona tipo di codice** fare clic su **Esegui il debug di questi tipi di codice** e selezionare i tipi da sottoporre a debug.

        Il valore predefinito **automatica** l'impostazione funziona per la maggior parte dei tipi di app. Per eseguire il debug dello script lato client in Chrome, scegliere **Webkit** come tipo di codice. Per Chrome, è possibile necessario avviare il browser in modalità in base al tipo di applicazione di debug (tipo `chrome.exe --remote-debugging-port=9222` dalla riga di comando).

        > [!NOTE]
        > Per il debug di script lato client, è necessario abilitare il debug degli script nel browser. 
  
    3.  Fare clic su **OK**.  
  
4.  Scegliere **Connetti**.

##  <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Connettersi a un processo in un computer remoto  
Per connettersi a un processo, è necessario conoscere il nome del processo (vedere [comuni scenari di debug](#BKMK_Scenarios) per alcuni nomi di processo comuni). Per istruzioni più complete per le app ASP.NET che sono state distribuite a IIS, vedere [Remote Debugging ASP.NET in un computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Se non si conosce il nome del processo per lo scenario, vedere [comuni scenari di debug](#BKMK_Scenarios)
  
Quando si usa la **Connetti a processo** nella finestra di dialogo è possibile selezionare un altro computer in cui è stato configurato per il debug remoto (vale a dire, il debugger remoto deve essere in esecuzione nel computer remoto). Per altre informazioni, vedere [debug remoto](../debugger/remote-debugging.md). Dopo avere selezionato un computer remoto, è possibile visualizzare l'elenco dei processi disponibili in esecuzione in tale computer e connettersi a uno o più di questi processi per eseguire il debug.
  
**Per selezionare un computer remoto:**  

1. In Visual Studio, selezionare **Debug > Connetti a processo** (o premere **CTRL + ALT + P**).

    Se si vuole riconnettere rapidamente un processo in alternativa, vedere [riassocia a processo](#BKMK_reattach).

2.  Nella finestra di dialogo **Connetti a processo** selezionare il tipo di connessione appropriato nell'elenco **Trasporto** . Per la maggior parte dei casi è possibile usare l'impostazione**Predefinito** .

    L'impostazione **Trasporto** viene mantenuta tra una sessione di debug e l'altra. 
  
3.  Usare la casella di riepilogo **Qualificatore** per scegliere il nome del computer remoto in uno dei seguenti modi:  
  
    1.  Digitare il nome nella casella di riepilogo **Qualificatore** .
    
        > [!Note]
        > Se, nei passaggi successivi, è possibile connettersi usando il nome del computer remoto, usare l'indirizzo IP. (Il numero di porta può essere visualizzato automaticamente dopo il processo di selezione. È possibile anche inserire manualmente. Nell'illustrazione seguente, 4020 è la porta predefinita per il debugger remoto.)  

        Se si desidera utilizzare il **trovare** pulsante, potrebbe essere necessario [aprire la porta UDP 3702](../debugger/remote-debugger-port-assignments.md) nel server.
  
    2.  Fare clic sulla freccia a discesa della casella di riepilogo **Qualificatore** e selezionare il nome del computer dall'elenco a discesa.  
  
    3.  Scegliere il pulsante **Trova** accanto all'elenco**Qualificatore** per aprire la finestra di dialogo **Seleziona connessione debugger remoto** . Nella finestra di dialogo **Seleziona connessione debugger remoto** sono elencati tutti i dispositivi presenti nella subnet locale e qualsiasi dispositivo connesso direttamente al computer tramite un cavo Ethernet. Fare clic sul computer o sul dispositivo desiderati e scegliere **Seleziona**. 
  
     L'impostazione **Qualificatore** viene invece mantenuta tra due sessioni di debug solo il qualificatore consente di stabilire correttamente una connessione di debug.
     
4.  Fare clic su **Aggiorna**.

      L'elenco **Processi disponibili** viene visualizzato automaticamente quando si apre la finestra di dialogo **Processi** . I processi possono essere avviati e interrotti in background mentre la finestra di dialogo è aperta. È quindi possibile che il contenuto non sia sempre aggiornato. Per visualizzare i processi correnti, è possibile aggiornare l'elenco in qualsiasi momento usando il pulsante **Aggiorna**. 
     
4.  Nella finestra di dialogo **Connetti a processo** individuare il programma con il quale si desidera stabilire una connessione nell'elenco **Processi disponibili** .

     Per selezionare rapidamente il processo desiderato, digitare la prima lettera del nome del processo oppure è possibile digitare un valore nella casella del filtro per cercare un nome di processo. Se non si conosce il nome del processo, vedere [comuni scenari di debug](#BKMK_Scenarios).
  
     Se il processo viene eseguito con un account utente diverso, selezionare la casella di controllo **Mostra processi di tutti gli utenti** .
     
5.  Scegliere **Connetti**.

## <a name="BKMK_reattach"></a> Riassocia a processo

È possibile riconnettere rapidamente i processi che sono stati precedentemente collegato a scegliendo **Debug > riassocia a processo...** (**Maiusc + Alt + P**). Quando si sceglie questo comando, il debugger tenterà immediatamente di connettere all'ultima processi sono stati collegati a usando la **Connetti a processo** nella finestra di dialogo.

Il debugger si riconnetterà tentando innanzitutto di associare l'ID del processo precedente e quindi, se ha esito negativo, associando il precedente nome del processo. Se non vengono trovate corrispondenze o se sono presenti più processi con lo stesso nome, il **Connetti a processo** verrà visualizzata la finestra di dialogo in cui è possibile selezionare il processo corretto.

> [!NOTE]
> Il **riassocia a processo** command è una novità in Visual Studio 2017.

## <a name="additional-info"></a>Informazioni aggiuntive

Durante l'esecuzione del debug è possibile essere connessi a più di un programma, ma in un dato momento solo uno di tali programmi potrà essere attivo nel debugger. È possibile impostare il programma attivo nella barra degli strumenti **Posizione di debug** o nella finestra **Processi** .  
  
Se si tenta di connettersi a un processo appartenente a un account utente non attendibile, verrà visualizzata una finestra di dialogo contenente un avviso di sicurezza per chiedere conferma dell'operazione. Per altre informazioni vedere [avviso di sicurezza: connessione a un processo appartenente a un utente non attendibile può essere pericolosa. Se le informazioni seguenti risultano sospette o non si è certi, non stabilire la connessione al processo](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).  
  
In alcuni casi, quando viene eseguito il debug in una sessione di Desktop remoto (Servizi terminal), nell'elenco **Processi disponibili** non vengono visualizzati tutti i processi disponibili. Se si esegue Visual Studio con un account utente limitato, nell'elenco **Processi disponibili** non verranno visualizzati i processi in esecuzione nella Sessione 0 utilizzata per i servizi e gli altri processi del server, incluso w3wp.exe. È possibile risolvere il problema eseguendo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] con un account amministratore o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dalla console del server invece di una sessione di Servizi Terminal. Se non è possibile adottare una di queste soluzioni alternative, una terza opzione consiste nel connettersi al processo eseguendo `vsjitdebugger.exe -p` *ProcessId* dalla riga di comando di Windows. È possibile determinare l'ID processo usando tlist.exe. Per ottenere tlist.exe, scaricare e installare gli strumenti di debug per Windows, disponibile all'indirizzo [download WDK e WinDbg](/windows-hardware/drivers/download-the-wdk).

## <a name="BKMK_Scenarios"></a> Scenari di debug comuni

Per identificare se è necessario usare **Connetti a processo** e sui processi a cui connettersi, di seguito sono riportati alcuni scenari di debug comuni (l'elenco non è completo). Dove sono disponibili altre istruzioni, sono disponibili collegamenti. Per accedere rapidamente la finestra di dialogo, utilizzare **CTRL + ALT + P** e quindi digitare la prima lettera del nome del processo.

Per alcuni tipi di app (ad esempio, le app UWP), non collega direttamente a un nome di processo, ma usare il **Debug pacchetto applicazione installato** invece l'opzione di menu (vedere la tabella).

> [!NOTE]
> Per informazioni sul debug di base in Visual Studio, vedere [Guida introduttiva con il debugger](../debugger/getting-started-with-the-debugger.md).

|Scenario|Eseguire il debug (metodo)|Nome processo|Note e collegamenti|
|-|-|-|-|
|Il debug remoto di ASP.NET 4 o 4.5 in un server IIS|Utilizzare gli strumenti remoti e connettersi al processo|w3wp.exe|Vedere [Remote Debugging ASP.NET in un computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Debug remoto di ASP.NET Core in un server IIS|Utilizzare gli strumenti remoti e connettersi al processo|dotnet.exe|Per la distribuzione di app, vedere [pubblicazione su IIS](https://docs.asp.net/en/latest/publishing/iis.html). Per eseguire il debug, vedere [Remote Debug ASP.NET Core in un computer IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|Eseguire il debug di script sul lato client in un server IIS locale (solo per i tipi di app supportati)|Usare associa a processo|Chrome.exe, MicrosoftEdgeCP.exe o iexplore.exe|Debug degli script deve essere abilitato. Per Chrome, è necessario eseguire anche Chrome in modalità di debug e selezionare **Webkit code** nel **collegare a** campo.|
|Debug di un'app c#, Visual Basic o C++ nel computer locale|Usare uno [debug standard](../debugger/getting-started-with-the-debugger.md) o Connetti a processo|*appname*.exe|Nella maggior parte degli scenari, usare il debug standard e connettersi al processo.|
|Debug remoto di un'app desktop di Windows|Remote tools|N/D| Visualizzare [Remote debug di un'app c# o Visual Basic](../debugger/remote-debugging-csharp.md) o [un'app C++ di eseguire il debug remoto](../debugger/remote-debugging-cpp.md)|
|Eseguire il debug di App ASP.NET nel computer locale dopo l'avvio dell'app senza il debugger|Usare associa a processo|iiexpress.exe|Questo potrebbe essere utile per rendere l'app di caricare più veloce, ad esempio, ad esempio, la profilatura. |
|Eseguire il debug di altri tipi di app supportati in un processo del server|Utilizzare gli strumenti remoti (se è remoto server) e associa a processo|Chrome.exe, iexplore.exe o altri processi|Se necessario, è possibile utilizzare Monitoraggio risorse per semplificare l'identificazione del processo. Visualizzare [debug remoto](../debugger/remote-debugging.md) e nelle sezioni successive di questo argomento|
|Un'app UWP (Universal), OneCore, HoloLens o IoT eseguire il debug remoto|Eseguire il debug pacchetto dell'app installato|N/D|Visualizzare [eseguire il Debug di un pacchetto dell'App installata](debug-installed-app-package.md) invece di usare **Connetti a processo**|
|Eseguire il debug di un'app per App di Windows universale (UWP), OneCore, HoloLens e IoT che non è stato avviato da Visual Studio|Eseguire il debug pacchetto dell'app installato|N/D|Visualizzare [eseguire il Debug di un pacchetto dell'App installata](debug-installed-app-package.md) invece di usare **Connetti a processo**|  
  
> [!NOTE]
>  Affinché il debugger possa connettersi a codice scritto in C++, è necessario che venga generato l'elemento `DebuggableAttribute`. È possibile aggiungere automaticamente questo elemento al codice mediante il collegamento all'opzione del linker [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) .

## <a name="what-debugger-features-can-i-use"></a>Le funzionalità del debugger è possibile usare?

Per utilizzare le funzionalità complete del debugger di Visual Studio (ad esempio, raggiungere punti di interruzione) quando si collega a un processo, il file eseguibile deve corrispondere esattamente all'origine locale e simboli (vale a dire, il debugger deve essere in grado di caricare i valori corretti [(.pbd) i file di simboli ](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). Per impostazione predefinita, questo richiede una build di debug.

Per scenari di debug remoti, è necessario disporre del codice sorgente (o una copia del codice sorgente) già aperto in Visual Studio. I file binari dell'app compilate nel computer remoto devono provenire dalla stessa build perché nel computer locale.

In alcuni scenari di debug locale, è possibile eseguire il debug in Visual Studio senza accesso all'origine se sono presenti App i file di simboli corretto (per impostazione predefinita, è necessaria una build di debug). Per altre informazioni, vedi [specificare file di simboli e origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  
##  <a name="BKMK_Troubleshoot_attach_errors"></a> Risolvere gli errori di connessione  
 I processi in esecuzione a cui il debugger tenta di connettersi possono contenere uno o più tipi di codice. I tipi di codice a cui il debugger può connettersi vengono visualizzati e selezionati nella finestra di dialogo **Seleziona tipo di codice** .  
  
 In alcuni casi il debugger riesce a connettersi a un tipo di codice ma non a un altro. Questa situazione può verificarsi quando si tenta di stabilire una connessione a un processo in esecuzione in un computer remoto, nel quale potrebbero essere stati installati i componenti per il debug remoto solo per alcuni tipi di codice. Può inoltre verificarsi quando si tenta di stabilire una connessione a due o più processi per il debug diretto di un database. Durante il debug SQL è supportata esclusivamente la connessione a un singolo processo.  
  
 Se il debugger è in grado di connettersi solo ad alcuni tipi di codice, verrà visualizzato un messaggio che identifica i tipi per i quali la connessione ha avuto esito negativo.  
  
 Se il debugger riesce a connettersi ad almeno un tipo di codice, è possibile procedere con il debug del processo. Sarà possibile eseguire il debug solo dei tipi di codice con i quali è stata stabilita una connessione. Il messaggio di esempio sopra riportato segnala che non è stato possibile stabilire una connessione al tipo di codice di script. Non sarà quindi possibile eseguire il debug del codice di script nel processo. Il codice di script del processo verrà comunque eseguito, ma non sarà possibile impostare punti di interruzione, visualizzare dati o eseguire altre operazioni di debug nello script.  
  
 Se si desidera ottenere informazioni più specifiche sulla causa che ha impedito al debugger di connettersi a un tipo di codice, è possibile provare a ripetere la connessione solo a quel tipo di codice.  
  
 **Per ottenere informazioni specifiche sul motivo per cui un tipo di codice non è stato possibile collegare**  
  
1.  Disconnettersi dal processo. Scegliere **Disconnetti tutto** dal menu **Debug**.  
  
2.  Riconnettersi al processo, selezionando un solo tipo di codice.  
  
    1.  Nella finestra di dialogo **Connetti a processo** selezionare il processo nell'elenco **Processi disponibili** .  
  
    2.  Fare clic su **Seleziona**.  
  
    3.  Nella finestra di dialogo **Seleziona tipo di codice** selezionare il pulsante di opzione **Esegui il debug di questi tipi di codice** e il tipo di codice per cui si è verificato il problema di connessione. Deselezionare tutti gli altri codici.  
  
    4.  Fare clic su **OK**. La finestra di dialogo **Seleziona tipo di codice** verrà chiusa.  
  
    5.  Nella finestra di dialogo **Connetti a processo** scegliere **Connetti**.  
  
     La connessione non verrà eseguita e verrà visualizzato un messaggio di errore specifico.  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire il debug di più processi](../debugger/debug-multiple-processes.md)   
 [Debug Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Debug remoto](../debugger/remote-debugging.md)