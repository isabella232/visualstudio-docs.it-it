---
title: 'IDebugProgram2:: GetDisassemblyStream | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f918b9895975554534ef1702334d7a006112f77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202736"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene il flusso di disassembly per il programma o una parte di questo programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetDisassemblyStream(   
   DISASSEMBLY_STREAM_SCOPE   dwScope,  
   IDebugCodeContext2*        pCodeContext,  
   IDebugDisassemblyStream2** ppDisassemblyStream  
);  
```  
  
```csharp  
int GetDisassemblyStream(   
   enum_DISASSEMBLY_STREAM_SCOPE  dwScope,  
   IDebugCodeContext2             pCodeContext,  
   out IDebugDisassemblyStream2   ppDisassemblyStream  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwScope`  
 in Specifica un valore dell'enumerazione [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) che definisce l'ambito del flusso di Disassembly.  
  
 `pCodeContext`  
 in Oggetto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) che rappresenta la posizione in cui avviare il flusso di Disassembly.  
  
 `ppDisassemblyStream`  
 out Restituisce un oggetto [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) che rappresenta il flusso Disassembly.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Restituisce `E_DISASM_NOTSUPPORTED` se il Disassembly non è supportato per questa architettura particolare.  
  
## <a name="remarks"></a>Osservazioni  
 Se il `dwScopes` parametro ha il `DSS_HUGE` flag del set di enumerazione [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) , il disassembly deve restituire un numero elevato di istruzioni di Disassembly, ad esempio per un intero file o modulo. Se il `DSS_HUGE` flag non è impostato, il disassembly dovrebbe essere limitato a una piccola area, in genere quella di una singola funzione.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
