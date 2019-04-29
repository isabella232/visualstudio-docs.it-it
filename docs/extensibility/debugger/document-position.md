---
title: Posizione del documento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: b59d739c-7572-427f-a70d-4e5df63d02c1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fc9d1e793405b2eb83fe4f72980a71e44d1acbd1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62926096"
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