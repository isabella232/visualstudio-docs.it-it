---
title: 'Errore: Il Server Web non è stato possibile trovare la risorsa richiesta | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 798e0892fc78b4ff8f8eb8ed03ee788e4f8f5b25
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53866543"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Errore: Impossibile trovare la risorsa richiesta nel server Web
Ai fini della sicurezza, IIS ha restituito un errore generico.  

Una causa possibile è la configurazione della sicurezza del server. In IIS 6.0 e versioni precedenti veniva utilizzato un programma aggiuntivo, noto come URLScan, per filtrare le richieste sospette e non formattate correttamente. In IIS 7.0 è predefinita una funzionalità di filtro delle richieste. In entrambi i casi, una funzionalità di filtro delle richieste troppo restrittiva può impedire a Visual Studio di eseguire il debug del server.  

Un'altra possibile causa dell'errore è che il servizio W3SVC per IIS non viene avviato. Controllare che questo servizio è stato avviato (grigio) nella finestra Servizi (*Services. msc*).

Esistono numerose altre cause possibili di questo errore. Alcune delle cause più comuni includono un problema di installazione o configurazione di IIS, di configurazione del sito Web o di autorizzazioni nel file system. È possibile provare ad accedere alla risorsa con un browser. A seconda della configurazione di IIS, potrebbe essere necessario utilizzare un browser locale nel server o analizzare il log degli errori di IIS per ottenere un messaggio di errore dettagliato.  
  
 Per altre informazioni sulla risoluzione dei problemi di IIS, vedere [Gestione e amministrazione di IIS](/iis/manage/provisioning-and-managing-iis/iis-management-and-administration).  
  
## <a name="see-also"></a>Vedere anche  
 [Errore: Il verbo DEBUG è bloccato dal server Web, che è stato a sua volta bloccato](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)