---
title: Codici di messaggio | Microsoft Docs
description: Informazioni sui significati dei codici di messaggio visualizzati in ogni riga di messaggio della visualizzazione Messaggi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ce6fe678785719ed52e9be59e28d7eedd98ebef6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146836"
---
# <a name="message-codes"></a>Codici di messaggio
Ogni riga di messaggio visualizzata [nella visualizzazione Messaggi](../debugger/messages-view.md) contiene un codice "P", "S", "s" o "R". Questi codici hanno i significati seguenti:

|Codice|Significato|
|----------|-------------|
|P|Il messaggio è stato inviato alla coda con la **funzione PostMessage.** Non sono disponibili informazioni relative alla disposizione finale del messaggio.|
|S|Il messaggio è stato inviato con **la funzione SendMessage.** Ciò significa che il mittente non recupera il controllo fino a quando il ricevitore non elabora e restituisce il messaggio. Il ricevitore può quindi passare un valore restituito al mittente.|
|s|Il messaggio è stato inviato, ma la sicurezza impedisce l'accesso al valore restituito.|
|R|Ogni riga 'S' ha una riga 'R' (restituita) corrispondente che elenca il valore restituito del messaggio. A volte le chiamate ai messaggi sono annidate, il che significa che un gestore di messaggi invia un altro messaggio.|