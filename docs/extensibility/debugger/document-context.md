---
title: Contesto del documento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 48fe651e69e5e2c97756788cc30e54454c26e51e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738914"
---
# <a name="document-context"></a>Contesto del documento
In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug, *contesto del documento*:

- Rappresenta una posizione in un file di origine. Per le lingue in cui il file di origine potrebbe non essere presente, un contesto del documento identifica una posizione in un documento generata in genere dall'ambiente di Runtime. È ad esempio possibile che un motore di script generi un documento dallo script. Per ulteriori informazioni, vedere la [posizione del documento](../../extensibility/debugger/document-position.md).

- Descrive una posizione in un documento di origine che corrisponde a un contesto di codice. Il gestore di simboli esegue il mapping di un contesto di codice al contesto della documentazione, usando le informazioni generate da un compilatore o un interprete.

- Viene implementato da un'interfaccia [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) .

## <a name="see-also"></a>Vedere anche
- [Contesto del codice](../../extensibility/debugger/code-context.md)
- [Provider di simboli](../../extensibility/debugger/symbol-provider.md)
- [Interfacce del provider di simboli](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)
