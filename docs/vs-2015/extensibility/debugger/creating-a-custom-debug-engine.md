---
title: Creazione di un oggetto personalizzato di motore di Debug | Microsoft Docs
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63383431"
---
# <a name="creating-a-custom-debug-engine"></a>Creazione di un motore di debug personalizzato
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un motore di debug (DE) è un componente che consente il debug di architetture in fase di esecuzione particolare. È in genere solo un'implementazione di DE per ogni ambiente run-time.  
  
> [!NOTE]
> Anche se sono disponibili implementazioni separate di DE per Transact-SQL e JScript, VBScript e JScript condividono un singolo DE.  
  
 Un CRI funziona con il sistema interprete o operazione per fornire tali servizi di debug come valutazione dell'espressione di controllo e i punti di interruzione esecuzione. Questi servizi vengono implementati tramite le interfacce DE e possono causare il debugger per la transizione tra diverse modalità operative. Per altre informazioni, vedere [modalità operative](../../extensibility/debugger/operational-modes.md).  
  
 Creazione di un CRI prevede i passaggi seguenti:  
  
1. La registrazione di un CRI con Visual Studio  
  
2. Abilitazione di un programma da sottoporre a debug  
  
3. Valutazione di controllo e lo stato di esecuzione  
  
4. L'invio di eventi  
  
5. Terminazione e scollegamento  
  
## <a name="in-this-section"></a>In questa sezione  
 [Registrazione di un motore di debug personalizzato](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Illustra i passaggi necessari per registrare un motore di debug con Visual Studio in modo che può essere usato.  
  
 [Abilitazione di un programma da sottoporre a debug](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Viene illustrato che prima che la Germania possa eseguire il debug di un programma, è prima necessario avviare il DE o collegarlo a un programma esistente.  
  
 [Controllo dell'esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Descrive il motivo per cui debug di un'applicazione richiede l'implementazione di funzionalità di controllo di esecuzione.  
  
 [Invio di eventi](../../extensibility/debugger/sending-events.md)  
 Viene illustrata la comunicazione tra il debugger e il DE come un modello di eventi basato su DCOM.  
  
 [Terminazione e scollegamento](../../extensibility/debugger/termination-and-detaching.md)  
 Viene illustrato come ottenere la terminazione normale, il che significa che non esistono Nessun punti di interruzione, eccezioni, errori di run-time o cicli infiniti nell'applicazione da sottoporre a debug.  
  
 [Chiamata degli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)  
 Documenti di ordine di chiamata degli eventi che si verificano in una sessione di debug.  
  
 [Procedura: Eseguire il debug di un motore di debug personalizzato](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Viene illustrato come eseguire il debug di un CRI personalizzato.  
  
## <a name="see-also"></a>Vedere anche  
 [Estendibilità del debugger di Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
