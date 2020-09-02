---
title: 'Errore: il server Web non è in grado di trovare la risorsa richiesta | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 1ceeaf30-918c-42bb-ace1-96944530fef3
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 555bb56ee84b7bc48f6b6453c11daef366f97e49
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75845127"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Errore: il server Web non è in grado di trovare la risorsa richiesta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ai fini della sicurezza, IIS ha restituito un errore generico.  
  
 Una causa possibile è la configurazione della sicurezza del server. In IIS 6.0 e versioni precedenti veniva utilizzato un programma aggiuntivo, noto come URLScan, per filtrare le richieste sospette e non formattate correttamente. In IIS 7.0 è predefinita una funzionalità di filtro delle richieste. In entrambi i casi, una funzionalità di filtro delle richieste troppo restrittiva può impedire a Visual Studio di eseguire il debug del server.  
  
 Questo errore può essere avere numerose cause. Alcune delle cause più comuni includono un problema di installazione o configurazione di IIS, di configurazione del sito Web o di autorizzazioni nel file system. È possibile provare ad accedere alla risorsa con un browser. A seconda della configurazione di IIS, potrebbe essere necessario utilizzare un browser locale nel server o analizzare il log degli errori di IIS per ottenere un messaggio di errore dettagliato.  
  
 Per altre informazioni sulla risoluzione dei problemi di IIS, vedere [Gestione e amministrazione di IIS](https://www.iis.net/learn/manage/provisioning-and-managing-iis/iis-management-and-administration).  
  
## <a name="see-also"></a>Vedere anche  
 [Strumento di sicurezza UrlScan](/iis/extensions/working-with-urlscan/urlscan-3-reference)   
 [Errore: il server Web è stato bloccato e blocca il verbo di DEBUG](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)
