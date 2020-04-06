---
title: Proprietà Sending Events . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5ec0d3aa29da562147b71b8efde49baf07d8ae0b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713036"
---
# <a name="send-events"></a>Inviare eventi
Il meccanismo per la comunicazione tra il debugger e il motore di debug (DE) è un modello di eventi basato su DCOM. Gli eventi vengono inviati come oggetti COM e ogni evento dispone di parametri che specificano:

- Il DE che ha chiamato l'evento.

- Una descrizione di quello che è successo.

- Informazioni sul processo, sul programma e sul thread che identificano il contesto in cui si è verificato l'evento. Il processo non viene inviato per gli eventi inviati da un DE.

- Tipo di evento che indica se l'evento è sincrono o asincrono.

  Tutti gli eventi di debug vengono inviati utilizzando il metodo [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="in-this-section"></a>Contenuto della sezione
 [Origini eventi](../../extensibility/debugger/event-sources-visual-studio-sdk.md) Vengono illustrate le due origini degli eventi: il motore di debug (DE) e il gestore di debug di sessione (SDM).

 [Tipi di evento supportati](../../extensibility/debugger/supported-event-types.md) Vengono illustrati i tipi di evento attualmente supportati: asincrono e sincrono.

 [Descrizioni degli eventi](../../extensibility/debugger/event-descriptions.md) Definisce gli eventi e i motivi del loro utilizzo.

## <a name="related-sections"></a>Sezioni correlate
 [Creazione di un motore di debug personalizzatoCreating a custom debug engine](../../extensibility/debugger/creating-a-custom-debug-engine.md) Viene descritto come un DE funziona con l'interprete o il sistema operativo per fornire servizi di debug.
