---
title: IEnumDebugPropertyInfo2::GetCount | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2::GetCount
helpviewer_keywords:
- IEnumDebugPropertyInfo2::GetCount
ms.assetid: 9b0b3ce6-08cb-46fd-a6d9-92b36e60da19
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 127255461f59628b1fa812b70a46dd1bc9b14ecb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954487"
---
# <a name="ienumdebugpropertyinfo2getcount"></a>IEnumDebugPropertyInfo2::GetCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Restituisce il numero di elementi nell'enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetCount(  
   ULONG* pcelt  
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
 Questo metodo non fa parte dell'interfaccia di enumerazione COM facoltativa che specifica che solo le `Next`, `Clone`, `Skip`, e `Reset` devono essere implementati i metodi.  
  
## <a name="see-also"></a>Vedere anche  
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
