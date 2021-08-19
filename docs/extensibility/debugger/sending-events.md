---
title: Invio di eventi | Microsoft Docs
description: Informazioni su come il debugger e il motore di debug usano un modello di eventi basato su DCOM. Gli eventi vengono inviati come oggetti COM.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 1f993639e8c79760d24502f2c58afc7c9ab8cdb0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122137646"
---
# <a name="send-events"></a>Inviare eventi
Il meccanismo per la comunicazione tra il debugger e il motore di debug è un modello di eventi basato su DCOM. Gli eventi vengono inviati come oggetti COM e ogni evento dispone di parametri che specificano:

- De che ha chiamato l'evento.

- Descrizione dell'evento.

- Informazioni su processo, programma e thread che identificano il contesto in cui si è verificato l'evento. Il processo non viene inviato per gli eventi inviati da un de.

- Tipo di evento che indica se l'evento è sincrono o asincrono.

  Tutti gli eventi di debug vengono inviati usando il metodo [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="in-this-section"></a>Contenuto della sezione
 [Origini eventi](../../extensibility/debugger/event-sources-visual-studio-sdk.md) Vengono illustrate le due origini degli eventi: il motore di debug (DE) e la gestione del debug di sessione (SDM).

 [Tipi di evento supportati](../../extensibility/debugger/supported-event-types.md) Vengono illustrati i tipi di evento attualmente supportati: asincrono e sincrono.

 [Descrizioni degli eventi](../../extensibility/debugger/event-descriptions.md) Definisce gli eventi e i motivi per cui viene utilizzato.

## <a name="related-sections"></a>Sezioni correlate
 [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md) Viene descritto il funzionamento di una derelimentazione con l'interprete o il sistema operativo per fornire servizi di debug.
