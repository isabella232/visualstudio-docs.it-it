---
title: 'IDebugProperty2:: GetPropertyInfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetPropertyInfo
helpviewer_keywords:
- IDebugProperty2::GetPropertyInfo
ms.assetid: 39d6e942-df72-4c84-a5d9-a386d112714c
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6a6d4c2fd943ddef0b4459460be1f67550e53d84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146267"
---
# <a name="idebugproperty2getpropertyinfo"></a>IDebugProperty2::GetPropertyInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene la struttura di [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) che descrive una proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetPropertyInfo (   
   DEBUGPROP_INFO_FLAGS dwFields,  
   DWORD                nRadix,  
   DWORD                dwTimeout,  
   IDebugReference2**   rgpArgs,  
   DWORD                dwArgCount,  
   DEBUG_PROPERTY_INFO* pPropertyInfo  
);  
```  
  
```cpp#  
int GetPropertyInfo (   
   enum_DEBUGPROP_INFO_FLAGS dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_PROPERTY_INFO[]     pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwFields`  
 in Combinazione di valori dell'enumerazione [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) che specifica i campi che devono essere compilati nella `pPropertyInfo` struttura.  
  
 `nRadix`  
 in Radice da usare per la formattazione di qualsiasi informazione numerica.  
  
 `dwTimeout`  
 in Specifica il tempo massimo di attesa, in millisecondi, prima che venga restituito da questo metodo. Usare `INFINITE` per attendere per un periodo illimitato.  
  
 `rgpArgs`  
 [in, out] Riservato per un utilizzo futuro; impostare su un valore null.  
  
 `dwArgCount`  
 in Riservato per un utilizzo futuro; impostare su zero.  
  
 `pPropertyInfo`  
 out Struttura [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) compilata con la descrizione della proprietà.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
