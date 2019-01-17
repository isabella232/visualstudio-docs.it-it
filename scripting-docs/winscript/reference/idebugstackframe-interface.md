---
title: Interfaccia IDebugStackFrame | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrame interface
ms.assetid: e95c1b4f-17c1-490c-a56b-c25fa45d4822
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0834abbedf88b911dd952c1f3928c5da3414abec
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348542"
---
# <a name="idebugstackframe-interface"></a>Interfaccia IDebugStackFrame
Rappresenta uno stack frame logico nello stack di thread. Chiamare il `IDebugStackFrame::QueryInterface` metodo per ottenere il `IDebugExpressionContext` interfaccia, che consente espressioni e valutazione delle espressioni di windows.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IDebugStackFrame` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugStackFrame::GetCodeContext](../../winscript/reference/idebugstackframe-getcodecontext.md)|Restituisce il contesto codice corrente associato al frame dello stack.|  
|[IDebugStackFrame::GetDescriptionString](../../winscript/reference/idebugstackframe-getdescriptionstring.md)|Restituisce una descrizione breve o lungo testuale del frame dello stack.|  
|[IDebugStackFrame::GetLanguageString](../../winscript/reference/idebugstackframe-getlanguagestring.md)|Restituisce una descrizione breve o lungo testuale della lingua.|  
|[IDebugStackFrame::GetThread](../../winscript/reference/idebugstackframe-getthread.md)|Restituisce il thread associato a questo frame dello stack.|  
|[IDebugStackFrame::GetDebugProperty](../../winscript/reference/idebugstackframe-getdebugproperty.md)|Restituisce un visualizzatore proprietà per il frame corrente.|