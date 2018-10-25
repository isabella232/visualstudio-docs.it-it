---
title: IEnumDebugProcesses2::Clone | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugProcesses2::Clone
helpviewer_keywords:
- IEnumDebugProcesses2::Clone
ms.assetid: 3d4196d3-5a80-4f76-b8b2-f72e80c8d406
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 673f7e576f9885bcd5b4b1bd37b377a0cd497a16
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910472"
---
# <a name="ienumdebugprocesses2clone"></a>IEnumDebugProcesses2::Clone
Restituisce una copia dell'enumerazione corrente come oggetto separato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Clone(  
   IEnumDebugProcesses2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugProcesses2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppEnum`  
 [out] Restituisce una copia di questa enumerazione come oggetto separato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 La copia dell'enumerazione ha lo stesso stato originale al momento che questo metodo viene chiamato. Tuttavia, gli Stati dell'originale e la copia sono separati e possono essere modificati singolarmente.  
  
## <a name="see-also"></a>Vedere anche  
 [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)