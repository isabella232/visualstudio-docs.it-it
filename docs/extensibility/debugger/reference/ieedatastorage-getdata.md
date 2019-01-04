---
title: IEEDataStorage::GetData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8ed1788804fea7d10734de339d7b5a91d9cd168b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53936971"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
Recupera il numero di byte specificato dall'oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetData(  
   ULONG  dataSize,  
   ULONG* sizeGotten,  
   BYTE*  data  
);  
```  
  
```csharp  
int GetData(  
   uint     dataSize,  
   out uint sizeGotten,  
   byte[]   data  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dataSize`  
 [in] Il numero di byte da recuperare (il `data` matrice deve contenere almeno questo numero di byte).  
  
 `sizeGotten`  
 [out] Restituisce il numero di byte effettivamente recuperati.  
  
 `data`  
 [in, out] Matrice da riempire con i dati richiesti.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 L'uso consigliato di questo metodo consiste nel recuperare tutti i byte di dati in una matrice locale, poiché non esiste alcuna possibilità di ignorare i byte nel processo di recupero. In questo caso, il parametro `dataSize` deve essere il valore restituito per il [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)