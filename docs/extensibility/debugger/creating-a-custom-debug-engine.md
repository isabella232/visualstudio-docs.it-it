---
title: Creazione di un motore di debug personalizzato | Microsoft Docs
description: Usare questi articoli per informazioni sulla creazione di un motore di debug che consenta il debug di architetture di runtime specifiche.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: dd04ac2183b726d777b180e1be127efec2284135
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122111762"
---
# <a name="create-a-custom-debug-engine"></a>Creare un motore di debug personalizzato
Un motore di debug è un componente che consente il debug di architetture di runtime specifiche. In genere è presente una sola implementazione di DE per ogni ambiente di run-time.

> [!NOTE]
> Anche se sono disponibili implementazioni DE separate per Transact-SQL e JScript, VBScript e JScript condividono un singolo DE.

 De funziona con l'interprete o il sistema operativo per fornire servizi di debug come controllo dell'esecuzione, punti di interruzione e valutazione delle espressioni. Questi servizi vengono implementati tramite le interfacce DE e possono causare la transizione del debugger tra modalità operative diverse. Per altre informazioni, vedere [Modalità operative.](../../extensibility/debugger/operational-modes.md)

 La creazione di un'istanza de è costituita dai passaggi seguenti:

1. Registrare un'istanza de con Visual Studio

2. Abilitare il debug di un programma

3. Implementare il controllo di esecuzione e la valutazione dello stato

4. Inviare eventi

5. Configurare la terminazione e lo scollegamento

## <a name="in-this-section"></a>Contenuto della sezione
 [Registrare un motore di debug personalizzato](../../extensibility/debugger/registering-a-custom-debug-engine.md) Illustra i passaggi necessari per registrare un motore di debug con Visual Studio in modo che possa essere usato.

 [Abilitare il debug di un programma](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) Spiega che prima che DE possa eseguire il debug di un programma, è necessario avviarlo o collegarlo a un programma esistente.

 [Implementare il controllo di esecuzione e la valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md) Viene illustrato il motivo per cui il debug di un'applicazione richiede l'implementazione delle funzionalità di controllo dell'esecuzione.

 [Inviare eventi](../../extensibility/debugger/sending-events.md) Descrive la comunicazione tra il debugger e DE come modello di eventi basato su DCOM.

 [Configurare la terminazione e lo scollegamento](../../extensibility/debugger/termination-and-detaching.md) Viene illustrato come ottenere la terminazione normale, ovvero non sono presenti punti di interruzione, eccezioni, errori di runtime o cicli infiniti nell'applicazione di cui eseguire il debug.

 [Chiamare eventi del debugger](../../extensibility/debugger/calling-debugger-events.md) Documenta l'ordine di chiamata degli eventi che si verificano in una sessione di debug.

 [Procedura: Eseguire il debug di un motore di debug personalizzato](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) Viene illustrato come eseguire il debug di un ded personalizzato.

## <a name="see-also"></a>Vedi anche
- [Visual Studio estensibilità del debugger](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
