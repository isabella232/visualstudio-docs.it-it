---
title: L'invio di eventi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2a2c87b2e05e4ffe94d77333095438f43b644976
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311337"
---
# <a name="send-events"></a>Inviare eventi
Il meccanismo per la comunicazione tra il debugger e il motore di debug (DE) è un modello di eventi basato su DCOM. Gli eventi vengono inviati come oggetti COM, e ogni evento dispone di parametri che specificano:

- Germania che ha chiamato l'evento.

- Descrizione di cosa è successo.

- Il processo, programma e informazioni sul thread che identifica il contesto di in cui si è verificato l'evento. Il processo non viene inviato per gli eventi inviati da un CRI.

- Il tipo di evento che indica se l'evento è sincrono o asincrono.

  Tutti gli eventi di debug vengono inviati usando il metodo [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="in-this-section"></a>Contenuto della sezione
 [Origini evento](../../extensibility/debugger/event-sources-visual-studio-sdk.md) illustra le due origini di eventi: il motore di debug (DE) e la sessione di debug manager (SDM).

 [Tipi di eventi supportati](../../extensibility/debugger/supported-event-types.md) vengono descritti i tipi di eventi attualmente supportate: sincrone e asincrone.

 [Le descrizioni degli eventi](../../extensibility/debugger/event-descriptions.md) definisce gli eventi e i motivi per l'uso.

## <a name="related-sections"></a>Sezioni correlate
 [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md) viene descritto il funzionamento di un CRI con l'interprete o sistema operativo per fornire servizi di debug.