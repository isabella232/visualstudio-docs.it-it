---
title: Limitazioni del debug di WCF | Microsoft Docs
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
- debugging, WCF
- WCF, debugging limitations
ms.assetid: 8e0333c4-1ddc-4abe-8f1c-d19bf6a2a07a
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c1d569712547144067cbfcfd894e31e1b41964e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798314"
---
# <a name="limitations-on-wcf-debugging"></a>Limitazioni del debug di WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sono disponibili tre modalità per avviare il debug di un servizio WCF:  
  
- Si esegue il debug di un processo client che chiama un servizio. Il debugger esegue le istruzioni del servizio. Il servizio non deve essere presente nella stessa soluzione dell'applicazione client.  
  
- Si esegue il debug di un processo client che effettua una richiesta a un servizio. Il servizio deve essere parte della soluzione.  
  
- Si utilizza **Connetti a processo** per connettersi a un servizio che è attualmente in esecuzione. Il debug inizia all'interno del servizio.  
  
  In questo argomento vengono descritte le limitazioni di questi scenari.  
  
## <a name="limitations-on-stepping-into-a-service"></a>Limitazioni dell'esecuzione di istruzioni in un servizio  
 Per eseguire istruzioni in un servizio da un'applicazione client di cui si esegue il debug, è necessario soddisfare le seguenti condizioni:  
  
-   Il client deve chiamare il servizio utilizzando un oggetto client sincrono.  
  
-   L'operazione del contratto non può essere unidirezionale.  
  
-   Se il server è asincrono, non è possibile visualizzare lo stack di chiamate completo durante l'esecuzione del codice nel servizio.  
  
-   È necessario abilitare il debug con il codice riportato di seguito nel file app.config o web.config:  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    </system.web>  
    ```  
  
     È necessario aggiungere questo codice solo una volta. È possibile aggiungere questo codice modificando il file con estensione config o tramite il collegamento al servizio utilizzando **Connetti a processo**. Quando si usa **Connetti a processo** in un servizio, il codice di debug viene aggiunto automaticamente al file config. Successivamente, è possibile eseguire il debug e le istruzioni nel servizio senza dover modificare il file config.  
  
## <a name="limitations-on-stepping-out-of-a-service"></a>Limitazioni dell'uscita da un servizio  
 L'uscita da un servizio e il ritorno al client presenta le stesse limitazioni descritte per l'esecuzione delle istruzioni di un servizio. Inoltre, il debugger deve essere connesso al client. Se è in corso il debug di un client e l'esecuzione di istruzioni in un servizio, il debugger rimane connesso al servizio. Ciò vale se è stata avviata il client utilizzando **Avvia debug** o connesso al client tramite **Connetti a processo**. Se il debug è stato avviato mediante la connessione al servizio, il debugger non è ancora connesso al client. In tal caso, se è necessario uscire dal servizio e al client, è innanzitutto necessario utilizzare **Connetti a processo** collegare manualmente al client.  
  
## <a name="limitations-on-automatic-attach-to-a-service"></a>Limitazioni della connessione automatica a un servizio  
 La connessione automatica a un servizio presenta le limitazioni riportate di seguito:  
  
-   Il servizio deve essere parte della soluzione [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] di cui si esegue il debug.  
  
-   Il servizio deve essere ospitato. Può essere parte di un progetto di sito Web (File system e HTTP), un progetto di applicazione Web (File system e HTTP) o un progetto di libreria di servizi WCF. I progetti di libreria di servizi WCF possono essere librerie di servizi o librerie di servizi di flusso di lavoro.  
  
-   Il servizio deve essere richiamato da un client WCF.  
  
-   È necessario abilitare il debug con il codice riportato di seguito nel file app.config o web.config:  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    <system.web>  
    ```  
  
## <a name="self-hosting"></a>Self-hosting  
 Oggetto *servizio indipendente* è un servizio WCF che non viene eseguito in IIS, l'Host del servizio WCF o [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Development Server. Per informazioni su come eseguire il debug di un servizio self-hosted, vedere [procedura: eseguire il Debug di un servizio WCF Self-Hosted](../debugger/how-to-debug-a-self-hosted-wcf-service.md).  
  
## <a name="self-hosting"></a>Self-hosting  
 Per abilitare il debug di [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 3.0 o 3.5 applicazioni [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 3.0 o 3.5 deve essere installato prima [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] è installato. Se [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] viene installato prima [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 3.0 o 3.5, si verifica un errore quando si prova a eseguire il debug un [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] applicazione 3.0 o 3.5. Il messaggio di errore è "Impossibile eseguire automaticamente l'istruzione sul server". Per risolvere questo problema, utilizzare il Windows **Pannello di controllo**, **programmi e funzionalità** ripristinare il [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] installazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug dei servizi WCF](../debugger/debugging-wcf-services.md)   
 [Procedura: Eseguire il debug di un servizio WCF indipendente](../debugger/how-to-debug-a-self-hosted-wcf-service.md)



