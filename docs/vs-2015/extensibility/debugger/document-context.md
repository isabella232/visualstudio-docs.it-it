---
title: Contesto di documento | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7a9e92976af5e098dca0d1a4bb81c777eb38a9f5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528271"
---
# <a name="document-context"></a>Contesto del documento
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [contesto di documento](https://docs.microsoft.com/visualstudio/extensibility/debugger/document-context).  
  
Nelle [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debug, una **contesto di documento**:  
  
-   Rappresenta una posizione in un file di origine. Per le lingue in cui il file di origine non può essere presente, un contesto di documento identifica una posizione in un documento in genere generato dall'ambiente di runtime. Ad esempio, un motore di scripting potrebbe generare un documento da script. Per altre informazioni, vedere [posizione documento](../../extensibility/debugger/document-position.md).  
  
-   Descrive una posizione in un documento di origine che corrisponde a un contesto del codice. Il gestore di simboli esegue il mapping di un contesto del codice al contesto di documentazione, utilizzando le informazioni generate da un compilatore o interprete.  
  
-   Viene implementato da un [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 [Contesto del codice](../../extensibility/debugger/code-context.md)   
 [Provider di simboli](../../extensibility/debugger/symbol-provider.md)   
 [Interfacce del Provider di simboli](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)

