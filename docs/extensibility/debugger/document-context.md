---
title: Contesto di documento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0ad3996877ee3ba0f16972fbd5cf10cb539ac975
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54993806"
---
# <a name="document-context"></a>Contesto di documento
Nelle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug, una *contesto di documento*:  
  
-   Rappresenta una posizione in un file di origine. Per le lingue in cui il file di origine non può essere presente, un contesto di documento identifica una posizione in un documento in genere generato dall'ambiente di runtime. Ad esempio, un motore di scripting potrebbe generare un documento da script. Per altre informazioni, vedere [posizione del documento](../../extensibility/debugger/document-position.md).  
  
-   Descrive una posizione in un documento di origine che corrisponde a un contesto del codice. Il gestore di simboli esegue il mapping di un contesto del codice al contesto di documentazione, utilizzando le informazioni generate da un compilatore o interprete.  
  
-   Viene implementato da un [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 [Contesto del codice](../../extensibility/debugger/code-context.md)   
 [Provider di simboli](../../extensibility/debugger/symbol-provider.md)   
 [Interfacce del provider di simboli](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)