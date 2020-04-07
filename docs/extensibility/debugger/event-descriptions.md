---
title: Descrizioni degli eventi Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738795"
---
# <a name="event-descriptions"></a>Descrizioni degli eventi
Ogni tipo di evento ha uno scopo specifico.

## <a name="events-and-the-reasons-for-their-use"></a>Eventi e le ragioni del loro utilizzo

|Event|Descrizione|
|-----------|-----------------|
|Attivare gli eventi del documento|Si verifica quando il motore di debug (DE) desidera che l'IDE per aprire o portare un documento in primo piano.|
|Eventi di errore associati a punti di interruzione o punti di interruzione|Inviato quando un punto di interruzione è associato o quando un punto di interruzione non può essere associato e viene restituito un errore.|
|Eventi non associati ai punti di interruzione|Si verifica quando un punto di interruzione associato viene dissociato dal codice.|
|Può fermare gli eventi|Inviato all'IDE per determinare se l'utente desidera interrompere in un punto specificato nel codice.|
|Eventi punto di interruzione|Si verifica quando viene raggiunto un codice o un punto di interruzione di dati.|
|Eventi di testo del documento|Si verifica quando il testo in un documento viene modificato. Questi eventi non vengono `IDebugEventCallBack2::Event` inviati tramite il metodo .|
|Eventi di creazione del motoreEngine create events|Inviato quando un motore viene creato per la prima volta.|
|Eventi del punto di ingresso|Inviato quando il programma in fase di debug ha eseguito il codice di inizializzazione e ha raggiunto il primo punto di ingresso dell'utente.|
|Eventi di eccezione|Inviato quando un programma in esecuzione raggiunge un'eccezione.|
|Eventi completi di valutazione dell'espressione|Inviato al termine della valutazione asincrona dell'espressione.|
|Eventi Trova simbolo|Inviato ogni volta che il DE deve chiedere all'utente di trovare i simboli per un modulo.|
|Caricare gli eventi completi|Inviato solo quando il caricamento iniziale del programma è completo e il primo codice sta per essere eseguito nel programma.|
|Eventi messaggio|Inviato quando i messaggi vengono inviati agli utenti.|
|Eventi di caricamento del modulo|Inviato quando un nuovo modulo viene caricato o scaricato.|
|Eventi stringa di output|Inviato quando il programma scrive l'output di debug.|
|Creare e distruggere eventi|Inviato per annunciare la creazione o l'eliminazione di processi, programmi, proprietà, sessioni e thread in modo che l'IDE di Visual Studio possa tenere traccia dello stato dei programmi sottoposti a debug.|
|Passaggio degli eventi completiStep complete events|Inviato al completamento di un passaggio.|
|Eventi di modifica del nome del thread|Inviato quando l'utente modifica il nome di un thread.|
|Eventi di modifica del nome del programma|Inviato quando l'utente modifica il nome di un programma.|

## <a name="see-also"></a>Vedere anche
- [Invio di eventi](../../extensibility/debugger/sending-events.md)
