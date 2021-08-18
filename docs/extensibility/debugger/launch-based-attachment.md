---
title: Allegato basato sull'avvio | Microsoft Docs
description: Informazioni sull'allegato basato sull'avvio a un programma, che è automatico e segue un percorso simile a quello dell'allegato manuale.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: f3839c1edb8b8406e5b5ae0645205f0316b88d62
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065163"
---
# <a name="launch-based-attachment"></a>Allegato basato sull'avvio
L'allegato basato sull'avvio a un programma è automatico. Quando il processo che ospita il programma viene avviato da SDM, l'allegato basato sull'avvio segue un percorso simile a quello del metodo di allegato manuale. Per informazioni, vedere [Connettersi al programma](../../extensibility/debugger/attaching-to-the-program.md).

## <a name="the-attaching-process"></a>Processo di connessione
 La differenza principale è la sequenza di eventi che seguono la **chiamata a Attach,** come indicato di seguito:

1. Inviare **un oggetto evento IDebugEngineCreateEvent2** a SDM. Per informazioni dettagliate, vedere [Inviare eventi](../../extensibility/debugger/sending-events.md).

2. Chiamare il `IDebugProgram2::GetProgramId` metodo **sull'interfaccia IDebugProgram2** passata al **metodo Attach.**

3. Inviare un **oggetto evento IDebugProgramCreateEvent2** per notificare a SDM che l'oggetto **IDebugProgram2** locale è stato creato per rappresentare il programma al de.

4. Inviare un [oggetto evento IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) per notificare a SDM che viene creato un nuovo thread per il processo avviato.

## <a name="see-also"></a>Vedi anche
- [Inviare gli eventi necessari](../../extensibility/debugger/sending-the-required-events.md)
- [Abilitare il debug di un programma](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
