---
title: I moduli | Microsoft Docs
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153740"
---
# <a name="modules"></a>Moduli
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In termini di architettura del debugger, un **modulo**:  
  
- È un contenitore fisico di codice, ad esempio un file eseguibile o una DLL.  
  
- Può ricaricare i simboli e descrivere se stesso. Descrizioni dei moduli vengono visualizzati nella finestra moduli dell'IDE.  
  
- È rappresentato da un [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) interfaccia, creato da un motore di debug per descrivere il modulo.  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
