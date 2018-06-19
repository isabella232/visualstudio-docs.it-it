---
title: 'Errore: Il Server Web Impossibile trovare la risorsa richiesta | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 1e6fec89a151525a84349b7019c7569eb752172e
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2018
ms.locfileid: "34454316"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Errore: il server Web non è in grado di trovare la risorsa richiesta
Ai fini della sicurezza, IIS ha restituito un errore generico.  
  
 Una causa possibile è la configurazione della sicurezza del server. In IIS 6.0 e versioni precedenti veniva utilizzato un programma aggiuntivo, noto come URLScan, per filtrare le richieste sospette e non formattate correttamente. In IIS 7.0 è predefinita una funzionalità di filtro delle richieste. In entrambi i casi, una funzionalità di filtro delle richieste troppo restrittiva può impedire a Visual Studio di eseguire il debug del server.  
  
 Questo errore può essere avere numerose cause. Alcune delle cause più comuni includono un problema di installazione o configurazione di IIS, di configurazione del sito Web o di autorizzazioni nel file system. È possibile provare ad accedere alla risorsa con un browser. A seconda della configurazione di IIS, potrebbe essere necessario utilizzare un browser locale nel server o analizzare il log degli errori di IIS per ottenere un messaggio di errore dettagliato.  
  
 Per ulteriori informazioni sulla risoluzione dei problemi di IIS, vedere [Gestione IIS e amministrazione](/iis/manage/provisioning-and-managing-iis/iis-management-and-administration).  
  
## <a name="see-also"></a>Vedere anche  
 [Errore: il server Web è stato bloccato e blocca il verbo DEBUG](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)