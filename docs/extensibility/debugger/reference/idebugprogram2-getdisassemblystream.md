---
title: IDebugProgram2::GetDisassemblyStream | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e8d2220d928128b02ea02d26f8273714a89171ea
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896458"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
Ottiene il flusso disassembly per questo programma o una parte di questo programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
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
 [in] Specifica un valore di [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) enumerazione che definisce l'ambito del flusso di disassemblaggio.  
  
 `pCodeContext`  
 [in] Un' [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) oggetto che rappresenta la posizione del punto da cui avviare il flusso di disassemblaggio.  
  
 `ppDisassemblyStream`  
 [out] Restituisce un [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) oggetto che rappresenta il flusso di disassemblaggio.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Restituisce `E_DISASM_NOTSUPPORTED` se disassembly non è supportato per questa architettura specifica.  
  
## <a name="remarks"></a>Note  
 Se il `dwScopes` il parametro ha la `DSS_HUGE` flag delle [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) enumerazione imposta, quindi il disassembly deve restituire un numero elevato di istruzioni disassembly, ad esempio, per un intero file o del modulo. Se il `DSS_HUGE` flag non è impostato, quindi il disassembly deve riguardare esclusivamente un'area di piccole dimensioni, che in genere una singola funzione.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)