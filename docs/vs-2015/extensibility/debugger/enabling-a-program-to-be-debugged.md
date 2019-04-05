---
title: Abilitazione di un programma da sottoporre a debug | Microsoft Docs
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968906"
---
# <a name="enabling-a-program-to-be-debugged"></a>Abilitazione di un programma da sottoporre a debug
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Prima che il motore di debug (DE) può eseguire il debug di un programma, è necessario avviare il DE o collegarlo a un programma esistente.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Recupero di una porta](../../extensibility/debugger/getting-a-port.md)  
 Viene illustrato come ottenere una porta come il primo passaggio per abilitare un programma da sottoporre a debug.  
  
 [Registrazione del programma](../../extensibility/debugger/registering-the-program.md)  
 Viene illustrato il passaggio successivo di abilitazione di un programma da sottoporre a debug: registrandola con la porta. Una volta registrato, il programma di debug può essere eseguito tramite il processo di collegamento o il debug just-in-time (JIT).  
  
 [Collegamento al programma](../../extensibility/debugger/attaching-to-the-program.md)  
 Viene illustrato il passaggio successivo: collegare il debugger al programma.  
  
 [Collegamento basato su avvio](../../extensibility/debugger/launch-based-attachment.md)  
 Descrive basato su avvio allegato a un programma, che risulta automatico all'avvio per il modello SDM.  
  
 [Invio degli eventi richiesti](../../extensibility/debugger/sending-the-required-events.md)  
 Procedura per gli eventi necessari quando si crea un motore di debug (DE) e collegarlo a un programma.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Definisce un motore di debug (DE) e vengono descritti i servizi implementati tramite le interfacce DE e come possono causare il debugger per la transizione tra diverse modalità operative.
