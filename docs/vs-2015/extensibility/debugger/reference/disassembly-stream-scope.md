---
title: DISASSEMBLY_STREAM_SCOPE | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 17ff0198b0472d63f070bc595b690f5cf252263a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810052"
---
# <a name="disassemblystreamscope"></a>DISASSEMBLY_STREAM_SCOPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Specifica l'ambito del flusso di disassemblaggio.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)

