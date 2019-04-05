---
title: IEnumDebugAddresses::GetCount | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::GetCount
helpviewer_keywords:
- IEnumDebugAddresses::GetCount method
ms.assetid: f2ca8ff8-539f-457c-83f8-9bbf97618065
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f90d1a24a084d054e612e3257b9009d4615deb06
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967284"
---
# <a name="ienumdebugaddressesgetcount"></a>IEnumDebugAddresses::GetCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questo metodo restituisce il numero di elementi nell'enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetCount(  
   [out] ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pcelt`  
 [out] Restituisce il numero di elementi nell'enumerazione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo non fa parte l'interfaccia di enumerazione COM facoltativa che specifica che solo successivo, il Clone, Skip e reimpostazione deve essere implementata.  
  
## <a name="see-also"></a>Vedere anche  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
