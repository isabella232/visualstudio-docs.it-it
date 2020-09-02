---
title: 'IDebugStackFrame2:: EnumProperties | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::EnumProperties
helpviewer_keywords:
- IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f92db2c2fbafcd5be991281d7da4f594dcfb2c85
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164799"
---
# <a name="idebugstackframe2enumproperties"></a>IDebugStackFrame2::EnumProperties
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crea un enumeratore per le proprietà associate all'stack frame, ad esempio le variabili locali.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT EnumProperties (   
   DEBUGPROP_INFO_FLAGS      dwFieldSpec,  
   UINT                      nRadix,  
   REFIID                    refiid,  
   DWORD                     dwTimeout,  
   ULONG*                    pcelt,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumProperties (   
   enum_DEBUGPROP_INFO_FLAGS   dwFieldSpec,  
   uint                        nRadix,  
   ref Guid                    refiid,  
   uint                        dwTimeout,  
   out uint                    pcelt,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwFieldSpec`  
 in Combinazione di flag dell'enumerazione [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) che specifica i campi nelle strutture [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) enumerate da compilare.  
  
 `nRadix`  
 in La radice da usare per la formattazione di qualsiasi informazione numerica.  
  
 `refiid`  
 in GUID di un filtro usato per selezionare le strutture di [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) da enumerare, ad esempio `guidFilterLocals` .  
  
 `dwTimeout`  
 in Tempo massimo, in millisecondi, di attesa prima che venga restituito da questo metodo. Usare `INFINITE` per attendere per un periodo illimitato.  
  
 `pcelt`  
 out Restituisce il numero di proprietà enumerate. Equivale a chiamare il metodo [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md) .  
  
 `ppEnum`  
 out Restituisce un oggetto [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) contenente un elenco delle proprietà desiderate.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="remarks"></a>Osservazioni  
 Poiché questo metodo consente il recupero di tutte le proprietà selezionate con una singola chiamata, è più veloce della chiamata sequenziale dei metodi [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) e [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)   
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
