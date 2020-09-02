---
title: Moduli | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7a2b2f04e1088b9b06cb05015a6b0b4da5d60927
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153740"
---
# <a name="modules"></a>Moduli
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In termini di architettura del debugger, un **modulo**:  
  
- È un contenitore fisico di codice, ad esempio un file eseguibile o una DLL.  
  
- Può ricaricare i simboli e descrivere se stesso. Le descrizioni dei moduli vengono visualizzate nella finestra moduli dell'IDE.  
  
- È rappresentato da un'interfaccia [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) creata da un motore di debug per descrivere il modulo.  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
