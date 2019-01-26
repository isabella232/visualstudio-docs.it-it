---
title: IDebugProperty2::SetValueAsReference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b185d284c7b5d5970737fa28aa006c636a6e6f1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54951482"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
Imposta il valore di questa proprietà sul valore del riferimento specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetValueAsReference(  
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```csharp  
int SetValueAsReference(  
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `rgpArgs`  
 [in] Matrice di argomenti da passare allo setter delle proprietà di codice gestito. Se il setter delle proprietà non accetta argomenti o se l'oggetto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) oggetto non fa riferimento a tali un setter delle proprietà, `rgpArgs` deve essere un valore null. Questo parametro è in genere un valore null.  
  
 `dwArgCount`  
 [in] Il numero di argomenti in di `rgpArgs` matrice.  
  
 `pValue`  
 [in] Un riferimento, sotto forma di un' [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) oggetto, il valore da usare per impostare questa proprietà.  
  
 `dwTimeout`  
 [in] Il tempo necessario eseguire per impostare il valore, espresso in millisecondi. Un valore tipico è `INFINITE`. Questo problema riguarda l'intervallo di tempo che può accettare qualsiasi valutazione possibili.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un errore di codice, in genere uno dei seguenti:  
  
|Error|Descrizione|  
|-----------|-----------------|  
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|Impostazione del valore da un riferimento non è supportato.|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Il valore non può essere impostato come questa proprietà fa riferimento a un metodo.|  
|`E_SETVALUE_VALUE_IS_READONLY`|Il valore è di sola lettura e non può essere impostato.|  
|`E_NOTIMPL`|Il metodo non è implementato.|  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)