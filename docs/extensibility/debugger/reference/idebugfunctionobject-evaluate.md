---
title: IDebugFunctionObject::Evaluate | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5d8d9c479c1dac638a63ce45d114c4a66e0a213d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908423"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
Chiama la funzione e restituisce il valore risultante come oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Evaluate(   
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```csharp  
int Evaluate(  
   IDebugObject[]   ppParams,   
   IntPtr           dwParams,   
   uint             dwTimeout,   
   out IDebugObject ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppParams`  
 [in] Matrice di [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) gli oggetti che rappresentano i parametri di input. Ognuno di questi parametri è stato creato con uno dei `Create` metodi nel [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaccia.  
  
 `dwParams`  
 [in] Il numero di parametri in di `ppParams` matrice.  
  
 `dwTimeout`  
 [in] Specifica il tempo massimo, espresso in millisecondi, di attesa prima della restituzione da questo metodo. Usare `INFINITE` per un'attesa indefinita.  
  
 `ppResult`  
 [out] Restituisce un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta il valore della funzione sotto forma di oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo configura ed esegue una chiamata alla funzione rappresentata dal [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)