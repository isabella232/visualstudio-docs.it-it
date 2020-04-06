---
title: Creazione di un motore di debug personalizzato Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a350d640fffcc6e09cf8f981c797b97071a0cacf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739031"
---
# <a name="create-a-custom-debug-engine"></a>Creare un motore di debug personalizzatoCreate a custom debug engine
Un motore di debug (DE) è un componente che consente il debug di particolari architetture di runtime. In genere esiste una sola implementazione DE per ogni ambiente di runtime.

> [!NOTE]
> Sebbene esistano implementazioni DE separate per Transact-SQLTransact-SQL e JScript, VBScript e JScript condividono un singolo DE.

 Un DE funziona con l'interprete o il sistema operativo per fornire servizi di debug quali il controllo dell'esecuzione, i punti di interruzione e la valutazione delle espressioni. Questi servizi vengono implementati tramite le interfacce DE e possono causare la transizione del debugger tra diverse modalità operative. Per ulteriori informazioni, consultate [Modalità operative.](../../extensibility/debugger/operational-modes.md)

 La creazione di un DE è costituita dai seguenti passaggi:

1. Registrare un DE con Visual StudioRegister a DE with Visual Studio

2. Abilitare il debug di un programmaEnable a program to be debugged

3. Implementare il controllo dell'esecuzione e la valutazione dello statoImplement execution control and state evaluation

4. Inviare eventi

5. Impostare la terminazione e lo scollegamento

## <a name="in-this-section"></a>Contenuto della sezione
 [Registrare un motore di debug personalizzatoRegister a custom debug engine](../../extensibility/debugger/registering-a-custom-debug-engine.md) Vengono illustrati i passaggi necessari per registrare un motore di debug con Visual Studio in modo che possa essere utilizzato.

 [Abilitare il debug di un programmaEnable a program to be debugged](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) Viene illustrato che prima di DE è possibile eseguire il debug di un programma, è necessario avviare il DE o collegarlo a un programma esistente.

 [Implementare il controllo dell'esecuzione e la valutazione dello statoImplement execution control and state evaluation](../../extensibility/debugger/execution-control-and-state-evaluation.md) Viene illustrato il motivo per cui il debug di un'applicazione richiede l'implementazione delle funzionalità di controllo dell'esecuzione.

 [Invia eventi](../../extensibility/debugger/sending-events.md) Descrive la comunicazione tra il debugger e il DE come modello eventi basato su DCOM.

 [Impostare la terminazione e lo scollegamento](../../extensibility/debugger/termination-and-detaching.md) Viene illustrato come ottenere la terminazione normale, ovvero che non sono presenti punti di interruzione, eccezioni, errori di runtime o cicli infiniti nell'applicazione di cui eseguire il debug.

 [Chiamare eventi del debuggerCall debugger events](../../extensibility/debugger/calling-debugger-events.md) Documenta l'ordine di chiamata degli eventi che si verificano in una sessione di debug.

 Procedura: eseguire il debug di un motore di [debug personalizzatoHow To: Debug a custom debug engine](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) Viene illustrato come eseguire il debug di un DE personalizzato.

## <a name="see-also"></a>Vedere anche
- [Estendibilità del debugger di Visual StudioVisual Studio debugger extensibility](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
