---
title: Contesto del codice . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6424c1182f30b1bbfe6c166209b94afb7ec45549
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739160"
---
# <a name="code-context"></a>Contesto del codice
Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug, un **contesto di codice**:

- Fornisce un'astrazione di una posizione nel codice nota al motore di debug (DE). Per la maggior parte delle architetture di runtime oggi, un contesto di codice può essere considerato come un indirizzo nel flusso di istruzioni di un programma. Per i linguaggi non tradizionali, in cui il codice non può essere rappresentato da istruzioni, un contesto di codice può essere rappresentato con altri mezzi.

- Descrive la posizione corrente nel flusso di esecuzione del programma di cui si sta eseguendo il debug.

- Esiste solo quando un programma è stato arrestato in corrispondenza di un punto di interruzione.

- Ha un contesto di documento associato.

- Viene implementato da un [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) interfaccia.

## <a name="see-also"></a>Vedere anche
- [Contesto del documento](../../extensibility/debugger/document-context.md)
- [Contesti del debuggerDebugger contexts](../../extensibility/debugger/debugger-contexts.md)
