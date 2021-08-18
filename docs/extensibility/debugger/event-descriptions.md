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
ms.openlocfilehash: d1632fde2f9f2040a3883f371291c06d190564c2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122153537"
---
# <a name="event-descriptions"></a>Descrizioni degli eventi
Ogni tipo di evento ha uno scopo specifico.

## <a name="events-and-the-reasons-for-their-use"></a>Eventi e motivi per l'uso

|Event|Descrizione|
|-----------|-----------------|
|Attivare gli eventi del documento|Si verifica quando il motore di debug (DE) vuole che l'IDE a aperti o portare un documento in primo piano.|
|Eventi di errore associati a un punto di interruzione o a un punto di interruzione|Inviato quando un punto di interruzione è associato o quando un punto di interruzione non può essere associato e viene restituito un errore.|
|Eventi non associati ai punti di interruzione|Si verifica quando un punto di interruzione associato viene disassociato dal codice.|
|Può arrestare gli eventi|Inviato all'IDE per determinare se l'utente vuole arrestarsi in un punto specificato nel codice.|
|Eventi dei punti di interruzione|Si verifica quando viene raggiunto un punto di interruzione del codice o dei dati.|
|Documentare eventi di testo|Si verifica quando il testo in un documento viene modificato. Questi eventi non vengono inviati tramite il `IDebugEventCallBack2::Event` metodo .|
|Eventi di creazione del motore|Inviato quando viene creato un motore per la prima volta.|
|Eventi del punto di ingresso|Inviato quando il programma in fase di debug ha eseguito il codice di inizializzazione e ha raggiunto il primo punto di ingresso dell'utente.|
|Eventi di eccezione|Inviato quando un programma in esecuzione raggiunge un'eccezione.|
|Eventi di valutazione delle espressioni completati|Inviato al termine della valutazione asincrona dell'espressione.|
|Eventi Find Symbol|Inviato ogni volta che il deret deve chiedere all'utente di trovare i simboli per un modulo.|
|Caricare gli eventi completi|Inviato solo quando il caricamento iniziale del programma è completo e il primo codice sta per essere eseguito nel programma.|
|Eventi di messaggio|Inviato quando i messaggi vengono inviati agli utenti.|
|Eventi di caricamento dei moduli|Inviato quando viene caricato o scaricato un nuovo modulo.|
|Eventi di stringa di output|Inviato quando il programma scrive l'output di debug.|
|Creare ed eliminare gli eventi|Inviato per annunciare la creazione o la distruzione di processi, programmi, proprietà, sessioni e thread in modo che l'IDE di Visual Studio possa tenere traccia dello stato dei programmi di cui è in corso il debug.|
|Eventi di completamento passaggio|Inviato al termine di un passaggio.|
|Eventi di modifica del nome del thread|Inviato quando l'utente modifica il nome di un thread.|
|Eventi di modifica del nome del programma|Inviato quando l'utente modifica il nome di un programma.|

## <a name="see-also"></a>Vedi anche
- [Invio di eventi](../../extensibility/debugger/sending-events.md)
