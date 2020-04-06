---
title: Contesto del documento Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738914"
---
# <a name="document-context"></a>Contesto del documento
Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug, un *contesto*del documento :

- Rappresenta una posizione in un file di origine. Per le lingue in cui il file di origine potrebbe non essere presente, un contesto di documento identifica una posizione in un documento generato in genere dall'ambiente di runtime. Ad esempio, un motore di scripting potrebbe generare un documento da script. Per ulteriori informazioni, consultate [Posizione del documento.](../../extensibility/debugger/document-position.md)

- Descrive una posizione in un documento di origine che corrisponde a un contesto di codice. Il gestore di simboli esegue il mapping di un contesto di codice al contesto della documentazione, usando le informazioni generate da un compilatore o un interprete.

- Viene implementato da un [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfaccia.

## <a name="see-also"></a>Vedere anche
- [Contesto del codice](../../extensibility/debugger/code-context.md)
- [Provider di simboli](../../extensibility/debugger/symbol-provider.md)
- [Interfacce del provider di simboli](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Contesti del debuggerDebugger contexts](../../extensibility/debugger/debugger-contexts.md)
