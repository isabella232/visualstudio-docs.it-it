---
title: Invio di eventi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 98247b894d2db628d508713875ba0ea7d0642729
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204735"
---
# <a name="sending-events"></a>Invio di eventi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il meccanismo per la comunicazione tra il debugger e il motore di debug (DE) è un modello di eventi basato su DCOM. Gli eventi vengono inviati come oggetti COM e ogni evento dispone di parametri che specificano quanto segue:  
  
- Oggetto DE che ha chiamato l'evento.  
  
- Descrizione degli eventi.  
  
- Informazioni sul processo, sul programma e sul thread che identificano il contesto in cui si è verificato l'evento. Il processo non viene inviato per gli eventi inviati da un DE.  
  
- Tipo di evento che indica se l'evento è sincrono o asincrono.  
  
  Tutti gli eventi di debug vengono inviati usando il metodo [IDebugEventCallback2:: Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Origini eventi](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Vengono illustrate le due origini degli eventi: il motore di debug (DE) e la gestione del debug della sessione (SDM).  
  
 [Tipi di evento supportati](../../extensibility/debugger/supported-event-types.md)  
 Vengono illustrati i tipi di eventi attualmente supportati: asincrono e sincrono.  
  
 [Descrizioni di eventi](../../extensibility/debugger/event-descriptions.md)  
 Definisce gli eventi e i motivi per utilizzarli.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Viene descritto il funzionamento di un DE con l'interprete o il sistema operativo per fornire servizi di debug.
