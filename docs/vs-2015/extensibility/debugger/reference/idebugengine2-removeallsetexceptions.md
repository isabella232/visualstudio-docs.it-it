---
title: IDebugEngine2::RemoveAllSetExceptions | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords:
- IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 823c3312fe68d73ddd8db3d40a35cefbed1b9ac7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967629"
---
# <a name="idebugengine2removeallsetexceptions"></a>IDebugEngine2::RemoveAllSetExceptions
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Rimuove l'elenco delle eccezioni che nell'IDE è impostata per un linguaggio o una particolare architettura della fase di esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT RemoveAllSetExceptions(   
   REFGUID guidType  
);  
```  
  
```csharp  
int RemoveAllSetExceptions(   
   ref Guid guidType  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `guidType`  
 [in] Il GUID per la lingua o il GUID per il motore di debug specifico per un'architettura di runtime.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Le eccezioni rimosse da questo metodo sono state impostate dalle chiamate precedenti per il [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) (metodo).  
  
 Per rimuovere un'eccezione specifica, chiamare il [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
