---
title: IEnumDebugPorts2::Next | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2::Next
helpviewer_keywords:
- IEnumDebugPorts2::Next
ms.assetid: 3f43d18c-6bd1-4ddd-95ef-9550abd2ad09
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7a5fd680e7acde91fb99ea06136c627d65b3e9ad
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180402"
---
# <a name="ienumdebugports2next"></a>IEnumDebugPorts2::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Restituisce il set successivo di elementi dall'enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT Next(  
   ULONG         celt,  
   IDebugPort2** rgelt,  
   ULONG*        pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint          celt,  
   IDebugPort2[] rgelt,  
   ref uint      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `celt`  
 [in] Il numero di elementi da recuperare. Specifica inoltre la dimensione massima del `rgelt` matrice.  
  
 `rgelt`  
 [in, out] Matrice di [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) elementi da compilare.  
  
 `pceltFetched`  
 [out] Restituisce il numero di elementi effettivamente restituiti nella `rgelt`.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se inferiore al numero richiesto di elementi potrebbe essere restituiti; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
