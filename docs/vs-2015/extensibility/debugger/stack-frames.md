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
ms.openlocfilehash: d3050e89db2f5cbb138f3d358b10c7cd936c560e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423387"
---
# <a name="stack-frames"></a>Frame dello stack
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In termini di architettura del debugger, un **stack frame**:  
  
- È un'astrazione di uno stack che fornisce il contesto di esecuzione di un thread. Un thread viene sempre eseguito all'interno di una funzione. Un stack frame include le variabili locali della funzione e gli argomenti. Per eseguire il debug con Visual Studio, il linguaggio o l'ambiente di cui è in corso il debug deve supportare gli stack frame.  
  
- È in grado di identificare e descrivere se stesso e può restituire il thread associato. Un stack frame può anche restituire il contesto del codice che rappresenta il puntatore all'istruzione corrente, nonché i contesti di documentazione e di valutazione dell'espressione associati.  
  
- Dispone di proprietà che descrivono il nome, il tipo e il valore di variabili e argomenti locali e che vengono visualizzati in diverse finestre di debug dell'IDE.  
  
- È rappresentato da un'interfaccia [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , in genere creata da un motore di debug (de) o da una macchina virtuale come conseguenza dell'esecuzione di un thread.  
  
## <a name="see-also"></a>Vedere anche  
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)   
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)   
 [Motore di debug](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
