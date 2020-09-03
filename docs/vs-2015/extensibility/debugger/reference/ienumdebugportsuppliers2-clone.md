---
title: 'IEnumDebugPortSuppliers2:: Clone | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2::Clone
helpviewer_keywords:
- IEnumDebugPortSuppliers2::Clone
ms.assetid: 98b9914d-4f32-44da-b422-68830bce44b4
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c8f3fffab8f8adbb3a44da0ec313887498ef0e21
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155012"
---
# <a name="ienumdebugportsuppliers2clone"></a>IEnumDebugPortSuppliers2::Clone
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Restituisce una copia dell'enumerazione corrente come oggetto separato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugPortSuppliers2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugPortSuppliers2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppEnum`  
 [out] Restituisce una copia di questa enumerazione come oggetto separato.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="remarks"></a>Osservazioni  
 La copia dell'enumerazione ha lo stesso stato dell'originale al momento della chiamata di questo metodo. Tuttavia, gli Stati della copia e dell'originale sono separati e possono essere modificati singolarmente.  
  
## <a name="see-also"></a>Vedere anche  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
