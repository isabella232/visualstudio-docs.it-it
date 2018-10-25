---
title: IDebugBinder::GetMemoryContext | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder::GetMemoryContext
helpviewer_keywords:
- IDebugBinder::GetMemoryContext method
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a94098a6645ef353ff3e18b17911c05d495fe8ae
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905441"
---
# <a name="idebugbindergetmemorycontext"></a>IDebugBinder::GetMemoryContext
Questo metodo converte una posizione di oggetto o un indirizzo di memoria in un contesto in memoria.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetMemoryContext(   
   IDebugField*           pField,  
   DWORD                  dwConstant,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int GetMemoryContext(  
   IDebugField              pField,   
   uint                     dwConstant,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pField`  
 [in] Un' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che descrive l'oggetto da individuare. Se `NULL`, quindi usare `dwConstant` invece.  
  
 `dwConstant`  
 [in] Un indirizzo di memoria costante, ad esempio 0x5000.  
  
 `ppMemCxt`  
 [out] Restituisce il [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) interfaccia che rappresenta l'indirizzo dell'oggetto o l'indirizzo in memoria.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)