---
title: Interfaccia metodo ijsdebugdatatarget | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a9b784d6-958f-4d55-b3f6-c2d6b260a16b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85c77209230abfe261c9ec0b884ad0a677cfbf07
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572458"
---
# <a name="ijsdebugdatatarget-interface"></a>Interfaccia IJsDebugDataTarget
Implementato dal debugger per fornire funzionalità per l'accesso e la modifica dello stato del processo del debugger di destinazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
IJsDebugDataTarget : public IUnknown;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Name|Descrizione|  
|----------|-----------------|  
|[Metodo IJsDebugDataTarget::AllocateVirtualMemory](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|Riserva e/o conferma un'area di memoria nello spazio degli indirizzi virtuale del processo di destinazione.|  
|[Metodo IJsDebugDataTarget::CreateStackFrameEnumerator](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|Crea un enumeratore per gli stack frame.|  
|[Metodo IJsDebugDataTarget::FreeVirtualMemory](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|Rilascia e/o Elimina un commit di un'area di memoria nello spazio degli indirizzi virtuali del processo di destinazione.|  
|[Metodo IJsDebugDataTarget::GetThreadContext](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|Recupera il contesto per il thread specificato.|  
|[Metodo IJsDebugDataTarget::GetTlsValue](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|Per il thread di cui è in corso il debug, recupera il valore nello slot TLS (thread local storage) per l'indice TLS specificato.|  
|[Metodo IJsDebugDataTarget::ReadBSTR](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|Legge un BSTR dalla destinazione di debug.|  
|[Metodo IJsDebugDataTarget::ReadMemory](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|Esegue la lettura della memoria del processo di destinazione.|  
|[Metodo IJsDebugDataTarget::ReadNullTerminatedString](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|Legge il numero specificato di caratteri dalla destinazione.|  
|[Metodo IJsDebugDataTarget::WriteMemory](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|Esegue la lettura della memoria del processo di destinazione.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag. h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti sulle interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)