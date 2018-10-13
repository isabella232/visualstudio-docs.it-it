---
title: IDebugFunctionObject::CreateObject | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 93a35747251d0d821b8c763036cb4e1ab110e5a2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49177372"
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crea un oggetto usando un costruttore.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT CreateObject(   
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   IDebugObject**        ppObject  
);  
```  
  
```csharp  
int CreateObject(  
   IDebugFunctionObject pConstructor,   
   uint                 dwArgs,   
   IDebugObject[]       pArgs,   
   out IDebugObject     ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pConstructor`  
 [in] Un' [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) oggetto che rappresenta il costruttore dell'oggetto da creare.  
  
 `dwArgs`  
 [in] Il numero di parametri in di `pArg` matrice. Rappresenta il numero di parametri passati al costruttore.  
  
 `pArg`  
 [in] Matrice di [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) gli oggetti che rappresentano i parametri passati al costruttore.  
  
 `ppObject`  
 [out] Restituisce un `IDebugObject` che rappresenta l'oggetto appena creato.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Chiamare questo metodo per creare un oggetto che rappresenta un'istanza di una classe (o altro tipo complesso che richiede un costruttore) che rappresenta un parametro alla funzione che è rappresentato dal [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaccia.  
  
 Se il parametro dell'oggetto non richiede un costruttore, chiamare il [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)

