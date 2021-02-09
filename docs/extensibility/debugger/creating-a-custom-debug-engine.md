---
title: Creazione di un motore di debug personalizzato | Microsoft Docs
description: Usare questi articoli per informazioni sulla creazione di un motore di debug che consente il debug di particolari architetture di Runtime.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7c0aa8550bc402520052003b59cf4ab1deaad7b2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888966"
---
# <a name="create-a-custom-debug-engine"></a>Creare un motore di debug personalizzato
Un motore di debug (DE) è un componente che consente il debug di particolari architetture di run-time. In genere esiste solo un'implementazione di DE per ogni ambiente di run-time.

> [!NOTE]
> Sebbene siano presenti implementazioni di DE separate per Transact-SQL e JScript, VBScript e JScript condividono un solo DE.

 Un DE interagisce con l'interprete o il sistema operativo per fornire servizi di debug quali il controllo dell'esecuzione, i punti di interruzione e la valutazione dell'espressione. Questi servizi vengono implementati tramite le interfacce DE e possono causare la transizione del debugger tra diverse modalità operative. Per ulteriori informazioni, vedere [modalità operative](../../extensibility/debugger/operational-modes.md).

 La creazione di un DE prevede i passaggi seguenti:

1. Registrare un DE con Visual Studio

2. Abilitare un programma di cui eseguire il debug

3. Implementare il controllo di esecuzione e la valutazione dello stato

4. Inviare eventi

5. Configurare la terminazione e lo scollegamento

## <a name="in-this-section"></a>Contenuto della sezione
 [Registrare un motore di debug personalizzato](../../extensibility/debugger/registering-a-custom-debug-engine.md) Vengono illustrati i passaggi necessari per registrare un motore di debug con Visual Studio in modo che possa essere utilizzato.

 [Abilitare un programma di cui eseguire il debug](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) Viene spiegato che prima di poter eseguire il debug di un programma, è necessario prima avviare il DE o collegarlo a un programma esistente.

 [Implementare il controllo di esecuzione e la valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md) Viene illustrato il motivo per cui il debug di un'applicazione richiede l'implementazione di funzionalità di controllo

 [Invia eventi](../../extensibility/debugger/sending-events.md) Descrive la comunicazione tra il debugger e il DE come modello di eventi basato su DCOM.

 [Configurare la terminazione e lo scollegamento](../../extensibility/debugger/termination-and-detaching.md) Viene illustrato come ottenere la terminazione normale, ovvero non sono presenti punti di interruzione, eccezioni, errori di run-time o cicli infiniti nell'applicazione di cui eseguire il debug.

 [Chiama eventi del debugger](../../extensibility/debugger/calling-debugger-events.md) Documenta l'ordine di chiamata degli eventi che si verificano in una sessione di debug.

 [Procedura: eseguire il debug di un motore di debug personalizzato](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) Viene illustrato come eseguire il debug di un DE personalizzato.

## <a name="see-also"></a>Vedi anche
- [Estensibilità del debugger di Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
