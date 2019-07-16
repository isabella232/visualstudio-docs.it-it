---
title: IDebugArrayObject::GetDimensions | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 09902c60f87cfb92d0f0778fcbd106ade4d8dac4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197780"
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene le dimensioni della matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetDimensions(   
   DWORD dwCount,  
   DWORD dwDimensions[]  
);  
```  
  
```csharp  
int GetDimensions(  
   [In] uint    dwCount,   
   [Out] uint[] dwDimensions  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwCount`  
 [in] Il numero di dimensioni da recuperare.  
  
 `dwDimensions`  
 [in, out] Matrice che viene compilata con le dimensioni di ogni dimensione. `dwCount` Specifica la dimensione massima del `dwDimensions` matrice.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Una matrice multidimensionale può avere dimensioni diverse per ogni dimensione. Si consideri ad esempio la matrice tridimensionale `myarray[3][2][6]`, questo metodo restituisce 3, 2 e 6 nel `dwDimensions` parametro nell'ordine indicato.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
