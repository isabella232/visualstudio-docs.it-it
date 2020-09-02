---
title: 'IEnumDebugThreads2:: Clone | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::Clone
helpviewer_keywords:
- IEnumDebugThreads2::Clone
ms.assetid: d774322c-e72d-4df3-b317-928da39dadc5
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cf9732942234f896216031d74acd5143832049bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147732"
---
# <a name="ienumdebugthreads2clone"></a>IEnumDebugThreads2::Clone
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Restituisce una copia dell'enumerazione corrente come oggetto separato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugThreads2 ppEnum  
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
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
