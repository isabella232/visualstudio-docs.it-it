---
title: Allegato basato sull'avvio | Microsoft Docs
description: Informazioni sull'allegato basato sul lancio a un programma, che è automatico e segue un percorso simile a quello dell'allegato manuale.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 97bbc098e766a1025c372ff35c5849bfe652649f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904334"
---
# <a name="launch-based-attachment"></a>Allegato basato sull'avvio
L'allegato basato sul lancio a un programma è automatico. Quando il processo che ospita il programma viene avviato da SDM, l'allegato basato su avvio segue un percorso simile a quello del metodo di collegamento manuale. Per informazioni, vedere [Connettersi al programma](../../extensibility/debugger/attaching-to-the-program.md).

## <a name="the-attaching-process"></a>Processo di collegamento
 La differenza principale è la sequenza di eventi che seguono la **chiamata Attach,** come indicato di seguito:

1. Inviare **un oggetto evento IDebugEngineCreateEvent2** a SDM. Per informazioni dettagliate, vedere [Inviare eventi.](../../extensibility/debugger/sending-events.md)

2. Chiamare il `IDebugProgram2::GetProgramId` metodo **sull'interfaccia IDebugProgram2** passata al **metodo Attach.**

3. Inviare un **oggetto evento IDebugProgramCreateEvent2** per notificare a SDM che l'oggetto **IDebugProgram2 locale** è stato creato per rappresentare il programma a DE.

4. Inviare un [oggetto evento IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) per notificare a SDM che viene creato un nuovo thread per il processo avviato.

## <a name="see-also"></a>Vedere anche
- [Inviare gli eventi necessari](../../extensibility/debugger/sending-the-required-events.md)
- [Abilitare il debug di un programma](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
