---
title: I codici di messaggio | Microsoft Docs
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
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d995a884b8d223a4415549739c9701fd72886a56
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517322"
---
# <a name="message-codes"></a>Codici di messaggio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [codici di messaggio](https://docs.microsoft.com/visualstudio/debugger/message-codes).  
  
Ogni riga del messaggio illustrato [visualizzazione messaggi](../debugger/messages-view.md) contiene 'P', del,' del,' o 'R' codice. Tali codici hanno i significati seguenti:  
  
|Codice|Significato|  
|----------|-------------|  
|P|Il messaggio è stato inserito nella coda con il **PostMessage** (funzione). Non sono disponibili informazioni sulla disposizione finale del messaggio.|  
|S|Il messaggio è stato inviato con la **SendMessage** (funzione). Ciò significa che il mittente non nuovamente il controllo fino a quando il ricevitore elabora e restituisce il messaggio. Il ricevitore può, pertanto, passare un valore restituito al mittente.|  
|s|È stato inviato il messaggio, ma che impedisce l'accesso al valore restituito.|  
|R|Della ognuno ' la riga contiene una riga corrispondente di 'R' (return) che elenca il valore restituito del messaggio. In alcuni casi le chiamate al messaggio sono nidificate, ovvero che un gestore di messaggi invia un altro messaggio.|



