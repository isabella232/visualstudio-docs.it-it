---
title: Creazione di un motore di debug personalizzato | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b2a73dfae7772d8edec076238704aa1b52c9b028
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840096"
---
# <a name="creating-a-custom-debug-engine"></a>Creazione di un motore di debug personalizzato
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un motore di debug (DE) è un componente che consente il debug di particolari architetture di run-time. In genere esiste solo un'implementazione di DE per ogni ambiente di run-time.  
  
> [!NOTE]
> Sebbene siano presenti implementazioni di DE separate per Transact-SQL e JScript, VBScript e JScript condividono un solo DE.  
  
 Un DE interagisce con l'interprete o il sistema operativo per fornire servizi di debug quali il controllo dell'esecuzione, i punti di interruzione e la valutazione dell'espressione. Questi servizi vengono implementati tramite le interfacce DE e possono causare la transizione del debugger tra diverse modalità operative. Per ulteriori informazioni, vedere [modalità operative](../../extensibility/debugger/operational-modes.md).  
  
 La creazione di un DE prevede i passaggi seguenti:  
  
1. Registrazione di un DE con Visual Studio  
  
2. Abilitazione di un programma di cui eseguire il debug  
  
3. Controllo di esecuzione e valutazione dello stato  
  
4. Invio di eventi  
  
5. Terminazione e scollegamento  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Registrazione di un motore di debug personalizzato](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Vengono illustrati i passaggi necessari per registrare un motore di debug con Visual Studio in modo che possa essere utilizzato.  
  
 [Abilitazione di un programma da sottoporre a debug](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Viene spiegato che prima di poter eseguire il debug di un programma, è necessario prima avviare il DE o collegarlo a un programma esistente.  
  
 [Controllo dell'esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Viene illustrato il motivo per cui il debug di un'applicazione richiede l'implementazione di funzionalità di controllo  
  
 [Invio di eventi](../../extensibility/debugger/sending-events.md)  
 Descrive la comunicazione tra il debugger e il DE come modello di eventi basato su DCOM.  
  
 [Terminazione e scollegamento](../../extensibility/debugger/termination-and-detaching.md)  
 Viene illustrato come ottenere la terminazione normale, ovvero non sono presenti punti di interruzione, eccezioni, errori di run-time o cicli infiniti nell'applicazione di cui eseguire il debug.  
  
 [Chiamata degli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)  
 Documenta l'ordine di chiamata degli eventi che si verificano in una sessione di debug.  
  
 [Procedura: Eseguire il debug di un motore di debug personalizzato](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Viene illustrato come eseguire il debug di un DE personalizzato.  
  
## <a name="see-also"></a>Vedere anche  
 [Estendibilità del debugger di Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
