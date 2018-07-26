---
title: L'invio di eventi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 87087a2087591b01170b82c0335e4bbffc579cc2
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252453"
---
# <a name="send-events"></a>Inviare eventi
Il meccanismo per la comunicazione tra il debugger e il motore di debug (DE) è un modello di eventi basato su DCOM. Gli eventi vengono inviati come oggetti COM, e ogni evento dispone di parametri che specificano:  
  
-   Germania che ha chiamato l'evento.  
  
-   Descrizione di cosa è successo.  
  
-   Il processo, programma e informazioni sul thread che identifica il contesto di in cui si è verificato l'evento. Il processo non viene inviato per gli eventi inviati da un CRI.  
  
-   Il tipo di evento che indica se l'evento è sincrono o asincrono.  
  
 Tutti gli eventi di debug vengono inviati usando il metodo [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Origini eventi](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Illustra le due origini di eventi: il motore di debug (DE) e la sessione di debug manager (SDM).  
  
 [Tipi di evento supportati](../../extensibility/debugger/supported-event-types.md)  
 Vengono descritti i tipi di eventi attualmente supportate: sincrone e asincrone.  
  
 [Descrizioni degli eventi](../../extensibility/debugger/event-descriptions.md)  
 Definisce gli eventi e i motivi per l'uso.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Descrive come un CRI funziona con l'interprete o sistema operativo per fornire servizi di debug.