---
title: IDebugPortSupplier3::EnumPersistedPorts | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
helpviewer_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4bb7d89128ce5c2002d38f18bf7b93f74817191b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54985315"
---
# <a name="idebugportsupplier3enumpersistedports"></a>IDebugPortSupplier3::EnumPersistedPorts
Questo metodo recupera un oggetto che consente l'enumerazione dell'elenco di porte persistente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT EnumPersistedPorts(  
   BSTR_ARRAY         PortNames,  
   IEnumDebugPorts2** ppEnum  
);  
```  
  
```csharp  
int EnumPersistedPorts(  
   BSTR_ARRAY           PortNames,  
   out IEnumDebugPorts2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `PortNames`  
 [in] Oggetto [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) struttura che contiene un elenco di nomi di porta per trovare e restituire tra le porte persistente. Verranno restituite solo delle porte persistente con questi nomi.  
  
 `ppEnum`  
 [out] Un oggetto che implementa il [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) interfaccia.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Porte persistenti vengono caricate quando viene creata un'istanza, un fornitore di porte e salvato quando viene eliminato definitivamente il fornitore della porta.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)   
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)   
 [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)