---
title: Codice contesto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9b02d5697260a9b212029ce1db4b7edb22de34c4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60038919"
---
# <a name="code-context"></a>Contesto del codice
Nelle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug, una **contesto codice**:

- Fornisce un'astrazione di una posizione nel codice come nota al motore di debug (DE). Per la maggior parte delle architetture di run-time oggi, un contesto del codice può essere considerato come un indirizzo nel flusso di istruzioni del programma. Per le lingue non convenzionale, dove codice non può essere rappresentato da istruzioni, un contesto del codice può essere rappresentato da un altro modo.

- Descrive la posizione corrente nel flusso di esecuzione del programma di cui che si esegue il debug.

- Esiste solo quando un programma è stata interrotta in un punto di interruzione.

- Ha un contesto di documento associato.

- Viene implementato da un [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) interfaccia.

## <a name="see-also"></a>Vedere anche
- [Contesto di documento](../../extensibility/debugger/document-context.md)
- [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)