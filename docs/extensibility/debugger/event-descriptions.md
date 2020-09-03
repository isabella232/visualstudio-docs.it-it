---
title: Descrizioni degli eventi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3c2582717fd4da3b833da90a951f9b8f72a59f71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738795"
---
# <a name="event-descriptions"></a>Descrizioni degli eventi
Ogni tipo di evento ha uno scopo specifico.

## <a name="events-and-the-reasons-for-their-use"></a>Eventi e motivi per l'uso

|Event|Descrizione|
|-----------|-----------------|
|Attiva eventi documento|Si verifica quando il motore di debug (DE) vuole che l'IDE apra o porti un documento in primo piano.|
|Eventi di errore associati al punto di interruzione o punto di interruzione|Inviato quando un punto di interruzione è associato o quando un punto di interruzione non può essere associato e viene restituito un errore.|
|Eventi non associati al punto di interruzione|Si verifica quando un punto di interruzione associato Annulla il binding dal codice.|
|Può arrestare gli eventi|Inviato all'IDE per determinare se l'utente desidera arrestare in corrispondenza di un punto specificato nel codice.|
|Eventi punto di interruzione|Si verificano quando viene raggiunto un punto di interruzione di codice o di dati.|
|Eventi testo documento|Si verificano quando viene modificato il testo in un documento. Questi eventi non vengono inviati tramite il `IDebugEventCallBack2::Event` metodo.|
|Eventi di creazione del motore|Inviato quando un motore viene creato per la prima volta.|
|Eventi punto di ingresso|Inviato quando il programma di cui è in corso il debug ha eseguito il codice di inizializzazione e ha raggiunto il primo punto di ingresso dell'utente.|
|Eventi eccezione|Inviato quando un programma in esecuzione raggiunge un'eccezione.|
|Eventi di completamento della valutazione delle espressioni|Inviato quando la valutazione dell'espressione asincrona è completata.|
|Trova eventi simbolo|Inviato ogni volta che il DE deve chiedere all'utente di trovare i simboli per un modulo.|
|Eventi di caricamento completo|Inviato solo quando il caricamento iniziale del programma è completato e il primo codice sta per essere eseguito nel programma.|
|Eventi di messaggio|Inviato quando i messaggi vengono inviati agli utenti.|
|Eventi di caricamento del modulo|Inviato quando viene caricato o scaricato un nuovo modulo.|
|Eventi stringa di output|Inviato quando il programma scrive l'output di debug.|
|Creazione ed eliminazione di eventi|Inviato per annunciare la creazione o l'eliminazione di processi, programmi, proprietà, sessioni e thread in modo che l'IDE di Visual Studio possa tenere traccia dello stato dei programmi di cui è in corso il debug.|
|Eventi di completamento del passaggio|Inviato quando un passaggio viene completato.|
|Eventi di modifica del nome del thread|Inviato quando l'utente modifica il nome di un thread.|
|Eventi di modifica del nome del programma|Inviato quando l'utente modifica il nome di un programma.|

## <a name="see-also"></a>Vedere anche
- [Invio di eventi](../../extensibility/debugger/sending-events.md)
