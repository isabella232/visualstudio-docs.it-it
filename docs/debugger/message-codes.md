---
title: I codici di messaggio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3899da3b668406a701ce5c1c4935b531754d10e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55017084"
---
# <a name="message-codes"></a>Codici di messaggio
Ogni riga del messaggio illustrato [visualizzazione messaggi](../debugger/messages-view.md) contiene 'P', del,' del,' o 'R' codice. Tali codici hanno i significati seguenti:  
  
|Codice|Significato|  
|----------|-------------|  
|P|Il messaggio è stato inserito nella coda con il **PostMessage** (funzione). Non sono disponibili informazioni sulla disposizione finale del messaggio.|  
|S|Il messaggio è stato inviato con la **SendMessage** (funzione). Ciò significa che il mittente non nuovamente il controllo fino a quando il ricevitore elabora e restituisce il messaggio. Il ricevitore può, pertanto, passare un valore restituito al mittente.|  
|s|È stato inviato il messaggio, ma che impedisce l'accesso al valore restituito.|  
|R|Della ognuno ' la riga contiene una riga corrispondente di 'R' (return) che elenca il valore restituito del messaggio. In alcuni casi le chiamate al messaggio sono nidificate, ovvero che un gestore di messaggi invia un altro messaggio.|