---
title: 'Errore: Il Server Web è stato bloccato e blocca il verbo DEBUG | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.webdbg_debug_verb_blocked
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 277619cb89003aea9dca58678f251f2f21826046
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55026593"
---
# <a name="error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb"></a>Errore: Il verbo DEBUG è bloccato dal server Web, che è stato a sua volta bloccato
L'accesso a un'applicazione Web o a un servizio Web XML non è riuscito in quanto è stato eseguito lo strumento di blocco IIS ed è stato installato e attivato URLScan. Questa condizione impedisce la ricezione del verbo DEBUG da parte di IIS.  
  
 URLScan è uno strumento di sicurezza che viene utilizzato con lo strumento di blocco IIS per fornire agli amministratori di siti Web IIS la capacità di disattivare le funzionalità non necessarie e limitare il tipo di richieste HTTP che verranno elaborate dal server. Bloccando richieste HTTP specifiche, lo strumento di sicurezza URLScan impedisce a richieste potenzialmente dannose di raggiungere il server e causare danni.  
  
 Se l'applicazione viene eseguita in IIS 6.0 in Windows Server 2003, non è necessario eseguire lo strumento di blocco IIS perché IIS 6.0 fornisce la stessa funzionalità.  
  
### <a name="to-enable-debugging-on-a-web-server-with-urlscan-installed"></a>Per attivare il debug su un server Web con URLScan installato  
  
1.  Individuare il file Urlscan.ini. In genere è presente in una directory simile a quella indicata di seguito.  
  
     C:\WINNT\System32\Inetsrv\urlscan  
  
2.  Creare una copia del file e assegnarvi il nome **Urlscan.old**.  
  
3.  Aprire la copia originale del file Urlscan.ini mediante il Blocco note o l'editore di testo desiderato.  
  
4.  In Urlscan.ini individuare la sezione [AllowVerbs]. Aggiungere DEBUG alla sezione [AllowVerbs]. Se è presente la stringa ;DEBUG nella sezione [AllowVerbs], e il punto e virgola per rimuovere il commento dal verbo.  
  
5.  Individuare la sezione [DenyVerbs]. Rimuovere DEBUG, se è presente nella sezione [DenyVerbs].  
  
6.  Salvare il file.  
  
7.  Riavviare il server o IIS.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni Web: Errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Errore: Impossibile trovare la risorsa richiesta nel server Web](../debugger/error-the-web-server-could-not-find-the-requested-resource.md)