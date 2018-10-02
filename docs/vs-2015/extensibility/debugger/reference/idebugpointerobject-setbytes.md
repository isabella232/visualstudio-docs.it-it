---
title: IDebugPointerObject::SetBytes | Microsoft Docs
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
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 48f5ffc38b83e227b35ac3967f06baa36f43b839
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532809"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugPointerObject::SetBytes](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugpointerobject-setbytes).  
  
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

