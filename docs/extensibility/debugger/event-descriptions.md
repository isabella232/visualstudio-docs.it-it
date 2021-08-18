---
title: Descrizioni degli eventi | Microsoft Docs
description: Informazioni sui tipi di eventi e sui motivi dell'uso. Ogni tipo di evento ha uno scopo specifico.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 4a9aae8668bbe2b0a92524ccfc5d8d0d18565fd80ea1a7dec2211f47e37f179d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121342804"
---
# <a name="event-descriptions"></a>Descrizioni degli eventi
Ogni tipo di evento ha uno scopo specifico.

## <a name="events-and-the-reasons-for-their-use"></a>Eventi e motivi per il loro uso

|Event|Descrizione|
|-----------|-----------------|
|Attivare gli eventi del documento|Si verifica quando il motore di debug (DE) vuole che l'IDE a open o portare un documento in primo piano.|
|Eventi di errore associati a un punto di interruzione o un punto di interruzione|Inviato quando un punto di interruzione è associato o quando non è possibile associare un punto di interruzione e viene restituito un errore.|
|Eventi non associati ai punti di interruzione|Si verifica quando un punto di interruzione associato viene dissociato dal codice.|
|Può arrestare gli eventi|Inviato all'IDE per determinare se l'utente vuole arrestarsi in corrispondenza di un punto specificato nel codice.|
|Eventi dei punti di interruzione|Si verifica quando viene raggiunto un punto di interruzione del codice o dei dati.|
|Eventi di testo del documento|Si verifica quando il testo di un documento viene modificato. Questi eventi non vengono inviati tramite il `IDebugEventCallBack2::Event` metodo .|
|Eventi di creazione del motore|Inviato alla prima creazione di un motore.|
|Eventi del punto di ingresso|Inviato quando il programma in fase di debug ha eseguito il codice di inizializzazione e ha raggiunto il primo punto di ingresso utente.|
|Eventi di eccezione|Inviato quando un programma in esecuzione raggiunge un'eccezione.|
|Eventi di completamento della valutazione delle espressioni|Inviato al termine della valutazione asincrona delle espressioni.|
|Trovare eventi di simboli|Inviato ogni volta che il DE deve chiedere all'utente di trovare i simboli per un modulo.|
|Caricare gli eventi completi|Inviato solo quando il caricamento iniziale del programma è completo e il primo codice sta per essere eseguito nel programma.|
|Eventi di messaggio|Inviato quando vengono inviati messaggi agli utenti.|
|Eventi di caricamento dei moduli|Inviato quando un nuovo modulo viene caricato o scaricato.|
|Eventi di stringa di output|Inviato quando il programma scrive l'output di debug.|
|Creare ed eliminare eventi|Inviato per annunciare la creazione o la distruzione di processi, programmi, proprietà, sessioni e thread in modo che l'IDE di Visual Studio possa tenere traccia dello stato dei programmi in fase di debug.|
|Eventi di completamento del passaggio|Inviato al termine di un passaggio.|
|Eventi di modifica del nome del thread|Inviato quando l'utente modifica il nome di un thread.|
|Eventi di modifica del nome del programma|Inviato quando l'utente modifica il nome di un programma.|

## <a name="see-also"></a>Vedi anche
- [Invio di eventi](../../extensibility/debugger/sending-events.md)
