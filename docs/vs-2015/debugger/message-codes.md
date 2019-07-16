---
title: I codici di messaggio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 92cc911b0217a406302553b3d913c032fc915b4c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68182956"
---
# <a name="message-codes"></a>Codici di messaggio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ogni riga del messaggio illustrato [visualizzazione messaggi](../debugger/messages-view.md) contiene 'P', del,' del,' o 'R' codice. Tali codici hanno i significati seguenti:  
  
|Codice|Significato|  
|----------|-------------|  
|P|Il messaggio è stato inserito nella coda con il **PostMessage** (funzione). Non sono disponibili informazioni sulla disposizione finale del messaggio.|  
|S|Il messaggio è stato inviato con la **SendMessage** (funzione). Ciò significa che il mittente non nuovamente il controllo fino a quando il ricevitore elabora e restituisce il messaggio. Il ricevitore può, pertanto, passare un valore restituito al mittente.|  
|s|È stato inviato il messaggio, ma che impedisce l'accesso al valore restituito.|  
|R|Della ognuno ' la riga contiene una riga corrispondente di 'R' (return) che elenca il valore restituito del messaggio. In alcuni casi le chiamate al messaggio sono nidificate, ovvero che un gestore di messaggi invia un altro messaggio.|
