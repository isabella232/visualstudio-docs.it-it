---
title: Contesto del codice | Microsoft Docs
description: Informazioni sul contesto del codice in Visual Studio debug, che descrive una posizione nel codice che esiste quando un programma si è arrestato in corrispondenza di un punto di interruzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 774daabac461c00998048455f4e23bd2ab7bd379
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627677"
---
# <a name="code-context"></a>Contesto del codice
Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug, un **contesto del codice:**

- Fornisce un'astrazione di una posizione nel codice nota al motore di debug. Per la maggior parte delle architetture di run-time di oggi, un contesto di codice può essere pensato come un indirizzo nel flusso di istruzioni di un programma. Per i linguaggi non differenziali, in cui il codice potrebbe non essere rappresentato da istruzioni, un contesto di codice può essere rappresentato con altri mezzi.

- Descrive la posizione corrente nel flusso di esecuzione del programma di cui si esegue il debug.

- Esiste solo quando un programma è stato arrestato in corrispondenza di un punto di interruzione.

- Dispone di un contesto di documento associato.

- Viene implementato da [un'interfaccia IDebugCodeContext2.](../../extensibility/debugger/reference/idebugcodecontext2.md)

## <a name="see-also"></a>Vedi anche
- [Contesto del documento](../../extensibility/debugger/document-context.md)
- [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)
