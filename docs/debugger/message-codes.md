---
title: Codici messaggi | Microsoft Docs
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
ms.openlocfilehash: 1c09245056bf7e947985bfa55dc9cc4a3a96b8cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62846273"
---
# <a name="message-codes"></a>Codici di messaggio
Ogni riga di messaggio visualizzata nella [visualizzazione messaggi](../debugger/messages-view.md) contiene un codice "P", "s", "o" R ". Questi codici hanno i significati seguenti:

|Codice|Significato|
|----------|-------------|
|P|Il messaggio è stato inserito nella coda con la funzione **PostMessage** . Non sono disponibili informazioni relative alla disposizione definitiva del messaggio.|
|S|Il messaggio è stato inviato con la funzione **SendMessage** . Ciò significa che il mittente non acquisisce il controllo finché il ricevitore non elabora e non restituisce il messaggio. Il ricevitore può quindi passare un valore restituito al mittente.|
|s|Il messaggio è stato inviato, ma la sicurezza impedisce l'accesso al valore restituito.|
|R|La riga di ogni ' s ha una riga ' R ' (Return) corrispondente che elenca il valore restituito del messaggio. Talvolta le chiamate di messaggio sono annidate, il che significa che un gestore di messaggi invia un altro messaggio.|