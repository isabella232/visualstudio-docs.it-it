---
title: Stack frame | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 54a9af8134ff729fe229b3ce551a4f30f104c09b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964666"
---
# <a name="stack-frames"></a>Stack frame
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In termini di architettura del debugger, un **frame dello stack**:  
  
-   È un'astrazione di un oggetto stack che fornisce il contesto di esecuzione di un thread. Un thread viene sempre eseguito all'interno di una funzione. Uno stack frame contiene le variabili locali della funzione e gli argomenti ad esso. Per eseguire il debug con Visual Studio, la lingua o l'ambiente in fase di debug deve supportare gli stack frame.  
  
-   Possono entrambi identificare e descrivere se stesso e può restituire il thread associato. Uno stack frame può restituire anche il contesto del codice che rappresenta il puntatore all'istruzione corrente, nonché la documentazione associata e contesti di valutazione di espressione.  
  
-   Dispone di proprietà che descrivono il nome, tipo e valore di argomenti e variabili locali e che vengono visualizzati nelle varie finestre di debug dell'IDE.  
  
-   È rappresentato da un [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfaccia, in genere creato da un motore di debug (DE) o una macchina virtuale come conseguenza l'esecuzione di un thread.  
  
## <a name="see-also"></a>Vedere anche  
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)   
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)   
 [Motore di debug](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
