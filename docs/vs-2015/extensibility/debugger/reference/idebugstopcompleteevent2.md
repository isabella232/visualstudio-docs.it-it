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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546921"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Il motore di debug (DE) può inviare questo evento facoltativo a gestione debug sessione (SDM) quando un programma è stato arrestato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Si tratta di una nuova interfaccia per [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] . Le versioni precedenti non supportano l'arresto asincrono.  
  
 [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) viene chiamato da SDM negli scenari multiprocesso o Multiprogramma. Quando un programma invia un evento di arresto al SDM, l'SDM richiede anche l'arresto di altri programmi.  
  
 Viene usato per informare in modo asincrono che un programma è stato arrestato. Questa operazione è utile per un motore di debug dell'interprete, in cui talvolta nessun codice è in esecuzione all'interno del programma sottoposto a debug. non è quindi possibile completare l' [arresto](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) in modo sincrono. Se un motore di debug vuole usare questa notifica asincrona, deve restituire `S_ASYNC_STOP` from [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
