---
title: Posizione documento | Microsoft Docs
description: Informazioni sul modo in cui la posizione di un documento nel debug di Visual Studio fornisce un'astrazione di una posizione in un file di origine come noto all'IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: b59d739c-7572-427f-a70d-4e5df63d02c1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 42f85d0d15c46cfdfc2b76130649976d15035d7a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840717"
---
# <a name="document-position"></a>Posizione del documento
In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug, *posizione del documento*:

- Fornisce un'astrazione di una posizione in un file di origine come noto all'IDE. Per la maggior parte delle lingue oggi, una posizione del documento può essere considerata come una posizione in un file di origine.

- Descrive una posizione in un documento di origine in un motore di debug.

- Viene implementato da un'interfaccia [IDebugDocumentPosition2](../../extensibility/debugger/reference/idebugdocumentposition2.md) .

## <a name="see-also"></a>Vedi anche
- [Contesto del codice](../../extensibility/debugger/code-context.md)
- [Contesto del documento](../../extensibility/debugger/document-context.md)
- [Provider di simboli](../../extensibility/debugger/symbol-provider.md)
- [Interfacce del provider di simboli](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)
