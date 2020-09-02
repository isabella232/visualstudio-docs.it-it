---
title: IDiaFrameData::execute | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4042cf58ee34b5f49df601b94e1110f03e0b6f5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197555"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esegue la rimozione dello stack e restituisce i risultati in un'interfaccia di frame di percorso stack.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `frame`  
 in Oggetto [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) che include lo stato dei registri dei frame.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. La tabella seguente illustra i possibili valori restituiti per questo metodo.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|E_DIA_INPROLOG|Non è possibile eseguire un stack frame durante il codice di prologo.|  
|E_DIA_SYNTAX|Si è verificato un errore di analisi nel programma frame.|  
|E_DIA_FRAME_ACCESS|Impossibile accedere ai registri o alla memoria.|  
|E_DIA_VALUE|Errore durante il calcolo di un valore (ad esempio, divisione per zero).|  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo viene chiamato durante il debug per rimuovere lo stack. L'oggetto [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) viene implementato dall'applicazione client per ricevere aggiornamenti ai registri e per fornire i metodi usati dal `execute` metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
