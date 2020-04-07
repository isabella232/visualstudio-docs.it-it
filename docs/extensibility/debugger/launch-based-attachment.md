---
title: Allegato basato sul lancio Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4910a97350366500b56593ec0076fdf0990b6d8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738468"
---
# <a name="launch-based-attachment"></a>Allegato basato sul lancio
L'attacco basato sul lancio a un programma è automatico. Quando il processo che ospita il programma viene avviato dal modello SDM, l'allegato basato sul lancio segue un percorso simile a quello del metodo di allegato manuale. Per informazioni, consultate [Allegare al programma.](../../extensibility/debugger/attaching-to-the-program.md)

## <a name="the-attaching-process"></a>Il processo di collegamento
 La differenza principale è la sequenza di eventi che seguono la chiamata **Attach,** come indicato di seguito:

1. Inviare un oggetto evento **IDebugEngineCreateEvent2** al modello SDM. Per informazioni dettagliate, vedere [Inviare eventi](../../extensibility/debugger/sending-events.md).

2. Chiamare `IDebugProgram2::GetProgramId` il metodo sull'interfaccia **IDebugProgram2** passata al metodo **Attach.**

3. Inviare un **IDebugProgramCreateEvent2** oggetto evento per notificare il modello SDM che l'oggetto **locale IDebugProgram2** è stato creato per rappresentare il programma al DE.

4. Inviare un oggetto evento [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) per notificare al modello SDM che viene creato un nuovo thread per il processo avviato.

## <a name="see-also"></a>Vedere anche
- [Inviare gli eventi richiesti](../../extensibility/debugger/sending-the-required-events.md)
- [Abilitare il debug di un programmaEnable a program to be debugged](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
