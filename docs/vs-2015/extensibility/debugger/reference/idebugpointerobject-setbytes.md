---
title: IDebugPointerObject::SetBytes | Microsoft Docs
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
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f1c39921ba56dffbf89716a712e0d8a25e065bd0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775563"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Imposta il valore indicato da una serie di byte consecutivi.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT SetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```csharp  
int SetBytes(  
   uint     dwStart,   
   uint     dwCount,   
   byte[]   pBytes,   
   out uint pdwBytes  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwStart`  
 [in] Offset, in byte, dall'inizio dell'oggetto puntato.  
  
 `dwCount`  
 [in] Il numero di byte da impostare.  
  
 `pBytes`  
 [in] Matrice di byte che rappresenta il nuovo valore. Questo valore viene archiviato nell'oggetto, a partire dall'offset specificato.  
  
 `pdwBytes`  
 [out] Restituisce che il numero di byte effettivamente impostato.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene utilizzato se il puntatore come rappresentato da questo [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) punta a un tipo primitivo o di una semplice matrice di tipi primitivi (vale a dire, una matrice che può essere rappresentato da una semplice sequenza di byte). Ciò `IDebugPointerObject` oggetto non può essere un riferimento null (deve puntare a un indirizzo in memoria).  
  
## <a name="see-also"></a>Vedere anche  
 [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)   
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)

