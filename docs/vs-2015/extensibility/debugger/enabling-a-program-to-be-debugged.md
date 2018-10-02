---
title: Abilitazione di un programma da sottoporre a debug | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f0dcb98df8562a5f35fc0d56d5a4ef6570021664
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532015"
---
# <a name="enabling-a-program-to-be-debugged"></a>Abilitazione di un programma da sottoporre a debug
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [abilitazione di un programma da sottoporre a debug](https://docs.microsoft.com/visualstudio/extensibility/debugger/enabling-a-program-to-be-debugged).  
  
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

