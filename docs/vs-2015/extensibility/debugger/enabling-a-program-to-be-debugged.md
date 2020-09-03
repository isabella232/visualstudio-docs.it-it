---
title: Abilitazione del debug di un programma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b0f0331430a1cc625dee2a7029742fd62d67fb56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155368"
---
# <a name="enabling-a-program-to-be-debugged"></a>Abilitazione di un programma da sottoporre a debug
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Prima che il motore di debug (DE) possa eseguire il debug di un programma, è necessario prima avviare il DE o collegarlo a un programma esistente.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Recupero di una porta](../../extensibility/debugger/getting-a-port.md)  
 Viene illustrato come ottenere una porta come primo passaggio per consentire il debug di un programma.  
  
 [Registrazione del programma](../../extensibility/debugger/registering-the-program.md)  
 Viene illustrato il passaggio successivo per abilitare un programma di cui eseguire il debug: registrazione con la porta. Una volta registrato, il programma può essere sottoposto a debug dal processo di connessione o debug JIT (just-in-Time).  
  
 [Collegamento al programma](../../extensibility/debugger/attaching-to-the-program.md)  
 Viene illustrato il passaggio successivo: associazione del debugger al programma.  
  
 [Connessione basata su avvio](../../extensibility/debugger/launch-based-attachment.md)  
 Descrive l'allegato basato sul lancio a un programma, che è automatico all'avvio da parte di SDM.  
  
 [Invio degli eventi richiesti](../../extensibility/debugger/sending-the-required-events.md)  
 Vengono illustrati gli eventi necessari durante la creazione di un motore di debug (DE) e la relativa associazione a un programma.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Definisce un motore di debug (DE) e descrive i servizi implementati tramite le interfacce DE e il modo in cui possono determinare la transizione del debugger tra diverse modalità operative.
