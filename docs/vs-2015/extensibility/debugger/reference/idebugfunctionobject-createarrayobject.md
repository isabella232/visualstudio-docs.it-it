---
title: IDebugFunctionObject::CreateArrayObject | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: f996e7b58150f1340bf7a47790696a54f4cbc7fa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519225"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugFunctionObject::CreateArrayObject](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugfunctionobject-createarrayobject).  
  
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

