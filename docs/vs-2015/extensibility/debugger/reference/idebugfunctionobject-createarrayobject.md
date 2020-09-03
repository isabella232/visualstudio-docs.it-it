---
title: 'IDebugFunctionObject:: CreateArrayObject | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 53c1961eb1ed72580fc314d7a1542ddc926780f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205815"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crea un oggetto Array. Questa matrice può contenere valori di istanze primitive o di oggetti.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT CreateArrayObject(   
   OBJECT_TYPE    ot,  
   IDebugField*   pClassField,  
   DWORD          dwRank,  
   DWORD          dwDims[],  
   DWORD          dwLowBounds[],  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreateArrayObject(  
   enum_OBJECT_TYPE ot,   
   IDebugField      pClassField,   
   uint             dwRank,   
   uint[]           dwDims,   
   uint[]           dwLowBounds,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ot`  
 in Specifica un valore dell'enumerazione [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) che indica il tipo del nuovo oggetto matrice.  
  
 `pClassField`  
 in Oggetto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che rappresenta la classe di un oggetto, se si crea una matrice di valori di istanza dell'oggetto. Se si crea una matrice di oggetti primitivi, questo parametro è un valore null.  
  
 `dwRank`  
 in Rango o numero di dimensioni della matrice.  
  
 `dwDims`  
 in Dimensioni di ogni dimensione della matrice.  
  
 `dwLowBounds`  
 in Origine di ogni dimensione (in genere 0 o 1).  
  
 `ppObject`  
 out Restituisce un oggetto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta la matrice appena creata. Si tratta in realtà di un oggetto [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) .  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Osservazioni  
 Chiamare questo metodo per creare un oggetto che rappresenta un parametro di matrice per la funzione rappresentata dall'interfaccia [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
