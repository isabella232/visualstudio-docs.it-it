---
title: Creazione di un oggetto personalizzato di motore di Debug | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ece2b480890054526552ad3aeea4f3bd1a437f74
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203680"
---
# <a name="create-a-custom-debug-engine"></a>Creare un motore di debug personalizzato
Un motore di debug (DE) è un componente che consente il debug di architetture in fase di esecuzione particolare. È in genere solo un'implementazione di DE per ogni ambiente run-time.  
  
> [!NOTE]
>  Anche se sono disponibili implementazioni separate di DE per Transact-SQL e JScript, VBScript e JScript condividono un singolo DE.  
  
 Un CRI funziona con il sistema interprete o operazione per fornire tali servizi di debug come valutazione dell'espressione di controllo e i punti di interruzione esecuzione. Questi servizi vengono implementati tramite le interfacce DE e possono causare il debugger per la transizione tra diverse modalità operative. Per altre informazioni, vedere [modalità operative](../../extensibility/debugger/operational-modes.md).  
  
 Creazione di un CRI prevede i passaggi seguenti:  
  
1.  Registrare un CRI con Visual Studio  
  
2.  Abilitare un programma da sottoporre a debug  
  
3.  Implementare la valutazione di controllo e lo stato di esecuzione  
  
4.  Inviare eventi  
  
5.  Configurazione di terminazione e scollegamento  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Registrare un motore di debug personalizzato](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Illustra i passaggi necessari per registrare un motore di debug con Visual Studio in modo che può essere usato.  
  
 [Abilitare un programma da sottoporre a debug](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Viene illustrato che prima che la Germania possa eseguire il debug di un programma, è prima necessario avviare il DE o collegarlo a un programma esistente.  
  
 [Implementare la valutazione di controllo e lo stato di esecuzione](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Descrive il motivo per cui debug di un'applicazione richiede l'implementazione di funzionalità di controllo di esecuzione.  
  
 [Inviare eventi](../../extensibility/debugger/sending-events.md)  
 Viene illustrata la comunicazione tra il debugger e il DE come un modello di eventi basato su DCOM.  
  
 [Configurazione di terminazione e scollegamento](../../extensibility/debugger/termination-and-detaching.md)  
 Viene illustrato come ottenere la terminazione normale, il che significa che non esistono Nessun punti di interruzione, eccezioni, errori di run-time o cicli infiniti nell'applicazione da sottoporre a debug.  
  
 [Chiamare gli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)  
 Documenti di ordine di chiamata degli eventi che si verificano in una sessione di debug.  
  
 [Procedura: Eseguire il Debug di un motore di debug personalizzato](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Viene illustrato come eseguire il debug di un CRI personalizzato.  
  
## <a name="see-also"></a>Vedere anche  
 [Estendibilità del debugger Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)