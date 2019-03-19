---
title: Interfaccia IDebugStackFrameSniffer | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSniffer interface
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0e753261098133eb97f5010dcef5f602d283aac4
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149484"
---
# <a name="idebugstackframesniffer-interface"></a>Interfaccia IDebugStackFrameSniffer
Consente di enumerare gli stack frame logici noti da un componente. Motori di script in genere implementano questa interfaccia. Il processo debug manager non utilizza questa interfaccia per trovare tutti gli stack frame associato a un determinato thread.  
  
> [!NOTE]
>  Il debugger chiama questa interfaccia dall'interno del thread di interesse. Il motore di scripting deve identificare il thread corrente e restituisce un enumeratore appropriato.  
  
## <a name="methods"></a>Metodi  
 Oltre ai metodi ereditati da `IUnknown`, il `IDebugStackFrameSniffer` interfaccia espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|Restituisce un enumeratore di stack frame per il thread corrente.|