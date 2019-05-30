---
title: Posizione del documento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: b59d739c-7572-427f-a70d-4e5df63d02c1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fecc50de842f628c54878af5fc91b5aeb3adefa4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345727"
---
# <a name="document-position"></a>Posizione di documento
Nelle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug, una *posizione documento*:

- Fornisce un'astrazione di una posizione in un file di origine come noti all'IDE. Per la maggior parte delle lingue oggi, una posizione di documento può essere considerata come una posizione in un file di origine.

- Descrive una posizione in un documento di origine a un motore di debug.

- Viene implementato da un [IDebugDocumentPosition2](../../extensibility/debugger/reference/idebugdocumentposition2.md) interfaccia.

## <a name="see-also"></a>Vedere anche
- [Contesto del codice](../../extensibility/debugger/code-context.md)
- [Contesto di documento](../../extensibility/debugger/document-context.md)
- [Provider di simboli](../../extensibility/debugger/symbol-provider.md)
- [Interfacce del provider di simboli](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)