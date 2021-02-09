---
title: Codici messaggi | Microsoft Docs
description: Informazioni sul significato dei codici di messaggio visualizzati in ogni riga di messaggio della visualizzazione messaggi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 92562dda3e8a705d2cdf9b00561aa13cbd9d75e5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891774"
---
# <a name="message-codes"></a>Codici di messaggio
Ogni riga di messaggio visualizzata nella [visualizzazione messaggi](../debugger/messages-view.md) contiene un codice "P", "s", "o" R ". Questi codici hanno i significati seguenti:

|Codice|Significato|
|----------|-------------|
|P|Il messaggio è stato inserito nella coda con la funzione **PostMessage** . Non sono disponibili informazioni relative alla disposizione definitiva del messaggio.|
|S|Il messaggio è stato inviato con la funzione **SendMessage** . Ciò significa che il mittente non acquisisce il controllo finché il ricevitore non elabora e non restituisce il messaggio. Il ricevitore può quindi passare un valore restituito al mittente.|
|s|Il messaggio è stato inviato, ma la sicurezza impedisce l'accesso al valore restituito.|
|R|La riga di ogni ' s ha una riga ' R ' (Return) corrispondente che elenca il valore restituito del messaggio. Talvolta le chiamate di messaggio sono annidate, il che significa che un gestore di messaggi invia un altro messaggio.|