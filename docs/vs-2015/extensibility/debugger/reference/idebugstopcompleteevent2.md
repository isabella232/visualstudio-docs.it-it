---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9c2a6a6e69bf47751706710801dd78c832ccd2c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546921"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Il motore di debug (DE) può inviare questo evento facoltativo da gestore di sessione di debug (SDM) quando un programma è stato arrestato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Si tratta di una nuova interfaccia per [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]. Arresto asincrono non supporta le versioni precedenti.  
  
 [Arrestare](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) viene chiamato da SDM negli scenari a più processi o multi-programma. Quando un programma invia un evento di arresto per il modello SDM, il modello SDM richiede altri programmi per arrestare, troppo.  
  
 Viene utilizzato per comunicare in modo asincrono il modello SDM che un programma è stato arrestato. Ciò è utile per un motore di debug dell'interprete, in cui in alcuni casi non è in esecuzione codice all'interno del programma, in modo [arrestare](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) non può essere eseguita in modo sincrono. Se un motore di debug vuole adottare questa notifica asincrona, deve restituire `S_ASYNC_STOP` dal [arrestare](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
