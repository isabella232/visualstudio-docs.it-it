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
ms.workload:
- vssdk
ms.openlocfilehash: 6e9af2618150df522a459e47f312c1dc1e6a220c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902254"
---
# <a name="send-events"></a>Inviare eventi
Il meccanismo di comunicazione tra il debugger e il motore di debug (DE) è un modello di eventi basato su DCOM. Gli eventi vengono inviati come oggetti COM e ogni evento include parametri che specificano:

- De che ha chiamato l'evento.

- Descrizione dell'accaduto.

- Informazioni sul processo, sul programma e sul thread che identificano il contesto in cui si è verificato l'evento. Il processo non viene inviato per gli eventi inviati da un de.

- Tipo di evento che indica se l'evento è sincrono o asincrono.

  Tutti gli eventi di debug vengono inviati usando il metodo [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="in-this-section"></a>Contenuto della sezione
 [Origini eventi](../../extensibility/debugger/event-sources-visual-studio-sdk.md) Vengono illustrate le due origini degli eventi: il motore di debug (DE) e lo SDM (Session Debug Manager).

 [Tipi di evento supportati](../../extensibility/debugger/supported-event-types.md) Vengono illustrati i tipi di evento attualmente supportati: asincroni e sincroni.

 [Descrizioni degli eventi](../../extensibility/debugger/event-descriptions.md) Definisce gli eventi e i motivi per il loro utilizzo.

## <a name="related-sections"></a>Sezioni correlate
 [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md) Descrive il funzionamento di un de con l'interprete o il sistema operativo per fornire servizi di debug.
