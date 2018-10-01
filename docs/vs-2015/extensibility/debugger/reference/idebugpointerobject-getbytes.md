---
title: IDebugPointerObject::GetBytes | Microsoft Docs
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
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3648c180b1bbd96c02c4f00276c0b90d6806b2e9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530394"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugPointerObject::GetBytes](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugpointerobject-getbytes).  
  
Ottiene il valore indicato come una serie di byte consecutivi.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```csharp  
int GetBytes(  
   uint       dwStart,   
   uint       dwCount,   
   out byte[] pBytes,   
   out uint   pdwBytes  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwStart`  
 [in] Offset, in byte, dall'inizio dell'oggetto puntato.  
  
 `dwCount`  
 [in] Il numero di byte da recuperare.  
  
 `pBytes`  
 [in, out] Una matrice che viene compilata con il valore come una serie di byte consecutivi, iniziando in corrispondenza dell'offset specificato dall'oggetto puntato.  
  
 `pdwBytes`  
 [out] Restituisce il numero di byte effettivamente recuperati.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene utilizzato se il puntatore come rappresentato da questo [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) punta a un tipo primitivo o di una semplice matrice di tipi primitivi (vale a dire, una matrice che può essere rappresentato da una semplice sequenza di byte).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)   
 [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)

