---
title: Interfaccia IEnumDebugStackFrames | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumDebugStackFrames interface
ms.assetid: 13484429-0140-4f4f-8502-3ca2a0553ed4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 224c26bccc5443cb20e2ca514ac6df1a111df05e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963364"
---
# <a name="ienumdebugstackframes-interface"></a>Interfaccia IEnumDebugStackFrames
Enumera gli stack frame corrispondenti a un thread.  
  
## <a name="methods"></a>Metodi  
 Oltre ai metodi ereditati da `IUnknown`, il `IEnumDebugStackFrames` interfaccia espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IEnumDebugStackFrames::Next](../../winscript/reference/ienumdebugstackframes-next.md)|Recupera un determinato numero di segmenti nella sequenza di enumerazione.|  
|[IEnumDebugStackFrames::Skip](../../winscript/reference/ienumdebugstackframes-skip.md)|Ignora un determinato numero di segmenti in una sequenza di enumerazione.|  
|[IEnumDebugStackFrames::Reset](../../winscript/reference/ienumdebugstackframes-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[IEnumDebugStackFrames::Clone](../../winscript/reference/ienumdebugstackframes-clone.md)|Crea un enumeratore che contiene lo stesso stato dell'enumeratore corrente.|