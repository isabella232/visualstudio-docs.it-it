---
title: Interfaccia IDebugStackFrameSnifferEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: dccd9210908922951c20378868c33b3389cbed4f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432242"
---
# <a name="idebugstackframesnifferex-interface"></a>Interfaccia IDebugStackFrameSnifferEx
Consente di enumerare gli stack frame logici noti da un componente. Motori di script in genere implementano questa interfaccia. Il processo debug manager non utilizza questa interfaccia per trovare tutti gli stack frame associato a un determinato thread.  
  
> [!NOTE]
> Questa interfaccia viene chiamata dall'interno del thread di interesse. L'implementazione dell'interfaccia deve identificare il thread corrente e restituisce un enumeratore appropriato.  
  
 Oltre ai metodi ereditati da `IDebugStackFrameSniffer`, il `IDebugStackFrameSnifferEx` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|Restituisce un enumeratore di stack frame per il thread corrente.|