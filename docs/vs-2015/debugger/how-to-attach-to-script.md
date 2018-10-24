---
title: 'Procedura: connettersi a file Script | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- script debugging, attaching to script
- script, attaching to
- processes, attaching to script
- remote debugging, attaching to script
ms.assetid: 82013e9a-ef53-4fd2-b451-a6891cdc6307
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 08a82442d4e7eed160c6ec83d67c498073b42ac9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49852557"
---
# <a name="how-to-attach-to-script"></a>Procedura: connettersi a file script
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questo argomento viene illustrato come connettere manualmente il debugger di Visual Studio a un file script per l'esecuzione del debug.  
  
### <a name="to-attach-to-a-running-process"></a>Per connettersi a un processo in esecuzione  
  
1. Scegliere **Connetti a processo** dal menu **Debug**. (Se è aperto alcun progetto, scegliere **Connetti a processo** nel **Tools** menu.)  
  
2. Nel **Connetti a processo** della finestra di dialogo esaminare le **processi disponibili** elenco e individuare il processo di script si desidera stabilire una connessione. È possibile identificare i processi di script esaminando la **tipo** colonna.  
  
   1.  Se il processo di cui si desidera eseguire il debug è in esecuzione in un altro computer, sarà necessario innanzitutto selezionare il computer remoto. Per altre informazioni, vedere [procedura: selezionare un Computer remoto](http://msdn.microsoft.com/en-us/4332ba8e-2f0b-4f62-b96a-e762b9f3c3ba).  
  
   2.  Se il processo viene eseguito con un account utente diverso, selezionare la casella di controllo **Mostra processi di tutti gli utenti** .  
  
   3.  Se si è connessi tramite **connessione Desktop remoto**, selezionare la **Mostra processi in tutte le sessioni** casella di controllo.  
  
3. Fare clic sul processo al quale ci si desidera connettere.  
  
4. Nel **collegare a** casella, dovrebbe essere **codice Script** oppure **automatico: codice Script**. Se viene visualizzata una voce diversa, attenersi alla seguente procedura:  
  
   1.  Fare clic su **Seleziona**.  
  
   2.  Nel **Seleziona tipo di codice** finestra di dialogo, fare clic su **eseguire il Debug di questi tipi di codice** e selezionare **Script**.  
  
   3.  Fare clic su **OK**.  
  
5. Scegliere **Connetti**.  
  
    A questo punto, è possibile che venga visualizzato un avviso in cui viene comunicato che il debug degli script è disabilitato in Internet Explorer. In tal caso, vedere [avviso: debug degli Script disabilitato](../debugger/warning-script-debugging-disabled.md).  
  
   L'elenco **Processi disponibili** viene visualizzato automaticamente quando si apre la finestra di dialogo **Processi** . I processi possono essere avviati e interrotti in background mentre la finestra di dialogo è aperta. È quindi possibile che il contenuto non sia sempre aggiornato. È possibile aggiornare l'elenco in qualsiasi momento per visualizzare l'elenco corrente dei processi, premere il **Aggiorna** pulsante.  
  
   Durante l'esecuzione del debug è possibile essere connessi a più di un programma, ma in un dato momento solo uno di tali programmi potrà essere attivo nel debugger. È possibile impostare il programma attivo nella barra degli strumenti Posizione di debug. Per altre informazioni, vedere [procedura: impostare il processo corrente](http://msdn.microsoft.com/en-us/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).  
  
   Tutti i **Debug** i comandi di menu esecuzione interessano il programma attivo. È possibile interrompere qualsiasi programma sottoposto a debug dalla finestra di dialogo processi. Visualizzare [usando i punti di interruzione](../debugger/using-breakpoints.md).  
  
> [!NOTE]
>  Se si tenta di connettersi a un processo appartenente a un account utente non attendibile, verrà visualizzata una finestra di dialogo contenente un avviso di sicurezza per chiedere conferma dell'operazione. Per altre informazioni, vedere [avviso di sicurezza: connessione a un processo appartenente a un utente non attendibile può essere pericolosa. Se le informazioni seguenti risultano sospette o non si è certi, non stabilire la connessione al processo](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md).  
  
 In alcuni casi, quando viene eseguito il debug in una sessione di Servizi terminal (Desktop remoto), nell'elenco Processi disponibili non vengono visualizzati tutti i processi disponibili. Se in [!INCLUDE[WinXPSvr](../includes/winxpsvr-md.md)] o versioni più recenti si esegue Visual Studio come utente con limitazioni, nell'elenco Processi disponibili non verranno visualizzati i processi in esecuzione nella Sessione 0, utilizzata per i servizi e gli altri processi del server tra cui w3wp.exe. È possibile risolvere il problema eseguendo Visual Studio con un account di amministratore o dalla console del server invece di una sessione di Servizi Terminal. Se nessuna di queste soluzioni alternative è possibile, una terza opzione consiste nel connettersi al processo digitando vsjitdebugger.exe -p IDProcesso dalla riga di comando di Windows. È possibile determinare l'ID processo utilizzando tlist.exe. Per ottenere tlist.exe, scaricare e installare gli strumenti di debug per Windows, disponibile all'indirizzo [Centro sviluppatori di Hardware Windows](http://go.microsoft.com/fwlink/?linkid=1651).  
  
## <a name="see-also"></a>Vedere anche  
 [Debug degli Script lato client](../debugger/client-side-script-debugging.md)   
 [Collegamento a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Avviso di sicurezza: la connessione a un processo appartenente a un utente non attendibile può essere pericolosa. Se le informazioni seguenti risultano sospette o non si è certi, non stabilire la connessione al processo](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)



