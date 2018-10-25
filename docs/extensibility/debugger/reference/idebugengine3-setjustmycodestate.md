---
title: IDebugEngine3::SetJustMyCodeState | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ffad3e6be4d81e19bd6f707bd30c744904217ba5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928971"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Le informazioni di stato JustMyCode, questo metodo indica al motore di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
);  
```  
  
```csharp  
int SetJustMyCodeState(  
   int             fUpdate,   
   uint            dwModules,   
   JMC_CODE_SPEC[] rgJMCSpec  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `fUpdate`  
 [in] Diverso da zero (`TRUE`) per aggiornare le informazioni correnti, zero (`FALSE`) per reimpostare tutte le informazioni (ignorando qualsiasi tipo impostato in precedenza).  
  
 `dwModules`  
 [in] Numero di strutture di informazioni in `rgJMCSpec.`  
  
 `rgJMCSpec`  
 [in] Matrice di [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) strutture da usare.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore.  
  
## <a name="remarks"></a>Note  
 JustMyCode è il concetto di debug solo del codice a cui appartiene un utente e ignorare tutto il codice intermedio, ad esempio il codice di sistema, anche se il codice sorgente è disponibile per tale codice di sistema.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)