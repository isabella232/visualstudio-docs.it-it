---
title: Profilatura e sicurezza in Windows Vista | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 736e7a04813a6c56d6cab6d1886171e321d583cb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532377"
---
# <a name="profiling-and-windows-vista-security"></a>Profilatura e sicurezza in Windows Vista
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [profilatura e sicurezza in Windows Vista](https://docs.microsoft.com/visualstudio/profiling/profiling-and-windows-vista-security).  
  
A seconda delle impostazioni delle autorizzazioni di accesso utente di [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)] rese disponibili dall'amministratore di un computer, un singolo utente potrebbe disporre dell'autorizzazione di sicurezza necessaria per profilare un processo in quel computer. Gli esempi seguenti illustrano le possibili differenze tra i diversi tipi di utenti:  
  
-   Se l'amministratore ha impostato l'avvio del driver e del servizio, alcuni utenti possono accedere a funzionalità di profilatura avanzate.  
  
-   Gli utenti di dominio possono accedere soltanto ad esempi di profilatura.  
  
-   Alcuni utenti possono negare l'accesso alla profilatura a tutti gli altri utenti.  
  
 Per altre informazioni, vedere le opzioni ADMIN in [VSPerfCmd](../profiling/vsperfcmd.md).  
  
## <a name="cross-session-profiling"></a>Profilatura tra sessioni  
 La *profilatura tra sessioni* è una funzionalità per la profilatura di un processo eseguito in una sessione di accesso differente. Ad esempio, la maggior parte dei servizi viene eseguita nella sessione 0 e gli utenti non possono effettuare esecuzioni direttamente nella sessione 0. Usando il pulsante **Connetti a processo** nella barra degli strumenti di Esplora prestazioni o l'opzione /attach dello strumento della riga di comando VSPerfCmd, è possibile profilare la maggior parte dei processi nelle diverse sessioni di accesso.  
  
 È possibile visualizzare un elenco dei processi disponibili impostando le opzioni di visibilità relative alla profilatura tra processi. Queste opzioni sono disponibili nella finestra **Connetti a processo** visualizzata quando si fa clic su **Connetti a processo**:  
  
-   **Mostra i processi di tutti gli utenti**  
  
     Quando questa opzione non è selezionata, nell'elenco vengono visualizzati solo i processi di proprietà dell'utente corrente. Quando si seleziona **Mostra i processi di tutti gli utenti**, nell'elenco vengono visualizzati i processi di tutti gli utenti.  
  
-   **Mostra processi in tutte le sessioni**  
  
     Quando questa opzione non è selezionata, nell'elenco vengono visualizzati i processi nella sessione corrente. Quando questa opzione è selezionata, nell'elenco vengono visualizzati i processi in tutte le sessioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramiche](../profiling/overviews-performance-tools.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Procedura: eseguire la connessione a un processo in esecuzione](http://msdn.microsoft.com/en-us/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)



