---
title: 'IDebugProgram2:: EnumCodePaths | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e4d34b1b6519407e02d4340a5108ef03cece12b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202775"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera un elenco di percorsi di codice per una posizione specificata in un file di origine.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
 in Parola sotto il cursore nella visualizzazione di **origine** o **Disassembly** nell'IDE.  
  
 `pStart`  
 in Oggetto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) che rappresenta il contesto del codice corrente.  
  
 `pFrame`  
 in Oggetto [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) che rappresenta il stack frame associato al punto di interruzione corrente.  
  
 `fSource`  
 in Valore diverso da zero ( `TRUE` ) se nella visualizzazione **origine** o zero ( `FALSE` ) se è presente nella visualizzazione **Disassembly** .  
  
 `ppEnum`  
 out Restituisce un oggetto [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) contenente un elenco di percorsi di codice.  
  
 `ppSafety`  
 out Restituisce un oggetto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) che rappresenta un contesto di codice aggiuntivo da impostare come punto di interruzione nel caso in cui il percorso del codice scelto venga ignorato. Questo problema può verificarsi nel caso di un'espressione booleana di corto circuito, ad esempio.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="remarks"></a>Osservazioni  
 Un percorso di codice descrive il nome di un metodo o di una funzione chiamata per ottenere il punto corrente nell'esecuzione del programma. Un elenco di percorsi di codice rappresenta lo stack di chiamate.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
