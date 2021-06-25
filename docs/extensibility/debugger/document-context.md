---
title: Contesto del documento | Microsoft Docs
description: Informazioni sul contesto del documento Visual Studio debug, che rappresenta una posizione in un file di origine o una posizione in un documento di origine per un contesto di codice.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a4b7554e274977f23474f6cf3e8e1af30d9e73b3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898188"
---
# <a name="document-context"></a>Contesto del documento
Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug, un contesto *di documento*:

- Rappresenta una posizione in un file di origine. Per i linguaggi in cui il file di origine potrebbe non essere presente, un contesto del documento identifica una posizione in un documento in genere generato dall'ambiente di esecuzione. Ad esempio, un motore di scripting potrebbe generare un documento dallo script. Per altre informazioni, vedere [Posizione del documento.](../../extensibility/debugger/document-position.md)

- Descrive una posizione in un documento di origine che corrisponde a un contesto di codice. Il gestore di simboli esegue il mapping di un contesto di codice al contesto della documentazione, usando le informazioni generate da un compilatore o un interprete.

- Viene implementato da [un'interfaccia IDebugDocumentContext2.](../../extensibility/debugger/reference/idebugdocumentcontext2.md)

## <a name="see-also"></a>Vedere anche
- [Contesto del codice](../../extensibility/debugger/code-context.md)
- [Provider di simboli](../../extensibility/debugger/symbol-provider.md)
- [Interfacce del provider di simboli](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)
