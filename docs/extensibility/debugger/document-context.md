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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 776e7d92d1763888700532f9e7ecac7bdfd52b5d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122043596"
---
# <a name="document-context"></a>Contesto del documento
Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug, un *contesto di documento:*

- Rappresenta una posizione in un file di origine. Per le lingue in cui il file di origine potrebbe non essere presente, un contesto di documento identifica una posizione in un documento in genere generata dall'ambiente di run-time. Ad esempio, un motore di scripting potrebbe generare un documento dallo script. Per altre informazioni, vedere [Posizione del documento.](../../extensibility/debugger/document-position.md)

- Descrive una posizione in un documento di origine che corrisponde a un contesto del codice. Il gestore dei simboli esegue il mapping di un contesto di codice al contesto della documentazione, usando le informazioni generate da un compilatore o un interprete.

- Viene implementato da [un'interfaccia IDebugDocumentContext2.](../../extensibility/debugger/reference/idebugdocumentcontext2.md)

## <a name="see-also"></a>Vedi anche
- [Contesto del codice](../../extensibility/debugger/code-context.md)
- [Provider di simboli](../../extensibility/debugger/symbol-provider.md)
- [Interfacce del provider di simboli](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)
