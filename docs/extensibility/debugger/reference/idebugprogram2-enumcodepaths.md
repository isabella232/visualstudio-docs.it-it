---
title: IDebugProgram2::EnumCodePaths | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f9ccfd7ceeaf63ca385c9c4b1e6ac4d734ade0f7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912864"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
Recupera un elenco dei percorsi di codice per una determinata posizione nel file di origine.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT EnumCodePaths(   
   LPCOLESTR            pszHint,  
   IDebugCodeContext2*  pStart,  
   IDebugStackFrame2*   pFrame,  
   BOOL                 fSource,  
   IEnumCodePaths2**    ppEnum,  
   IDebugCodeContext2** ppSafety  
);  
```  
  
```csharp  
int EnumCodePaths(   
   string                 pszHint,  
   IDebugCodeContext2     pStart,  
   IDebugStackFrame2      pFrame,  
   Int                    fSource,  
   out IEnumCodePaths2    ppEnum,  
   out IDebugCodeContext2 ppSafety  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszHint`  
 [in] La parola sotto il cursore nella **origine** oppure **Disassembly** visualizzazione nell'IDE.  
  
 `pStart`  
 [in] Un' [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) oggetto che rappresenta il contesto codice corrente.  
  
 `pFrame`  
 [in] Un' [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) dell'oggetto che rappresenta lo stack frame associato con il punto di interruzione corrente.  
  
 `fSource`  
 [in] Diverso da zero (`TRUE`) se si trova nel **origine** vista o zero (`FALSE`) se si trova nel **Disassembly** visualizzazione.  
  
 `ppEnum`  
 [out] Restituisce un [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) oggetto contenente un elenco dei percorsi di codice.  
  
 `ppSafety`  
 [out] Restituisce un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) dell'oggetto che rappresenta un contesto di codice aggiuntivi da impostare come un punto di interruzione in caso di percorso hardcoded scelto viene ignorata. Questa situazione può verificarsi nel caso di un'espressione booleana esegue un corto circuita, ad esempio.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Un percorso di codice descrive il nome di un metodo o funzione che è stato chiamato per ottenere al momento dell'esecuzione del programma corrente. Un elenco di percorsi di codice rappresenta lo stack di chiamate.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)