---
description: Ai fini della sicurezza, IIS ha restituito un errore generico.
title: Il server Web non è stato in grado di trovare la risorsa richiesta | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 00d59b08a98a66afce7ddbeb5f78d6e5d5f90c0734e74777f9c24cbc8132f98f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121419975"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Errore: il server Web non è in grado di trovare la risorsa richiesta
Ai fini della sicurezza, IIS ha restituito un errore generico.

Una causa possibile è la configurazione della sicurezza del server. In IIS 6.0 e versioni precedenti veniva utilizzato un programma aggiuntivo, noto come URLScan, per filtrare le richieste sospette e non formattate correttamente. In IIS 7.0 è predefinita una funzionalità di filtro delle richieste. In entrambi i casi, una funzionalità di filtro delle richieste troppo restrittiva può impedire a Visual Studio di eseguire il debug del server.

Un'altra possibile causa di questo errore è che il servizio W3SVC per IIS non è stato avviato. Verificare che il servizio sia avviato (in grigio) nella finestra Servizi (*services.msc*).

Esistono numerose possibili cause aggiuntive di questo errore. Alcune delle cause più comuni includono un problema di installazione o configurazione di IIS, di configurazione del sito Web o di autorizzazioni nel file system. È possibile provare ad accedere alla risorsa con un browser. A seconda della configurazione di IIS, potrebbe essere necessario utilizzare un browser locale nel server o analizzare il log degli errori di IIS per ottenere un messaggio di errore dettagliato.

 Per altre informazioni sulla risoluzione dei problemi di IIS, vedere [Gestione e amministrazione di IIS](/iis/manage/provisioning-and-managing-iis/iis-management-and-administration).

## <a name="see-also"></a>Vedi anche
- [Errore: il server Web è stato bloccato e blocca il verbo DEBUG](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)
