---
title: Invio di eventi | Microsoft Docs
description: Informazioni sul modo in cui il debugger e il motore di debug utilizzano un modello di eventi basato su DCOM. Gli eventi vengono inviati come oggetti COM.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 0262868ae442bfdd8b99c16f59e000f4ebfc35c5
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847910"
---
# <a name="send-events"></a>Inviare eventi
Il meccanismo per la comunicazione tra il debugger e il motore di debug (DE) è un modello di eventi basato su DCOM. Gli eventi vengono inviati come oggetti COM e ogni evento ha parametri che specificano:

- Oggetto DE che ha chiamato l'evento.

- Descrizione degli eventi.

- Informazioni sul processo, sul programma e sul thread che identificano il contesto in cui si è verificato l'evento. Il processo non viene inviato per gli eventi inviati da un DE.

- Tipo di evento che indica se l'evento è sincrono o asincrono.

  Tutti gli eventi di debug vengono inviati usando il metodo [IDebugEventCallback2:: Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="in-this-section"></a>Contenuto della sezione
 [Origini eventi](../../extensibility/debugger/event-sources-visual-studio-sdk.md) Vengono illustrate le due origini degli eventi: il motore di debug (DE) e la gestione del debug della sessione (SDM).

 [Tipi di evento supportati](../../extensibility/debugger/supported-event-types.md) Vengono illustrati i tipi di eventi attualmente supportati: asincrono e sincrono.

 [Descrizioni degli eventi](../../extensibility/debugger/event-descriptions.md) Definisce gli eventi e i motivi per utilizzarli.

## <a name="related-sections"></a>Sezioni correlate
 [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md) Viene descritto il funzionamento di un DE con l'interprete o il sistema operativo per fornire servizi di debug.
