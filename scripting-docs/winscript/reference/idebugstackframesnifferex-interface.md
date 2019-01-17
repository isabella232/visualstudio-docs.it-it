---
title: Interfaccia IDebugStackFrameSnifferEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSnifferEx interface
ms.assetid: fd6cf744-dee7-45f2-9a90-355b90372923
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76f10d6bbb34c61e87a1be0f61dcd7db168274e7
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348490"
---
# <a name="idebugstackframesnifferex-interface"></a>Interfaccia IDebugStackFrameSnifferEx
Consente di enumerare gli stack frame logici noti da un componente. Motori di script in genere implementano questa interfaccia. Il processo debug manager non utilizza questa interfaccia per trovare tutti gli stack frame associato a un determinato thread.  
  
> [!NOTE]
>  Questa interfaccia viene chiamata dall'interno del thread di interesse. L'implementazione dell'interfaccia deve identificare il thread corrente e restituisce un enumeratore appropriato.  
  
 Oltre ai metodi ereditati da `IDebugStackFrameSniffer`, il `IDebugStackFrameSnifferEx` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|Restituisce un enumeratore di stack frame per il thread corrente.|