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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4b836a5d4c1faad6b4c0375e2ec51d759816889
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903610"
---
# <a name="message-codes"></a>Codici di messaggio
Ogni riga di messaggio visualizzata nella [visualizzazione messaggi](../debugger/messages-view.md) contiene un codice "P", "s", "o" R ". Questi codici hanno i significati seguenti:

|Codice|Significato|
|----------|-------------|
|P|Il messaggio è stato inserito nella coda con la funzione **PostMessage** . Non sono disponibili informazioni relative alla disposizione definitiva del messaggio.|
|S|Il messaggio è stato inviato con la funzione **SendMessage** . Ciò significa che il mittente non acquisisce il controllo finché il ricevitore non elabora e non restituisce il messaggio. Il ricevitore può quindi passare un valore restituito al mittente.|
|s|Il messaggio è stato inviato, ma la sicurezza impedisce l'accesso al valore restituito.|
|R|La riga di ogni ' s ha una riga ' R ' (Return) corrispondente che elenca il valore restituito del messaggio. Talvolta le chiamate di messaggio sono annidate, il che significa che un gestore di messaggi invia un altro messaggio.|