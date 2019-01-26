---
title: DISASSEMBLY_STREAM_SCOPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3fddab6fc65848a5fa2577785d9f3db934f50086
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55012937"
---
# <a name="disassemblystreamscope"></a>DISASSEMBLY_STREAM_SCOPE
Specifica l'ambito del flusso di disassemblaggio.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
typedef DWORD DISASSEMBLY_STREAM_SCOPE;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
```  
  
## <a name="members"></a>Membri  
 DSS_HUGE  
 Specifica che il contesto del codice di disassemblaggio sarebbe generare più output di un client in genere è necessario recuperare in una singola chiamata.  
  
 DSS_FUNCTION  
 Specifica che la funzione contenuta dal contesto del codice deve essere disassemblata. Specifica che il flusso disassembly rappresenta una funzione, quando restituiti per il [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) (metodo).  
  
 DSS_MODULE  
 Quando restituisce il `IDebugDisassemblyStream2::GetScope` metodo, specifica che il flusso disassembly rappresenta un modulo.  
  
 DSS_ALL  
 Specifica il disassembly per l'intero spazio indirizzi.  
  
## <a name="remarks"></a>Note  
 Passato come argomento per il [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) metodo e restituito dalle [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) (metodo).  
  
 Questi valori possono essere combinati con un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)