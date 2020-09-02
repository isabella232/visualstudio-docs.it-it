---
title: 'Procedura: connettersi allo script | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 719654916087e7c7f4249ff52abbed628a2c56a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704504"
---
# <a name="how-to-attach-to-script"></a>Procedura: connettersi a file script
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questo argomento viene illustrato come connettere manualmente il debugger di Visual Studio a un file script per l'esecuzione del debug.  
  
### <a name="to-attach-to-a-running-process"></a>Per connettersi a un processo in esecuzione  
  
1. Scegliere **Connetti a processo** dal menu **Debug**. Se non è aperto alcun progetto, scegliere **Connetti a processo** dal menu **Strumenti**.  
  
2. Nella finestra di dialogo **Connetti a processo** analizzare l'elenco **Processi disponibili** e individuare il processo di script al quale ci si desidera connettere. È possibile identificare i processi di script esaminando la colonna **Tipo**.  
  
   1. Se il processo di cui si desidera eseguire il debug è in esecuzione in un altro computer, sarà necessario innanzitutto selezionare il computer remoto. Per ulteriori informazioni, vedere [procedura: selezionare un computer remoto](https://msdn.microsoft.com/4332ba8e-2f0b-4f62-b96a-e762b9f3c3ba).  
  
   2. Se il processo viene eseguito con un account utente diverso, selezionare la casella di controllo **Mostra processi di tutti gli utenti** .  
  
   3. Se la connessione è stata effettuata mediante **Connessione desktop remoto**, selezionare la casella di controllo **Mostra processi in tutte le sessioni**.  
  
3. Fare clic sul processo al quale ci si desidera connettere.  
  
4. Nel **Collega a** casella, si noterà **codice Script** o **automatico: Codice script**. Se viene visualizzata una voce diversa, attenersi alla seguente procedura:  
  
   1. Fare clic su **Seleziona**.  
  
   2. Nella finestra di dialogo **Seleziona tipo di codice** fare clic su **Esegui il debug di questi tipi di codice** e selezionare **Script**.  
  
   3. Fare clic su **OK**.  
  
5. Scegliere **Connetti**.  
  
    A questo punto, è possibile che venga visualizzato un avviso in cui viene comunicato che il debug degli script è disabilitato in Internet Explorer. Se si verifica questa situazione, vedere [Warning: debug di script disabilitato](../debugger/warning-script-debugging-disabled.md).  
  
   L'elenco **Processi disponibili** viene visualizzato automaticamente quando si apre la finestra di dialogo **Processi** . I processi possono essere avviati e interrotti in background mentre la finestra di dialogo è aperta. È quindi possibile che il contenuto non sia sempre aggiornato. Per visualizzare i processi correnti, è possibile aggiornare l'elenco in qualsiasi momento utilizzando il pulsante **Aggiorna**.  
  
   Durante l'esecuzione del debug è possibile essere connessi a più di un programma, ma in un dato momento solo uno di tali programmi potrà essere attivo nel debugger. È possibile impostare il programma attivo nella barra degli strumenti Posizione di debug. Per altre informazioni, vedere [procedura: impostare il processo corrente](https://msdn.microsoft.com/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).  
  
   Tutti i comandi di esecuzione del menu **Debug** hanno effetto sul programma attivo. È possibile interrompere qualsiasi programma sottoposto a debug dalla finestra di dialogo processi. Vedere [utilizzo](../debugger/using-breakpoints.md)di punti di interruzione.  
  
> [!NOTE]
> Se si tenta di connettersi a un processo appartenente a un account utente non attendibile, verrà visualizzata una finestra di dialogo contenente un avviso di sicurezza per chiedere conferma dell'operazione. Per altre informazioni, vedere [avviso di sicurezza: La connessione a un processo appartenente a un utente non attendibile può essere pericolosa. Se le informazioni seguenti sono sospette o non si è certi della loro provenienza e del loro stato, non connettersi al processo](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015).  
  
 In alcuni casi, quando viene eseguito il debug in una sessione di Servizi terminal (Desktop remoto), nell'elenco Processi disponibili non vengono visualizzati tutti i processi disponibili. Se in [!INCLUDE[WinXPSvr](../includes/winxpsvr-md.md)] o versioni più recenti si esegue Visual Studio come utente con limitazioni, nell'elenco Processi disponibili non verranno visualizzati i processi in esecuzione nella Sessione 0, utilizzata per i servizi e gli altri processi del server tra cui w3wp.exe. È possibile risolvere il problema eseguendo Visual Studio con un account di amministratore o dalla console del server invece di una sessione di Servizi Terminal. Se non è possibile adottare una di queste soluzioni alternative, una terza opzione consiste nel connettersi al processo digitando vsjitdebugger.exe -p IDProcesso dalla riga di comando di Windows. È possibile determinare l'ID processo utilizzando tlist.exe. Per ottenere tlist.exe, scaricare e installare gli strumenti di debug per Windows disponibili sul sito [Centro sviluppatori Windows - Hardware](https://developer.microsoft.com/windows/hardware).  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di script sul lato client](../debugger/client-side-script-debugging.md)   
 [Connetti a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Avviso di sicurezza: la connessione a un processo di proprietà di un utente non attendibile può essere pericolosa. Se le informazioni seguenti sono sospette o non sono sicure, non connettersi a questo processo](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015)   
 [Sicurezza del debugger](../debugger/debugger-security.md)
