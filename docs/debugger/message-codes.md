---
title: I codici di messaggio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7c1f568ead3e5862460d4ae4e18e51687737d4a5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53866296"
---
# <a name="message-codes"></a>Codici di messaggio
Ogni riga del messaggio illustrato [visualizzazione messaggi](../debugger/messages-view.md) contiene 'P', del,' del,' o 'R' codice. Tali codici hanno i significati seguenti:  
  
|Codice|Significato|  
|----------|-------------|  
|P|Il messaggio è stato inserito nella coda con il **PostMessage** (funzione). Non sono disponibili informazioni sulla disposizione finale del messaggio.|  
|S|Il messaggio è stato inviato con la **SendMessage** (funzione). Ciò significa che il mittente non nuovamente il controllo fino a quando il ricevitore elabora e restituisce il messaggio. Il ricevitore può, pertanto, passare un valore restituito al mittente.|  
|s|È stato inviato il messaggio, ma che impedisce l'accesso al valore restituito.|  
|R|Della ognuno ' la riga contiene una riga corrispondente di 'R' (return) che elenca il valore restituito del messaggio. In alcuni casi le chiamate al messaggio sono nidificate, ovvero che un gestore di messaggi invia un altro messaggio.|