---
title: Interfaccia IDebugExpressionContext | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpressionContext Interface
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpressionContext interface
ms.assetid: 52af82e8-0dec-49e2-a7f3-d00f66ca1401
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5920d644922b15f193ee396ea0c6bddb8a574698
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58156671"
---
# <a name="idebugexpressioncontext-interface"></a>Interfaccia IDebugExpressionContext
Rappresenta un contesto in cui le espressioni possono essere valutate. L'oggetto stack frame implementa questa interfaccia.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IDebugExpressionContext` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md)|Crea un'espressione di debug per il testo specificato.|  
|[IDebugExpressionContext::GetLanguageInfo](../../winscript/reference/idebugexpressioncontext-getlanguageinfo.md)|Restituisce un nome e GUID per la lingua che possiede questo contesto.|