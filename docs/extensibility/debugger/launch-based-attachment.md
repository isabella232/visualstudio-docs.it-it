---
title: Allegato basato su avvio | Microsoft Docs
description: Informazioni sull'allegato basato su avvio a un programma, che è automatico e segue un percorso simile a quello dell'allegato manuale.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 7e041c692a833b7d0a1891c078388a3f5b2d11e4
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606671"
---
# <a name="launch-based-attachment"></a>Allegato basato su avvio
L'allegato basato su avvio a un programma è automatico. Quando il processo che ospita il programma viene avviato da SDM, l'allegato basato su avvio segue un percorso simile a quello del metodo allegato manuale. Per informazioni, vedere [Connetti al programma](../../extensibility/debugger/attaching-to-the-program.md).

## <a name="the-attaching-process"></a>Processo di associazione
 La differenza principale è la sequenza di eventi che seguono la chiamata di **connessione** , come indicato di seguito:

1. Inviare un oggetto evento **IDebugEngineCreateEvent2** a SDM. Per informazioni dettagliate, vedere [inviare eventi](../../extensibility/debugger/sending-events.md).

2. Chiamare il `IDebugProgram2::GetProgramId` metodo sull'interfaccia **IDebugProgram2** passata al metodo di **connessione** .

3. Inviare un oggetto evento **IDebugProgramCreateEvent2** per notificare a SDM che l'oggetto **IDebugProgram2** locale è stato creato per rappresentare il programma alla de.

4. Inviare un oggetto evento [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) per notificare a SDM che è stato creato un nuovo thread per il processo avviato.

## <a name="see-also"></a>Vedere anche
- [Invia gli eventi necessari](../../extensibility/debugger/sending-the-required-events.md)
- [Abilitare un programma di cui eseguire il debug](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
