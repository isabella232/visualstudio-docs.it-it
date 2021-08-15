---
title: Impostazioni degli allegati basate sull'avvio | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: d674dd26a8908b26a53bf212692faebdd3e9589af49c9641513c1fb526a9981b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121324015"
---
# <a name="launch-based-attachment"></a>Allegato basato sull'avvio
L'allegato basato sul lancio a un programma è automatico. Quando il processo che ospita il programma viene avviato da SDM, l'allegato basato su avvio segue un percorso simile a quello del metodo di collegamento manuale. Per informazioni, vedere [Connettersi al programma.](../../extensibility/debugger/attaching-to-the-program.md)

## <a name="the-attaching-process"></a>Processo di collegamento
 La differenza principale è la sequenza di eventi che seguono la **chiamata Attach,** come indicato di seguito:

1. Inviare **un oggetto evento IDebugEngineCreateEvent2** a SDM. Per informazioni dettagliate, vedere [Inviare eventi.](../../extensibility/debugger/sending-events.md)

2. Chiamare il `IDebugProgram2::GetProgramId` metodo **sull'interfaccia IDebugProgram2** passata al **metodo Attach.**

3. Inviare un **oggetto evento IDebugProgramCreateEvent2** per notificare a SDM che l'oggetto **IDebugProgram2 locale** è stato creato per rappresentare il programma a DE.

4. Inviare un [oggetto evento IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) per notificare a SDM che viene creato un nuovo thread per il processo avviato.

## <a name="see-also"></a>Vedi anche
- [Inviare gli eventi necessari](../../extensibility/debugger/sending-the-required-events.md)
- [Abilitare il debug di un programma](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
