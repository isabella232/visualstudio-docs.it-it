---
title: IDebugFunctionObject::CreateArrayObject | Microsoft Docs
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
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8330fa51b4ab0adcb11fdc5c20729a6f2b41ca52
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752979"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crea un oggetto matrice. Questa matrice può contenere una primitiva o i valori dell'istanza dell'oggetto.  
  
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
 [in] Specifica un valore di [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) enumerazione che indica il tipo del nuovo oggetto matrice.  
  
 `pClassField`  
 [in] Un' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetto che rappresenta la classe di un oggetto, se la creazione di una matrice di oggetti i valori dell'istanza. Se si crea una matrice di oggetti primitivi, questo parametro è un valore null.  
  
 `dwRank`  
 [in] Il numero di dimensioni o il numero di dimensioni della matrice.  
  
 `dwDims`  
 [in] Le dimensioni di ogni dimensione della matrice.  
  
 `dwLowBounds`  
 [in] L'origine di ogni dimensione (in genere 0 o 1).  
  
 `ppObject`  
 [out] Restituisce un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetto che rappresenta la matrice appena creata. Si tratta in realtà un' [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Chiamare questo metodo per creare un oggetto che rappresenta un parametro di matrice per la funzione che è rappresentata dal [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)

