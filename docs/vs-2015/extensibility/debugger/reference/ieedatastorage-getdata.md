---
title: IEEDataStorage::GetData | Microsoft Docs
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
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: be6b411ae5881dbcfcfc51de98d5b67cd57e8048
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188122"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera il numero di byte specificato dall'oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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

