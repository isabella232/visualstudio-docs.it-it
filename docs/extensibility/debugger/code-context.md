---
title: Contesto del codice | Microsoft Docs
description: Informazioni sul contesto del codice nel debug di Visual Studio, che descrive una posizione nel codice presente quando un programma è stato interrotto in corrispondenza di un punto di interruzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 685650e0e97c3f9851f051fdaa78f86252597ff8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930720"
---
# <a name="code-context"></a>Contesto del codice
In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug, un **contesto di codice**:

- Fornisce un'astrazione di una posizione nel codice come noto al motore di debug (DE). Per la maggior parte delle architetture di runtime oggi, un contesto di codice può essere considerato come un indirizzo nel flusso di istruzioni di un programma. Per le lingue non tradizionali, in cui il codice non può essere rappresentato dalle istruzioni, un contesto di codice può essere rappresentato da altri mezzi.

- Descrive la posizione corrente nel flusso di esecuzione del programma di cui si esegue il debug.

- Esiste solo quando un programma è stato interrotto in corrispondenza di un punto di interruzione.

- Dispone di un contesto del documento associato.

- Viene implementato da un'interfaccia [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) .

## <a name="see-also"></a>Vedi anche
- [Contesto del documento](../../extensibility/debugger/document-context.md)
- [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)
