---
title: Attacco basato su avvio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 638eaea19b4f21e749fbd3db845f18eb573420f2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344152"
---
# <a name="launch-based-attachment"></a>Attacco basato su avvio
Basato su avvio allegato a un programma è automatica. Quando il processo che ospita il programma viene avviato per il modello SDM, basato su avvio degli allegati segue un percorso simile a quella del metodo allegato manuale. Per informazioni, vedere [collegare al programma](../../extensibility/debugger/attaching-to-the-program.md).

## <a name="the-attaching-process"></a>Il processo di collegamento
 La differenza principale è la sequenza di eventi seguendo la **Attach** chiamare, come indicato di seguito:

1. Invio di un **IDebugEngineCreateEvent2** oggetto dell'evento per il modello SDM. Per informazioni dettagliate, vedere [inviare eventi](../../extensibility/debugger/sending-events.md).

2. Chiamare il `IDebugProgram2::GetProgramId` metodo sul **IDebugProgram2** interfaccia passato al **Attach** (metodo).

3. Invio di un **IDebugProgramCreateEvent2** oggetto dell'evento per notificare il modello SDM che locale **IDebugProgram2** oggetto è stato creato per rappresentare il programma per la Germania.

4. Invio di un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) oggetto dell'evento per notificare il modello SDM che viene creato un nuovo thread per il processo che ha avviato.

## <a name="see-also"></a>Vedere anche
- [Inviare gli eventi richiesti](../../extensibility/debugger/sending-the-required-events.md)
- [Abilitare un programma da sottoporre a debug](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)