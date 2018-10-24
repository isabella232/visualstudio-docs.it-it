---
title: IDebugDisassemblyStream2::GetScope | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2::GetScope
helpviewer_keywords:
- IDebugDisassemblyStream2::GetScope
ms.assetid: 71c6e632-642a-42d8-a995-77e4ac190a5b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 739c2515d402d4132b2fd5eb10c7ba2cbd5e04b2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49814844"
---
# <a name="idebugdisassemblystream2getscope"></a>IDebugDisassemblyStream2::GetScope
Ottiene l'ambito del flusso di disassemblaggio.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetScope(   
   DISASSEMBLY_STREAM_SCOPE* pdwScope  
);  
```  
  
```csharp  
int GetScope(   
   out enum_ DISASSEMBLY_STREAM_SCOPE pdwScope  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdwScope`  
 [out] Restituisce un valore di [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) enumerazione che descrive l'ambito di questo flusso disassembly.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 L'ambito del disassembly potrebbe essere una funzione o l'intero modulo, ad esempio.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)