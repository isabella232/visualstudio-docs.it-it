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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fef3debcbce3a178c4321114d69c87c627611a07
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915323"
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
