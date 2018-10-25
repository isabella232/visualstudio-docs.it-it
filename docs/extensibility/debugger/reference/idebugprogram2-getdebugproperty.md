---
title: IDebugProgram2::GetDebugProperty | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7296698f3caf7fd189505c68e1c8b7d6261b1e93
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888164"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
Ottiene le proprietà del programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetDebugProperty(   
   IDebugProperty2** ppProperty  
);  
```  
  
```csharp  
int GetDebugProperty(   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppProperty`  
 [out] Restituisce un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) oggetto che rappresenta le proprietà del programma.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Le proprietà restituite da questo metodo sono specifiche del programma. Se il programma deve restituire più di una proprietà, il [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) oggetto restituito da questo metodo è un contenitore di proprietà aggiuntive e chiamando la [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) metodo restituisce un elenco di tutte le proprietà.  
  
 Un programma può esporre qualsiasi numero e tipo di proprietà aggiuntive che possono essere descritti tramite il `IDebugProperty2` interfaccia. Un IDE potrebbe visualizzare le proprietà di programma aggiuntive tramite un'interfaccia utente del browser di proprietà generica.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)