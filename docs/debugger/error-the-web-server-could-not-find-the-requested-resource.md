---
description: Ai fini della sicurezza, IIS ha restituito un errore generico.
title: Il server Web non è in grado di trovare la risorsa richiesta | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e3509094e25447cedc6e46d7d811d65c39ea83e1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146613"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Errore: il server Web non è in grado di trovare la risorsa richiesta
Ai fini della sicurezza, IIS ha restituito un errore generico.

Una causa possibile è la configurazione della sicurezza del server. In IIS 6.0 e versioni precedenti veniva utilizzato un programma aggiuntivo, noto come URLScan, per filtrare le richieste sospette e non formattate correttamente. In IIS 7.0 è predefinita una funzionalità di filtro delle richieste. In entrambi i casi, una funzionalità di filtro delle richieste troppo restrittiva può impedire a Visual Studio di eseguire il debug del server.

Un'altra possibile cause di questo errore è che il servizio W3SVC per IIS non è stato avviato. Verificare che il servizio sia stato avviato (disattivato) nella finestra servizi (*Services. msc*).

Questo errore può essere causato da numerose cause aggiuntive. Alcune delle cause più comuni includono un problema di installazione o configurazione di IIS, di configurazione del sito Web o di autorizzazioni nel file system. È possibile provare ad accedere alla risorsa con un browser. A seconda della configurazione di IIS, potrebbe essere necessario utilizzare un browser locale nel server o analizzare il log degli errori di IIS per ottenere un messaggio di errore dettagliato.

 Per altre informazioni sulla risoluzione dei problemi di IIS, vedere [Gestione e amministrazione di IIS](/iis/manage/provisioning-and-managing-iis/iis-management-and-administration).

## <a name="see-also"></a>Vedi anche
- [Errore: il server Web è stato bloccato e blocca il verbo di DEBUG](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)
