---
title: IDebugProperty2::EnumChildren | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6f297b4adf3c7194340bfdda71936de93c4506a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54988246"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
Recupera un elenco degli elementi figlio della proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT EnumChildren (   
   DEBUGPROP_INFO_FLAGS      dwFields,  
   DWORD                     dwRadix,  
   REFGUID                   guidFilter,  
   DBG_ATTRIB_FLAGS          dwAttribFilter,  
   LPCOLESTR                 pszNameFilter,  
   DWORD                     dwTimeout,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumChildren (   
   enum_DEBUGPROP_INFO_FLAGS   dwFields,  
   uint                        dwRadix,  
   ref Guid                    guidFilter,  
   uint                        dwAttribFilter,  
   string                      pszNameFilter,  
   uint                        dwTimeout,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwFields`  
 [in] Una combinazione di flag dal [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) enumerazione che specifica quali campi in enumerati [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) strutture sono da compilare.  
  
 `dwRadix`  
 [in] Specifica la radice da utilizzare nella formattazione qualsiasi informazioni numeriche.  
  
 `guidFilter`  
 [in] GUID del filtro utilizzato con il `dwAttribFilter` e `pszNameFilter` parametri per selezionare quali `DEBUG_PROPERTY_INFO` elementi figlio devono essere enumerati. Ad esempio, `guidFilterLocals` filtri per le variabili locali.  
  
 `dwAttribFilter`  
 [in] Una combinazione di flag dal [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) enumerazione che specifica il tipo di oggetti da enumerare, ad esempio `DBG_ATTRIB_METHOD` per tutti i metodi che possono essere figli di questa proprietà. Usato in combinazione con il `guidFilter` e `pszNameFilter` parametri.  
  
 `pszNameFilter`  
 [in] Il nome del filtro utilizzato con il `guidFilter` e `dwAttribFilter` parametri per selezionare quali `DEBUG_PROPERTY_INFO` elementi figlio devono essere enumerati. Ad esempio si imposta questo parametro per i filtri "MyX" per tutti gli elementi figlio con il nome "MyX."  
  
 `dwTimeout`  
 [in] Specifica il tempo massimo, espresso in millisecondi, di attesa prima della restituzione da questo metodo. Usare `INFINITE` per un'attesa indefinita.  
  
 `ppEnum`  
 [out] Restituisce un [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) oggetto contenente un elenco delle proprietà figlio.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)