---
title: Invio di eventi | Microsoft Docs
description: Informazioni sul modo in cui il debugger e il motore di debug utilizzano un modello di eventi basato su DCOM. Gli eventi vengono inviati come oggetti COM.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 135dd0278ee765ef88ae6cef39675a2fa92236d7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070390"
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
